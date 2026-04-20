# PES-VCS Lab Report

**Name:** Thejaswi Kishore  
**SRN:** PES1UG23CS655  
**Platform:** Ubuntu 24.04

---

## Build Instructions

```bash
sudo apt update && sudo apt install -y gcc build-essential libssl-dev
export PES_AUTHOR="Thejaswi Kishore <PES1UG23CS655>"
make all
Phase 1 — Object Storage Foundation

Files modified: object.c

object_write prepends a "<type> <size>\0" header to the data, hashes the
whole thing with SHA-256, skips writing if the object already exists
(deduplication), creates the shard directory, writes to a temp file, fsyncs,
and renames atomically. This guarantees the object store is never left with a
partial file even on a crash.

object_read reverifies the SHA-256 after reading (integrity check), parses
the type and declared size from the header, validates the declared size against
the actual byte count, then returns the data portion in a caller-owned buffer.

Screenshot 1A — ./test_objects
<img width="1512" height="563" alt="WhatsApp Image 2026-04-20 at 5 17 10 PM" src="https://github.com/user-attachments/assets/f1dd7bef-e64b-4252-8204-8ecdd96e3ed7" />
