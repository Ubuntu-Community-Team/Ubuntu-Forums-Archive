---
title: "Finding Windows network shares from Lubuntu"
date: 2013-09-22
forum: Desktop Environments
---

### Post by kenaniah on 2013-09-22
Hello forum!

Running Lubuntu 13.04, trying to access Windows shares on my home network.

I found an old thread (now closed) that walked me through installing Gigolo.

This program seems to work when installed, except it doesn't see my home network.

So I hit connect, select "Windows Share", enter the server path and share name.

The program does some thinking, and then nothing appears.

How do I make this program work?  Or is there an easier way to find and access my Windows network? 

Also discovered - I can open the file manager, go-network drives, and see my workgroup listed.......but when I try to open it, I'm told it's not mounted. What could I do with that?

Sheesh......can't open my slave drive on this machine, either........I'm doing something wrong, somewhere.....

Please and thank you!:)

---

### Post by gigoachef on 2013-11-28
> I can open the file manager, go-network drives, and see my workgroup listed.......but when I try to open it, I'm told it's not mounted.

This is a problem caused by a known bug in PcManFm

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1174571]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1174571")

---

