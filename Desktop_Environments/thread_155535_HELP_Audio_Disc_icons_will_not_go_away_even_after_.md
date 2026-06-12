---
title: "HELP: Audio Disc icons will not go away even after unmounting/ejecting"
date: 2006-04-05
forum: Desktop Environments
---

### Post by brian g on 2006-04-05
I have all these Audio Disc icons all over my desktop and in "Computer" . i can not get to go away (unless i reboot, but i don't feel i should have to do that to get rid of some icons). My CD/DVD drives are all empty, but these icons just stay. When i put a disc in and then eject it it produces another icon. i've tried ctrl+r to refresh the desktop. when i click on them it says Couldn't display "cdda:///dev/hdd" .. so i tried sudo umount /dev/hdd and it gets an error saying that it isn't mounted
**how can i get rid of all these stagnant audio disc icons?**
Hiding them is not what i'm looking to do, i want them gone and I dont want them to appear unless I have a disc in the drive.
so how do i clear them out?

---

### Post by brian g on 2006-04-09
seriously.. ](*,)

---

### Post by nanotube on 2006-04-09
have you tried just hitting delete?

---

### Post by brian g on 2006-04-09
[QUOTE=nanotube]have you tried just hitting delete?[/QUOTE]
You cannot move the volume "Audio Disc" to the trash.
if you want to eject the volume, please use "Eject" in the popup menu of the volume.


i've ejected and all it does is opens the tray.
theres no disc in the tray
i close the empty tray, and icons still exist.

---

### Post by brian g on 2006-04-09
in "Computer" clicking on the drives icons displays the error..

"Couldn't display "cdda:///dev/hdd".
There was an error launching the application."

so i..

brian@bertha:~$ umount /dev/hdd 
umount: /dev/hdd is not mounted (according to mtab)

brian@bertha:~$ sudo umount /dev/hdd
Password:
umount: /dev/hdd: not mounted

---

### Post by jonjon09 on 2008-02-18
I have the exact same problem except mine says /dev/hdc instead of /dev/hdd
it's really annoying because I can't use anything in the cd drive once that icon appears unless I restart the computer. i completely blocks all use of the drive.

---

