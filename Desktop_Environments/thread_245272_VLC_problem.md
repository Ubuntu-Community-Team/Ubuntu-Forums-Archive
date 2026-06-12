---
title: "VLC problem"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Darth Muzzy on 2006-08-27
When I try to open an AVI file with VLC, it crashes and I get this error message:

VLC media player 0.8.4 Janus
[00000320] oss audio output error: cannot open audio device (/dev/dsp)
Creating link /home/alexander/.kde/socket-hellborn.
can't create mcop directory

I've tried sudo apt-get update and sudo apt-get upgrade.  Any suggestions?

---

### Post by dcotruta on 2006-08-27
This is a problem with the aRts package (it controls sound).

reported here -> [https://launchpad.net/distros/ubuntu/+source/arts/+bug/55973](https://launchpad.net/distros/ubuntu/+source/arts/+bug/55973)

I thought this was just affecting Fedora, but I guess it's in Ubuntu too. You could try the ReHat patch...

---

### Post by Darth Muzzy on 2006-09-03
The link provided has proved unhelpful.  I still have no idea as to how to go about fixing the problem.

---

