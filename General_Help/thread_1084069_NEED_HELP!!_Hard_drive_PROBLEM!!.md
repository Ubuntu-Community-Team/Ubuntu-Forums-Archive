---
title: "NEED HELP!! Hard drive PROBLEM!!"
date: 2009-03-01
forum: General Help
---

### Post by linux noooob on 2009-03-01
I ran ```
sudo dd if=/dev/zero of=/dev/hda bs=521 count=1
```  on a live CD so i could have a fresh install of ubuntu and windows but now on gparted on the live CD it says i only have 521 bytes of data!! HELP please :( The hardrive is 111.11 gb btw

---

### Post by mulligan.can on 2009-03-01
Umm, sorry, I don't get what that command was meant to achieve?

EDIT: I mean, I assume that was to erase the disk? That was your intent right? If not then, well, thats what you just did... Using gparted to start with would probably have worked easier...

---

### Post by linux noooob on 2009-03-01
This is really confusing!! I have /hda which is 502 b and sda which is 111.11 gb i am confused!? not to mention i have a grub 17 error!

---

### Post by WatchingThePain on 2009-03-01
You've only got 521 bytes because you gave it that option bs=521 so thats all it wrote.

---

### Post by caljohnsmith on 2009-03-01
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

---

### Post by jwbrase on 2009-03-01
> **linux noooob said:**
> This is really confusing!! I have /hda which is 502 b and sda which is 111.11 gb i am confused!? not to mention i have a grub 17 error!

As I understand it from the documentation, the command you put in, dd, copies "bs" bytes from "if" to "of," and does it "count" times.

/dev/zero is a special file that gives you as many zeroes as you read from it, and /dev/hda is your hard drive.

So the command you put in means "Copy 521 bytes worth of zeroes to the hard drive. Do this once."

So in effect, I think what you've done is created a blank partition of 521 bytes on your hard drive.

Grub error 17 is what Grub gives when it can't recognize the filesystem on the partition it's been pointed to. Your Grub menu.lst file is probably pointing to hda. Since hda is a blank partition, it doesn't have a filesystem, and since it's only 521 bytes, it probably wouldn't have room for one.

---

### Post by WatchingThePain on 2009-03-01
Wouldn't fdisk or something similar be a better way to prepare for a clean install?. If you are trying to get a lower level of formatting you might need a disc utility for that.

---

### Post by linux noooob on 2009-03-02
After installing ubuntu again it all went away thanks for the help though :D

---

