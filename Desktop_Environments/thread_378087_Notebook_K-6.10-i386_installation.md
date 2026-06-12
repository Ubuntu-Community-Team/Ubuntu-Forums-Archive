---
title: "Notebook K-6.10-i386 installation"
date: 2007-03-06
forum: Desktop Environments
---

### Post by SRTS on 2007-03-06
I finally convince a friend to try Linux on his notebook (HP Pavilion dv5000, Duo Core). I suggest KUbuntu 6.10 (i386).

Graphical installation...partitioner comes up, I set root mount point and confirm. We get the message telling us that no root mount point has been set. I restart the thing to get to text installation, maybe that works. On choosing "restart" in the K menu, at the end of shutting down it asks to remove the CD and click ENTER. I do so. Nothing happens. I try some more times, nothing. Time to shut off/on the machine via its switch.

Text mode installation. Works. For some reason I'm not getting an option to choose packets I want to install, but oh well, can do that later. KDM comes up, logging in, Desktop comes up.. No drive icons on the desktop.

Trying to configure WLAN..click on K-menu, internet, set up wlan, it says "no wlan device found, program is now exiting" or similar. Bam. I try to google on a second PC about the reasons. No solution to be found quickly. We shut the **** down. I've already embarrassed myself enough in front of my friend for tonight.

At home I fire up my own KUbuntu (6.06), which I haven't used for a while. Trying to google for solutions. After searching frigging forums and mailing lists for 1 annoying hour I finally get some ideas of the problem. Decide to put the files on USB stick to bring them over to my friend tomorrow. Also I notice that a lot of updates are available from the indicator icon in the panel tray. I do a packet upgdate first. Now plug in USB stick. Konqueror shows it as usual.. then "an unknown error has occured". I can't access the stick. I google for another 30 minutes, until I finally find ONE posting of someone who has a solution..found out on his OWN. Bug in 3 HAL-related packets. Have to downgrade them from 18.2 to 18.1. I do that..USB works again! Hoorrayy!

Oh yeah, and I still have no sound in JAVA thanks to the whole ALSA/OSS/blablabla sound nonsense, except for when the JAVA app is the only application running that uses sound at that time. During that time, no other app will be able to produce sound then of course.

This is a horrible waste of my time trying to fix bugs..like what? Sound and even U S B? Give me a break. Booting back to Win2k for today since I won't have enough time for some more hours of googling today unfortunately.


I hope someone who is able to improve the system will read this, those issues have to disappear. While I'm mentally exhausted from trying to get Linux established on ppl's desktops here (including my own) I'd still be glad to accept any suggestions on how to fix this stuff.

---

