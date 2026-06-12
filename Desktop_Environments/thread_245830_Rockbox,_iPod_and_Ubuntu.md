---
title: "Rockbox, iPod and Ubuntu"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Ay Deverrick on 2006-08-28
Back in the day, I used to use Windows, and got fed up with all the firmware issues with my iPod, so I went and put Rockbox on it.

Eventually, after using Linux off and on for two years, I jumped in and made the switch.  After getting everything tweaked just right for me, I decided to update my year+ old rockbox firmware.  Well, when I plug in my iPod, it automounts and everything, however all of the files are write protected.  I can go off and right click them all change their permissions that way, however that would take several hours due to the sheer amount of files on my iPod.

I've mostly used Debian in my previous linux endeavours, and I can't find where my iPod is mounted, so I can't just use chmod to quickly change the permissions of these files, and there isn't an entry in /etc/fstab for my iPod.  Can someone shed some light on this?

---

### Post by lagagnon on 2006-08-28
Open a terminal and type:  "tail -f /var/log/messages" . Now plug your iPod into your computer. Watch the messages to find out what device name the iPod has been given (often /dev/sda). Then:

sudo mount /dev/sda /media/ipod (or whatever).

---

