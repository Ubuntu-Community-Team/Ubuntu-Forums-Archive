---
title: "Unable to eject CD"
date: 2005-09-13
forum: Desktop Environments
---

### Post by otey on 2005-09-13
My CD-drive wont eject my cd. 
When i press eject on my CD-drive, nothing h1appens. 
When i rightclick on the drive in "computer://" and choose eject, i get the error message: 

Unable to eject media

* Show more details
   eject: unable to eject, last error: Invalid argument

What should i do?

---

### Post by odin on 2005-09-13
try unmount it manually with umount

for example try:

umount /dev/cdrom 

and then try eject again.

note that for unmounting you cant be using your cd drive with any program.

---

### Post by otey on 2005-09-13
otey@osys:~$ umount /dev/cdrom
umount: /dev/hda is not mounted (according to mtab)
otey@osys:~$


I have tried to eject, when mounted and when unmounted.

---

### Post by Thiago on 2005-09-13
otey, try umount /media/cdrom

---

### Post by FLeiXiuS on 2005-09-13
[QUOTE=Thiago]otey, try umount /media/cdrom[/QUOTE]

Also add the -f parameter to force it to unmount regardless..

umount -f /media/cdrom

---

### Post by Curlydave on 2005-09-13
This is one of the things that I love about Linux. You ask how to eject a CD because the button is borked by gnome or whatever has borked the button, and people tell you to enter a bunch of console commands.  :-P

---

### Post by otey on 2005-09-14
[QUOTE=FLeiXiuS]Also add the -f parameter to force it to unmount regardless..

umount -f /media/cdrom[/QUOTE]

I tried everyting. And i unmounted the cd. but the cd-drive just held on to it. I also tried to force unmount to see if that would make it ejectable. But it did'nt. Then I exited Gnome, and it worked. I have not had the same problem since. 

Maybe it is nothing to worry about.

---

