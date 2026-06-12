---
title: "Steam problem... Yet again."
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by lakku on 2007-10-20
Ok, so, hello guys.

I have a problem and I think only you guys could help me. It's about Steam (surprise, I think this hasn't been asked many times) but, ok. 

So I can't get Steam running anymore on my Ubuntu. After the 7.10 update it says "Another copy of Steam is already running" In 7.04 I used to open Steam with the root command but now in 7.10 I just right-clicked Steam.exe and chose Open with wine but it gives me that error. And when trying to open with root command it gives me "ERROR: unable to open steamTmp.exe for writing"

So I started googling about this problem and find my way on these forums. So yeah, the nice -19 command is not working for me because of no steamTmp.exe. I have Steam also installed on my NTFS drive but I can't even find steamTmp.exe from there. 

So I'm asking help from you guys, thanks.

---

### Post by ubu-for on 2007-10-20
Copy the complete Steam (CSS) folder to your Ubuntu "/home" partition!

---

### Post by lakku on 2007-10-20
Hmm, I'm amazed. :P 

I had to copy the folder 4 times to my home folder before I got it working. Oh well, thanks :)

---

### Post by ubu-for on 2007-10-20
> **lakku said:**
> Hmm, I'm amazed. :P 

It was a problem with your Windows partition (NTFS) and not with Steam. Don't use your NTFS programs with Wine. Copy them always to a Linux partition (ext2, ext3).

> **lakku said:**
> I had to copy the folder 4 times to my home folder before I got it working. Oh well, thanks :)

You're welcome!

---

