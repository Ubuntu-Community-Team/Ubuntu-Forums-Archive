---
title: "ffmpeg cron job"
date: 2010-06-18
forum: Desktop Environments
---

### Post by HvRooyen on 2010-06-18
Hi all:

Trying to use ffmpeg to create mpeg from directory of jpegs (IPCam motion triggered uploads to ftp account in directory a).
Running the following command as user ipcams gives me what I need:
ffmpeg -f image2 -i a/%5d.jpg a.mpg
Nex step: Placing the above command into executable mkmpeg in /home/ipcams and running it also works, but **trying to run it as a cron job (as user ipcams) gives the following**:

I/O error occurred
Usually that means that input file is truncated and/or corrupted.

I assume I am doing something very stupid, but do not know enough to figure out what it is.

Advice please?

TIA
H.

---

### Post by HvRooyen on 2010-06-18
Reply to own question: Problem solved by specifying full paths to ffmpeg as well as folders.

---

