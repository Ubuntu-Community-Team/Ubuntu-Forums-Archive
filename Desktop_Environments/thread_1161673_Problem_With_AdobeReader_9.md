---
title: "Problem With AdobeReader 9"
date: 2009-05-16
forum: Desktop Environments
---

### Post by vijaysarathy on 2009-05-16
Hi all,
 I installed AdobeReader 9 by using (in terminal as root)
         1) chmod a+x AdbeRdr9.1.0-1_i486linux_enu.bin
         2) ./AdbeRdr9.1.0-1_i486linux_enu.bin

I opened it through Applications --> Office --> AdobeReader 9.

The problem is that it opens and closes immediately. I am unable to open/read any .pdf files through AdobeReader 9.

Anyone pls help me ...
Thanks in advance..

---

### Post by Vostrocity on 2009-05-16
I don't know a solution, but why are you using Adobe Reader? That is a horrible piece of software.

---

### Post by andrea000 on 2009-05-17
The package name is wrong or it was at one time and it may still be.

Try removing it then if you still need it reinstall

sudo apt-get remove adobereader-enu

---

### Post by _Purple_ on 2009-05-17
Remove it and try to install it from the repositories. Type in terminal
```
sudo apt-get install acroread
```

You can use Evince which is the default PDF reader in Ubuntu. I have tried Adobe reader 9 and one problem I found was it does not allow you to save files on FAT or NTFS partitions unless you run it with gksudo.

---

