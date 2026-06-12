---
title: "Poweredge 2300 Problems"
date: 2007-09-07
forum: Dell  Ubuntu Support
---

### Post by phantasm on 2007-09-07
I psoted this in the Hardware forum but so far have got nothing. I really need some input. Thanks.

I just installed Ubuntu 7.04 Server on an older server i have in my house. When the system boots i see the following messages regarding sda and sdb. I do not know exactly what it's trying to tell me though. lol.

[IMG]http://i160.photobucket.com/albums/t179/phantsam/Ubuntu.jpg[/IMG]

The system is a Dell Poweredge 2300 with the following specs:

[LIST]
[*]2x PIII 650mhz
[*]768MB RAM (PC100 ECC)
[*]2x 18GB SCSI HD's (RAID 1 - Ubuntu Server install)
[*]4x 36GB SCSI HD's (RAID 5)
[*]PERC 3 DC RAID Controller
[/LIST]

The PERC card is configured for Mass Storage mode, CentOS had issues recognizing it in IO2 mode so i changed it. I no longer use CentOS though... coule this be an issue? Any insight is appreciated.

---

### Post by Afishionado on 2007-09-07
First off, is it able to finish booting normally, and then mount and access the drives in question?

If so, this is the sort of thing I tend to ignore and move on. ;) Someone else will probably tell me that this is an urgent signal of impending doom and that I'm an idiot ;) so we'll see who else replies.

---

### Post by neptho on 2007-09-07
It's just saying that the disk's controller doesn't state wether or not write-through caching is available.  Ignore it.

---

### Post by phantasm on 2007-09-08
Ok. i know i specified Write Through when i set up the array though...

---

