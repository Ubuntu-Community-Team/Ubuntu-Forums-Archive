---
title: "Regaining functionality"
date: 2006-10-08
forum: Desktop Environments
---

### Post by Cythusly on 2006-10-08
I'm a new user to Dapper, and Linux in general.  I'm running a Gnome session.  Today I have been doing some things: set up GAIM beta3, a login for my parents, Flash, and the newest Java...  somewhere in there I noticed my second HDD (with all my information from my Windows install, everything, pictures, music... my life from the last 4 years) was no longer mounted on the desktop, neither was a link to the music folder I had on the desktop or any other desktop icons.  I tried to right click and found that I wasn't getting any response from that.

I have no idea what I've done, if anyone could help, it'd be great, thanks!

-Tyler

---

### Post by H.E. Pennypacker on 2006-10-08
Please go to Places > Computer, and see if the partitions you are talking about are located there.  If they are, you are facing another issue: the links to those partitions are not located on the desktop.

If you don't see them there, go to System > Administration > Disks (Disk Manager).  See if you can locate the partitions there.  If you can't, you have a mounting problem.  You'll have to research auto-mounting.

Download and install gParted.  See if your partitions show up through gParted.  If they are still there, they will definately be picked up by gParted.

---

### Post by Henry Rayker on 2006-10-08
I saw that you said you created a login for your parents. Are you positive that you are on your original account? I haven't ever created a second account on any of my installs, but it could be from that. Check all logins to see if any of the things you need are present. Also, try a reboot. Something might have locked up.

---

### Post by Cythusly on 2006-10-09
I just realized that I don't have access to my home folder, or my "filesystem".  I have checked System > Administration > Disks and the drives are there, but they're not showing up.

Rebooting is the first thing I tried, I've also tried shutting down completely and then starting from there... nothing's helped.

---

### Post by IoCaster on 2006-10-09
> **Cythusly said:**
> I'm a new user to Dapper, and Linux in general.  I'm running a Gnome session.  Today I have been doing some things: set up GAIM beta3, a login for my parents, Flash, and the newest Java...  somewhere in there I noticed my second HDD (with all my information from my Windows install, everything, pictures, music... my life from the last 4 years) was no longer mounted on the desktop, neither was a link to the music folder I had on the desktop or any other desktop icons.  I tried to right click and found that I wasn't getting any response from that.

I have no idea what I've done, if anyone could help, it'd be great, thanks!

-Tyler

You should be able to locate the drive in nautilus--> system files--> /media. You can also try terminal--> gconf-editor--> apps--> nautilus and put a check in the box for computer_icon_visible.

---

### Post by Cythusly on 2006-10-09
> **IoCaster said:**
> You should be able to locate the drive in nautilus--> system files--> /media. You can also try terminal--> gconf-editor--> apps--> nautilus and put a check in the box for computer_icon_visible.

There is a check box for computer_icon_visible checked, as well as volumes_visible, trash_icon_visibl- none of it is visible on the desktop.

---

### Post by IoCaster on 2006-10-09
> **Henry Rayker said:**
> I saw that you said you created a login for your parents. Are you positive that you are on your original account? I haven't ever created a second account on any of my installs, but it could be from that. Check all logins to see if any of the things you need are present. Also, try a reboot. Something might have locked up.

I read and even quoted his post and it didn't register, but you're probably spot on with that.

---

### Post by Cythusly on 2006-10-14
I figured it out- for some reason nautilus was either deleted or corrupted, so a quick reinstall and everything is working again, except the menu popup by right-clicking on the desktop, but I still need to reboot.  Thanks for all the suggestions!

---

