---
title: "Extremely slow past &quot;Preparing Restricted Drivers&quot;"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Dimebag on 2006-07-22
I am almost a complete newb to linux in general, but I managed to get an Ubuntu 6.06 box up and running. I managed to get all the drivers working (at least it appeared so), as well as set up tv-out. The first problem I noticed was that my primary monitor would for some reason did not have the option to do 1280x1024, I know both the card and monitor are capable, yet the highest res I was aloud was 1024x768. The computer was running smoothley although I did seem to be running slow (I would click the shortcut for pretty much any program it would say starting program, then it would disappear from the taskbar for a minute or two then finally open. I had come to terms with this as I could not find a solution and just assumed it was the fact I am running the OS on an old 20GB Seagate. The real problem started when I tried to set the monitor and tv on dual view. Things have kind of gone fubar since then, but basically I made some changes to xorg.conf, and rebooted to an extremely slow boot starting with "Preparing Restricted Driver.." the slowness persists and it usually takes 5-10 minutes to reach login screen, then once I am finally able to login I must wait another 5-10 minutes for Gnome to load, and another few minutes until I can even think of opening an application, which continues to take 10 or so minutes to open. I rolled back my xorg.conf files to before I added the tv and unplugged it, and I rolled back smb.conf just in case that might be causing slows, but it continues to do this in gnome or KDE. I can't really find any problems so specific and unusual experienced by other people. I dont know what config files to post here to give full information, but let me know which ones and I will post them here.

Thanks

---

### Post by mc_bizon on 2006-09-14
i have the same problem

---

### Post by nikhilk on 2006-09-14
Could you post your machine configuration?

---

### Post by mc_bizon on 2006-09-15
today it started working normally again. maybe because i installed updates

---

