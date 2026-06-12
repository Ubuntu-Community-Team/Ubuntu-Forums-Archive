---
title: "GDM broken"
date: 2006-09-16
forum: Desktop Environments
---

### Post by mthaddon on 2006-09-16
Hi Folks,

I rebooted my machine at work the other day, and for some reason X is broken - I can't even get to the login prompt. Basically it looks like it's trying to get there, but every few seconds it falls back to a black screen, and then tries again. I think I see the mouse icon (can't exactly remember, as I say, this is on my work machine) before it fails to show the login window.

I can login to the box via ssh while it's doing this, and I tried /etc/init.d/gdm restart, but didn't seem to make a difference. I tried another kernel and that didn't seem to help at all. If I choose recovery mode I can get to the command prompt and login as root, and interesting I can do "startx" and get to the desktop (as root), but obviously with a few errors about some services not being started (power management, I think).

I have a feeling that it may be related to some e17 packages I installed from the edevelop.org archive:

deb [http://edevelop.org/ubuntu](http://edevelop.org/ubuntu) dapper e17
deb-src [http://edevelop.org/ubuntu](http://edevelop.org/ubuntu) dapper e17

So I'm assuming the first thing to try is uninstalling these packages. Can anyone let me know how to uninstall all packages from a given repository (or if there's something else I should try first)?

Thanks, Tom

---

### Post by Feanor on 2006-09-17
I suggest you to see what DM you are using. If you're using entrance (is a login manager such as GDM but provided by edevelop.org) it's possible is it that creates problems.

I use sysv-rc-conf to see my runlevels (this isn't the only way you can do it) and what they launch, so if you run
```
sudo sysv-rc-conf
```
go to column 2 and remove the X on entrance and assure that there's one on GDM than reboot (or stop entrance and restart gdm)

if you haven't sysv-rc-conf installed
```
sudo apt-get install sysv-rc-conf
```

You can also try to simply remove entrance
```
sudo apt-get remove entrance
```
and then reboot or stop entrance and restart gdm

Anyway, if you have nvidia video card the problem can be due to this
[http://ubuntuforums.org/showthread.php?t=257459]("http://ubuntuforums.org/showthread.php?t=257459")

hope this can be useful
Cheers

---

### Post by mthaddon on 2006-09-17
Thanks, I'll give that a try on Monday. I'm using an Intel card, so I don't think it's the NVIDIA issue, and when I tried logging into e17 from GDM I got a seg fault, so if it is using entrance instead of gdm that would be likely...

Cheers, Tom

Update: sudo apt-get remove entrance fixed it all. Thanks!

---

