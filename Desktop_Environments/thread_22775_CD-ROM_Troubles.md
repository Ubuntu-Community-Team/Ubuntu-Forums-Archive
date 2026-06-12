---
title: "CD-ROM Troubles"
date: 2005-03-29
forum: Desktop Environments
---

### Post by orion_114 on 2005-03-29
I seem to be unable to mount CD-ROMS. :(
I tried to right click--> "mount volume" in the browser and that didn't work and I have tried
sudo mount /media/cdrom0/ -o unhide
but I cant seem to see the disc at all!
Anyone got any ideas on what is going wrong ?
I am running hoary preview.

The other thing is when I reboot my machine the Disc seems to mount but then the buttons on my CD-ROM drive dont work, I have to click eject in ubuntu to get the disc out. :(

---

### Post by Declan on 2005-03-29
I can't help, but I can report that my CD-Rom is behaving a bit unpredictably since a recent update.  Everything had been going fine, but now it fails to mount the filesystems on certain discs, fails to recognise audio discs sometimes, and always fails to recognise DVDs.

None of this was the case until about 4 days ago, and it did coincide with an update.
I'm not sure however whether it might not in fact coincide with a hardware problem.
Does anyone know a way to check the health of a CD-ROM drive when it is misbehaving, in order to see whether the problem lies at the hardware or at the software level?

I know that my question is not the same as the thread originator, but I hope that by asking it in the same thread some nice person will come along and point us in the right general direction with regards to diagnosing such problems.

Thanks,

Declan

---

### Post by lorap on 2005-03-30
hi friend!
i'll try help you.
first of all let's get your usb device working.
if you're running warty your usb driver should be "sr0".
then to have your usb storage device working do the next:

i.create a directory "usb-cd":

sudo mkdir /media/usb-cd

ii.open "fstab" file that resides in "/etc" directory:

sudo nano /etc/fstab

iii.now let's edit it,to do so add next line:

/dev/sr0 /media/usb-cd udf,iso9660,user,noauto,rw 0 0

iv.to save changes:

ctrl+o

v.to exit:

ctrl+x

p.s:
i'm not at my pc right now so forgive me if i didn't write everything in fstab file exactly,but once you've it open you'll be able see what the right sequence of the words like "user" or "noauto" should be,you just make everything like for internal cd record would be there already written by warty.
have a nice day friend!
pavel

---

