---
title: "I broke my wubi installation of jaunty"
date: 2009-06-07
forum: General Help
---

### Post by AndrewYY on 2009-06-07
Earlier today, I was transferring some files from my desktop on jaunty to my usb device.

I started to fiddle with compiz a bit while I waited for the transfer to finish (it was roughly a 300mb file)

Suddenly, everything on the screen froze with the progress bar at about halfway. I tried pressing a bunch of keys, but nothing really worked. I guess it's useful to point out that my mouse was the only thing still moving around, though I couldn't click on anything.

I held the off button for a few seconds and the computer turned off.

When I rebooted, it took me to the screen where I could pick between windows and ubuntu, so I picked ubuntu. Instantly, I am face to face with a grub command line.

I ran:
[FONT="Courier New"]kernel /ubuntu/winboot/wubidr.mbr[/FONT]

which appeared to have worked

and then I ran
[FONT="Courier New"]boot[/FONT]

which crashed.

When I switched to windows, I looked at the ubuntu folder and realized the entire folder [FONT="Courier New"]C:/ubuntu/disks[/FONT] was corrupt.

Is there any way to rescue my ubuntu, or at least my files?

---

