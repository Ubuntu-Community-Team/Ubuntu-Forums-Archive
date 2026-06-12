---
title: "Grub help"
date: 2009-05-06
forum: General Help
---

### Post by hobbes4725 on 2009-05-06
Ok, so I installed Ubuntu a while ago, to an external hard drive. In doing so, I had to install grub. And every time that I restarted my computer, I had to make sure that my external harddrive was plugged into my computer or else I would get a grub bootloader message( i can't remember the number, but I believe the error came from the fact that grub is located on my external drive, and not on my laptop's C: drive)  So I was wondering, is there a way to either change grub so it boots from my c: drive so i can restart my computer without the external drive, or is there a way to just completely bypass grub and boot into windows? I've tried going to the boot list, and tried every option, but none of them boot into windows...

---

### Post by adult swim on 2009-05-06
are you running vista or xp and do you have the install cd for whichever one you are using?

---

### Post by hobbes4725 on 2009-05-06
I'm running XP Professional SP3, and I do not have a install cd. I'm just wondering if somehow, I could move grub from my external to my c: drive so that I can use grub to boot into windows, and when I want to, load into Ubuntu.

---

### Post by hobbes4725 on 2009-05-06
I do however have the livecd that I installed Ubuntu with. I don't know if that information is useful or not, but I thought I should throw that in.

---

### Post by lindsay7 on 2009-05-06
I think this should solve your problem, pay attention to the part posted by Meierfra in this post.


[http://ubuntuforums.org/showthread.php?t=1098173](http://ubuntuforums.org/showthread.php?t=1098173)

---

### Post by adult swim on 2009-05-06
the problem arises because grub is on the mbr of your internal cd drive, not on your external drive.  when you boot your computer without the external drive, grub fires up and looks for /boot which is on your external drive (where your ubuntu installation is.)  it cannot find /boot so you get the error. 
to fix it you will need to get your windows mbr back on your internal drive.  you can do that with super grub disk [www.supergrubdisk.org](www.supergrubdisk.org) 
once you have that sorted out, the solution is to place grub on the mbr of your external hard drive, that way when you boot your computer without the external drive hooked up, it is as if ubuntu/grub has never been on your computer.  when you have your external drive hooked up, you will have to select to boot from the external drive and then ubuntu will boot.  let me know when you get windows mbr fixed and well work on getting grub on the external mbr
EDIT: mierfa's post in the link provided does what i wrote above but sidesteps downloading and burning super grub disk.  if it were me, id go with his advice!

---

### Post by hobbes4725 on 2009-05-06
I know have it running perfectly. Thank you both for the help.

---

### Post by lindsay7 on 2009-05-07
Glad it worked out for you good luck with your new os.

---

