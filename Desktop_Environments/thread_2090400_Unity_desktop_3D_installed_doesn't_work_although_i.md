---
title: "Unity desktop 3D installed doesn't work although it did from Live CD"
date: 2012-12-02
forum: Desktop Environments
---

### Post by amanchesterman on 2012-12-02
I have used Xubuntu happily for a couple of years but I want to try out the Unity desktop with a view to switching to it. I tried Ubuntu 12.04 (same as my version of Xubuntu) from Live CD and it appeared to work perfectly so I installed the desktop using
```
sudo apt-get install ubuntu-desktop
```No problems were reported with the installation, however when I log in now only Unity 2D works. If I select the 'Ubuntu' (3D) option at login the process stops with the desktop wallpaper: no panel, no launcher; and I have to log out to resume.

Can any one give advice as to what might be wrong? My computer is a middle aged Toshiba laptop, 32 bit, dual core Pentium processor, 2 GB RAM. The system info for 'graphics' says: 'driver - unknown' and 'experience - standard' -- is that a clue?

Thanks
John

---

### Post by elliotn on 2012-12-02
install compiz

---

### Post by elliotn on 2012-12-02
install compiz and ccsm

---

### Post by amanchesterman on 2012-12-02
Hi and thanks for your quick response.
The terminal reports that compiz is installed already. When I try to install ccsm it says: 'unable to locate package ccsm'. What do I do next?
Thanks, J.

---

### Post by amanchesterman on 2012-12-02
OK I found out how to install ccsm and did so, and activated the Unity plugin. But the Ubuntu desktop still won't start when I log in to the computer.

However Unity 2D and GNOME work fine, so at least I have alternatives to Xfce now.

Thanks
J

---

### Post by irv on 2012-12-02
From my own experience I found trying to run multiple desktop will sometimes give you problems. They seem to have files that conflict with one another. I found if you install Ubuntu with Unity first and then add other desktops things seem to work better. But when you start with Xfce and then install Unity it will give your problems.
What I do if I want to try different desktop I just install a fresh OS on a USB drive and run it from there. I tend to stick with one per install now.

---

