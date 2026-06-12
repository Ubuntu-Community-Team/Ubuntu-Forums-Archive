---
title: "mounting a generic mp3 player"
date: 2009-08-31
forum: Desktop Environments
---

### Post by andrea000 on 2009-08-31
I am trying mount a generic mp3 player i know it
will work with ubuntu because the person i got it
off of uses ubuntu 9 and all he did was plug it in
it's a oasis mp3 playerlibmtp and mtptools are 
installed.Sometimes i can get it to show up in
nautilus but when i click on it a error pops up
telling me it could not mount the device.

---

### Post by dE_logics on 2009-09-01
Does the Mp3 player use Microsoft filesystems?...if so they are corrupt.

Boot into windows and do a file check of that partition in the mp3 player.

---

### Post by andrea000 on 2009-09-01
Thank you i have it going now this is what i did

1)I opened a terminal and did a back up the existing
fstab file sudo cp /etc/fstab /etc/fstab.bak
2)Edit the fstab sudo nano /etc/fstab
3)Next i added this line to the fstab file assuming
my hda1 filesystem is ntfs: /dev/hda1 /media/hda1
ntfs defaults 0 0 (and i was assuming so dont do this
unless you know
4)In the terminal again, enter sudo mount -a to refresh
the fstab.
5)Then finally i entered cd /media/hda1 then dir to test.

That's it i hope this helps someone have this same
problem

Thank you

---

