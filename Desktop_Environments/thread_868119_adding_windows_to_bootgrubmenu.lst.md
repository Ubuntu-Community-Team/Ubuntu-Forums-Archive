---
title: "adding windows to /boot/grub/menu.lst"
date: 2008-07-23
forum: Desktop Environments
---

### Post by systemshock869 on 2008-07-23
I'm not sure if this is the right forum.. oh well

I was updating stuff using Adept, and it said there was a new version of menu.lst available, but that mine was locally edited, and asked if I wanted to keep my old one or install the new one.  I installed the new one, and it finished updating and needed to reboot.  So I did.

I had edited menu.lst to list windows first, and changed the line that says 'other operating systems' to 'linux,' and put linux under there, because I couldn't figure out how to have it boot to Windows by default otherwise.  

So when it updated menu.lst, it kept my modified 'other operating systems' section and changed the rest, therefore giving me at least 8 different ways to boot linux, and none to boot windows.

How can I get my windows option back??  I should have saved a copy before I changed it.  I'll know next time I guess.  I have no Idea what it should say to boot windows.

Windows is installed in the first partition of the only hard drive though, if that helps

thanks!!

---

### Post by tamoneya on 2008-07-23
here is what I use for windows:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
You can add it into grub where ever you prefer but note that you may need to change (hd0,0) depending on your configuration.  (hd0,0) = /dev/sda1.  I you dont know what partition your windows OS is on please show us the output of ```
sudo fdisk -l
```

---

### Post by systemshock869 on 2008-07-23
hey, I appreciate it!
It's on hda1

---

### Post by tamoneya on 2008-07-23
in grub hda1 = (hd0,0)

---

