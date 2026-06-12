---
title: "Monitor trouble"
date: 2005-09-18
forum: Desktop Environments
---

### Post by monkie on 2005-09-18
Alright well, I have been running a dual booted ubuntu 5.04 with xp for a week or so now, and it's been running fine. Well, my screen started to shake so I decided to edit my xorg.conf to change the refresh rate without making a backup (I know... sooooo dumb)

I can't remember the exact numbers, but I changed the vertRefresh I believe from maybe 75 to 60. So I rebooted and it boots up fine until it loads all my user settings i guess, because right before the login screen comes up my monitor goes all black and the little green lights to change the shape of the display and such all flash at the same time. Now I can type my username and password and login fine, I hear the music play.

Also, I tried booting up from the livecd and the monitor runs fine. From there I ran xorgconif I did all that. But it didn't work. Do you guys have any suggestions I could try without doing a full reinstall?

Oh, and my monitor is a Dell E551c.

I really need some help, please. :(((

---

### Post by monkie on 2005-09-18
bump :(

---

### Post by monkie on 2005-09-18
Alright well just to update. I did fix the problem. What I did was bootup into the livecd. Then made a directory called /mnt/hdd. Mounted my root drive on my hard drive to that directory and copied the xorg.conf file from the cd into /etc/X11/xorg.conf

worked liked a charm.

---

### Post by zenwhen on 2005-09-19
I am glad you got your problem solved, and am glad you updated your thread with the solution, even though you didn't get what you were loking for out of it. Thats classy.  :)

---

