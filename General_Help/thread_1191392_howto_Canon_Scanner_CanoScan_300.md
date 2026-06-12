---
title: "howto: Canon Scanner CanoScan 300"
date: 2009-06-18
forum: General Help
---

### Post by jodelsepp on 2009-06-18
I though I'd post how I made the scanner CanoScan 300 work on my system. It's an old scanner, SCSI. Had been supported by Sane for a long time. I'm posting in the hope future users will find it. I had found [http://ubuntuforums.org/showthread.php?t=320018](http://ubuntuforums.org/showthread.php?t=320018) from three years ago without a solution. Couldn't post there, because it's read only.

On a terminal, I used:
$ sane-find-scanner 
...
found SCSI scanner "CANON IX-03035B 2.01" at /dev/sg3
...

This found my scanner and gave me the current device ID. In my case: /dev/sg3
I know the Sane device string that works is: canon:/dev/sg3

Flegita didn't find the scanner automatically, and I don't how I'd manually tell Flegita what device to use. So I installed xsane, using synaptics, or:
$ apt-get install xsane

Now here is the command you need to run on the terminal. When you do this, replace /dev/sg3 with the ID that was reported above by sane-fine-scanner:

$ xsane canon:/dev/sg3

I got some errors about "permission denied", but don't know what they refer to. I could scan fine. Preview works, scanning works, etc.

---

