---
title: "Testing Network Throughput"
date: 2005-10-26
forum: Desktop Environments
---

### Post by faulkner132 on 2005-10-26
What is the best way to do this?

The information I want to get is the speed data is written to and retrieved from a network drive.

For example a report along the lines of:

Computer1 -> Server
Write Speed: 10 MB/s  (speed Computer1 writes data to Server's local drive)
Read Speed: 8.2 MB/s  (speed Computer1 retrieves data from Server's local drive)

Thanks for any help.

---

### Post by mlomker on 2005-10-26
I usually just use FTP to move a large file and see what it tells me for throughput.  I'm sure that there are more sophisticated approaches...

---

### Post by faulkner132 on 2005-10-26
[QUOTE=mlomker]I usually just use FTP to move a large file and see what it tells me for throughput.  I'm sure that there are more sophisticated approaches...[/QUOTE]
Good idea, but my situation is a bit unique.  I want to build a computer booting off a USB flash drive and running it memory.  It will, essentially, act a front-end to a server which will be a music/video host for recording TV.

I need to know if a gigabit network will support writing to a network drive fast enough.  In theory it should transfer data at 125 MB/s, but bottlenecks exist and I need to see actual speeds...

Is this is a post for the server forum?

---

