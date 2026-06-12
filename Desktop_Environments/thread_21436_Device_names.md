---
title: "Device names"
date: 2005-03-22
forum: Desktop Environments
---

### Post by graabein on 2005-03-22
A few questions on Nautilus and the desktop...

- How do I rename "CD-ROM 1" and "CD-ROM 2" in Nautilus Computer? I want to call them "DVD" and "CD-ROM". I tried starting Nautilus as root and I got to edit the names but no changes were saved.

- How do I configure the USB devices to display label name instead of sda1/sdb1? Both my CD and DVD works just fine with label names. My USB devices got their real label name when I booted "Warty" Live CD.

---

### Post by lorap on 2005-03-23
hi friend!
your problem's pretty small one.
i'm not currently at my pc then one thing you'll need to check yourself,but the whole precess's like this.
FIRST:you've the name you want to be changed in two places.one in "/media" and the second in "/etc/fstab".fstab is a file you'll need to open and edit.
SECOND:to change any name in a system directory you've to be the root user.
now let's work.

ALEF:there's a command called "rn" - rename or "rndir" - this you'll have to check on your own in "/bin" directory,it'd be very easy.but once you got the name of a command say it's "rndir" you do this:

sudo rndir /media/dvd /media/cdrom1

before you use this command you've to check who should be the firs the new name or an old one.to check that write this:

man rndir

this'll print you the help on this command.be i at my pc now i'd do it for you but as soon as i'm not at home you'll need to check it yourself.

BET:once you've the names in "/media" changed you open "fstab" and change it this way:

sudo nano /etc/fstab

once you've it open change in the lines the names in media from /media/cdrom0
to /media/dvd.the same about the second one.
to save the changes press "ctrl+o" then "enter".to close "ctrl+x".
now you're done :-)
have a nice day!
pavel

---

### Post by graabein on 2005-03-29
Thanks! I tried it during the holiday and it worked great! 


Btw, how do I configure sda1 and sdb1 to show the label name of mounted media instead of just sda1/sdb1?   :-(

---

