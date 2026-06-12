---
title: "Truecypt install script wont run under 11.10"
date: 2011-10-14
forum: Desktop Environments
---

### Post by cavedog on 2011-10-14
I've just done a fresh install of Lubuntu 11.10 on my Asus 1001PX, using the alt install and using the full disk encryption option.  I have attempted to install Truecrypt, but the script doesn't seem to execute, even with I attempt to open that directory as root (which also doesn't seem to work, as I don't get the indications that it has opened as root).


What am I doing wrong/ not doing?

---

### Post by nosport on 2011-10-16
> What am I doing wrong/ not doing?


Nothing, apparently.  I have the same problem here; it installed fine under Lubuntu 11.04, but not under 11.10.

Help anyone?

---

### Post by nosport on 2011-10-16
I did it manually; here's what worked for me:

Go to [www.truecrypt.org](www.truecrypt.org) and download the ubuntu .tar.gz file.  It should end up in your Downloads folder.

Open file manager (folder icon on menu bar)
Double click on Downloads folder
Double click on Truecrypt package
Select Extract (to unpack the archive into same folder)

Open a terminal window (menu/System Tools/Terminal).
At the prompt, type: cd /home/ubuntu/Downloads (to go to folder)
Type: ls    (to list the files in the folder, just to check you're in the right folder)
Type: sh truecrypt-7.1-setup-x86 (or whatever version is there)
Answer the questions, pressing enter many times, yes, and so on.
The SHell script should install Truecrypt. 

Good luck.
-N O'S

---

### Post by llelectronics on 2011-10-17
There is a deb package I created originally for Neptune but it works on Ubuntu/Lubuntu aswell: 
Just download and install:
[http://zevenos.dyndns.org/repo/pool/main/t/truecrypt/truecrypt_7.1_i386.deb](http://zevenos.dyndns.org/repo/pool/main/t/truecrypt/truecrypt_7.1_i386.deb)

---

### Post by cavedog on 2011-10-17
> **nosport said:**
> I did it manually; here's what worked for me:

Go to [www.truecrypt.org](www.truecrypt.org) and download the ubuntu .tar.gz file.  It should end up in your Downloads folder.

Open file manager (folder icon on menu bar)
Double click on Downloads folder
Double click on Truecrypt package
Select Extract (to unpack the archive into same folder)

Open a terminal window (menu/System Tools/Terminal).
At the prompt, type: cd /home/ubuntu/Downloads (to go to folder)
Type: ls    (to list the files in the folder, just to check you're in the right folder)
Type: sh truecrypt-7.1-setup-x86 (or whatever version is there)
Answer the questions, pressing enter many times, yes, and so on.
The SHell script should install Truecrypt. 

Good luck.
-N O'S

Thanks a bunch.  I was starting to think I'm losing my mind.

---

### Post by nosport on 2011-10-18
> **llelectronics said:**
> There is a deb package I created originally for Neptune but it works on Ubuntu/Lubuntu aswell: 
Just download and install:
[http://zevenos.dyndns.org/repo/pool/main/t/truecrypt/truecrypt_7.1_i386.deb](http://zevenos.dyndns.org/repo/pool/main/t/truecrypt/truecrypt_7.1_i386.deb)

Excellent, thanks for creating it.
-N

---

