---
title: "simple networking mount question..."
date: 2006-01-08
forum: Desktop Environments
---

### Post by recklessray on 2006-01-08
hi, i have two desktops, one runs breezey and the other xp, and a laptop running breezey.

breezey desktop "linux-box" 192.168.1.100
xp desktop "music-box" 192.168.1.104
breezey laptop "lappy" 192.168.1.102

i have a drive mapped from 'music-box' which i connected to from 'linux-box' using the connect to server utility. it found the shared drives and poped a nice icon on my desktop, so its cool now i can access files on the xp computer no hasle. same goes for the laptop, i have an icon on the desktop which opens to the shared directories on the laptop.

my question is, how can i mount these drives and is it posible to mount them from fstab when i boot? i would like to be able to stream music from the xp box and play it on 'linux-box' but my player (cplay) needs to see the directory and doesnt seem to be able to use shared folders and such like...

im sure this is doable and probably quite simple. a friend of mine who is a bit of a linux guru did it for me a while ago but i have to reinstall ubuntu since then due to a hardware upgrade... please keep any advice simple as im a relative noob.

any help will be most gratefully received!

best regards, ray :)

---

### Post by recklessray on 2006-01-08
by the way, not sure if its relevent, but i use a wireless four port switch/router and the laptop is wireless - the desktops are wired.

---

### Post by recklessray on 2006-01-08
anyone?

---

### Post by lamego on 2006-01-08
I didn't got your problem.
Aren't you able to access to your shared folders on the XP box already ?
There is no such thing as drive mapping on linux, to access you your XP data the remote share will be mounted into a specific path on your linux system, not on a drive.
And yes you can setup a cron entry to automatically mount that remote share on a given path...

---

### Post by Zimmer on 2006-01-08
Hello,
Have a look here for general Samba Networking issues posts #5 - #9
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
and this
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

maybe you will find what you need there...
Regards

---

