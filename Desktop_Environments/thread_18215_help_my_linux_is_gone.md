---
title: "help my linux is gone"
date: 2005-03-05
forum: Desktop Environments
---

### Post by kingofhell on 2005-03-05
i was a happy user of linux, was using grub for dual booting but since i reformatted my windows, theres no option to boot into linux. its not practical for me to abandon windows coz my linux cant display files with chinese name.

---

### Post by lorap on 2005-03-05
the only thing left to u is reinstall linux.
mbr was rewrited by microsoft so if u don't have rescue linux diskets that's the way to solve this problem.
pavel

---

### Post by bored2k on 2005-03-05
[QUOTE=lorap]the only thing left to u is reinstall linux.
mbr was rewrited by microsoft so if u don't have rescue linux diskets that's the way to solve this problem.
pavel[/QUOTE]


THATS NOT TRUE !!!!!

he HAS ubuntu disc thats ENOUGH !!

[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

> Q: How to restore GRUB menu after Windows installation?

   1. Read General Notes
   2.

      e.g. Assumed that /dev/hda1 is the location of /boot partition
   3. Read How to use Ubuntu Installation CD, to gain root user access?
   4.

      sh-2.05b# grub

      grub> root (hd0,0)
      grub> setup (hd0)
      grub> quit

Q: How to add Windows entry into GRUB menu?

   1. Read General Notes
   2.

      e.g. Assumed that /dev/hda1 is the location of Windows partition
   3. Read How to list the partition tables?
   4.

      $ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
      $ sudo gedit /boot/grub/menu.lst
   5. Append the following lines at the end of file

      title           Windows 95/98/NT/2000
      root            (hd0,0)
      makeactive
      chainloader     +1
      savedefault
   6. Save the edited file (sample)

---

### Post by daveintokyo on 2005-03-05
Um.......I feel a little underpowered to comment here... KoH, your Linux is not gone....(probably...I guess...) As last poster noted, the Master Boot Record has been overwritten by Windows, but everything is still there, probably...
So, if you look around "problems with dual booting" you will see this again, and again....."always install Lx after Ws".... You can retrieve your system....but, frankly speaking, as a newcomer I have found it easier to just re-install...Linux is much cleverer the Ws and gracefully accepts that it can live with a second OS,...So, the point is, as a newcomer we do not have lots of data to worry about, so a re-install, while a little embarrassing is not so bad......BUT If you do have lots of data , do not panic, everything is still there (probably).......

---

### Post by daveintokyo on 2005-03-05
Ahh..while I sat and wrote my message, someone who knew more came along!....sorry bored2K... I was trying to stop a panic re-install if there was a lot of data at stake...!

---

### Post by bored2k on 2005-03-05
[QUOTE=daveintokyo]Ahh..while I sat and wrote my message, someone who knew more came along!....sorry bored2K... I was trying to stop a panic re-install if there was a lot of data at stake...![/QUOTE]
 lol its ok i just  more or less learned that little trick some weeks ago and ive noticed not many ppl use it .

btw if u like Re Installs [like me - i do it lik, all the time], during the partition step input > do not format - leave partition intac < and i doubt it will delete files.

thats why i have my$Home in another partition, i can reinstall as many times as i want to, my data will never be gone ... tho my sweet configs will :(

---

