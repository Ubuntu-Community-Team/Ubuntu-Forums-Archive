---
title: "dell help?"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by starmix on 2008-07-09
hi people dont know if this is the right place for this question but im a bit clueless.
my other half ordered a dell laptop and opted to have it with no operating system.
it arrived with ubuntu on it and neither of use have any idea of how to use it.
he wants windows xp installed on it so we purchased a windows xp disc but when we put it in the dell it wont run the installer program off the disk.

can anyone help?

---

### Post by AlbertTatlocksCap on 2008-07-09
Ok - it won't run from within the Ubuntu OS

You will have to boot off it when the computer starts up

Usually with Dells - press F12 when you see the DELL splash screen and that will bring up the bot menu then you will be able to boot from the XP CD

Hope this helps

---

### Post by pbarne on 2008-07-09
Have you changed the Boot order to Boot from CD first?
Hit F2 to go into the BIOS on power up and adjust the settings
in there.

Cheers,

Paul

---

### Post by starmix on 2008-07-09
i tried pressing esc in the start up menu but it only took me to the re-install menu
ill try that other way thanx

edit - right ok i set it up to boot from cd drive and it works but when it gets to step 2 it says cannot find hard disk drive installed?

---

### Post by noobb on 2008-07-09
This is my first experience using forums, so I hope I am doing this correctly.

By searching the web i found a deb package for the Dell Conexant modem in Ubuntu 7.10.  I also found instructions for setting up a dialup connection in Ubuntu 7.10

I installed the deb package (again using instructions here in Ubuntu forums), configured the dialup connection, added my account using $ sudo adduser NAME dip (and the corresponding one for dialout).  Nothing seemed to happen at all when I went to the terminal and went 'pon' -- 

I restarted and the modem started dialing out even before I logged in (which process did not go as smoothly as usual).  Once in, the modem was working and I could connect to the internet.  "Poff" didn't work - only $ sudo poff

Now everytime I log in, the modem dials out (unless its not plugged in, but even then I can hear Ubuntu looking for it.)

Something seems strange and I have no idea what to do about.  As mentioned I am running Ubuntu 7.10.  the machine is Dell  Optiplex GX280.

If anyone has any idea what is going on, I would love to get it sorted.  It is usable as is, but clearly isn't working correctly.

Thanks in advance for any help!

---

