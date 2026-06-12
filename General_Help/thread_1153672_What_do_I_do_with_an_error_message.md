---
title: "What do I do with an error message"
date: 2009-05-09
forum: General Help
---

### Post by gittr_done on 2009-05-09
Using Jaunty 9.04 UBUNTU with UNR features applied.  I am trying to download the Amazon MP3 downloader.  I have Firefox set to ask me where to save files being downloaded.  When I try to download and save the AmazonMP3.deb file, I get the following error msg:   There is not enough room on the disk to save /tmp/kG_bpbMZ.part.    I am brand new at Linux, so this message is beyond Greek to me.  Also, I cannot seem to find anything via Google to help decipher and correct.   Thanks in Advance

---

### Post by Egi_Power on 2009-05-09
Hi!

I think the answer is in the message. :)
> **There is not enough room on the disk to save /tmp/kG_bpbMZ.part.**

Your system can't save the file, because there is not enough space on your hard disk.

When you installed Ubuntu, did you make a separate /tmp partition?

Can you try to save the file on your Desktop instead?

Egi__Power

---

### Post by _Purple_ on 2009-05-09
Open terminal (Application > Accessories > Terminal) and type the following commands
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

Then try to download the file again. Post back if you still get the error message.

---

### Post by sahabcse on 2009-05-09
Paste the o/p of
cd /tmp
sudo du -csh ./*

---

