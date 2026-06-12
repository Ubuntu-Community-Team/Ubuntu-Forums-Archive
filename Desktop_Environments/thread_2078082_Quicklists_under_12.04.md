---
title: "Quicklists under 12.04"
date: 2012-10-30
forum: Desktop Environments
---

### Post by RogerD on 2012-10-30
Does anyone know how to get quicklists working with 12.04?

I quite like Unity - the left of the screen is a good place for a launcher, but I can't get on with the way I'm obliged to access multiple minimised files within a single application. Double clicking on the icon, and then trying to identify the file I want from the multiple images on my screen just seems clumsy. How much easier, as with Docky, to be able to right click on the application icon, and then scroll to the file I want.

There are a number of websites supposedly offering scripts for implementing the same thing under Unity, in the form of quicklists, e.g. at [http://www.ubuntugeek.com/unity-window-quicklists.html:](http://www.ubuntugeek.com/unity-window-quicklists.html:)

sudo apt-add-repository ppa:alanbell/unity
sudo apt-get update
sudo apt-get install unity-window-quicklists

But when I try this, and othes a bit like it, nothing happens, and yes I have rebooted.

Help anyone?

Regards

Roger D

---

### Post by flint5 on 2012-10-30
You need this fix to work:

sudo sed -i 's/OnlyShowIn=UNITY/OnlyShowIn=Unity/g' /etc/xdg/autostart/unity-window-quicklists.desktop

---

### Post by RogerD on 2012-10-30
I think I've already tried this. Here's what I get:

roger@main-desktop:~$ sudo sed -i 's/OnlyShowIn=UNITY/OnlyShowIn=Unity/g' /etc/xdg/autostart/unity-window-quicklists.desktop
[sudo] password for roger: 
sed: can't read /etc/xdg/autostart/unity-window-quicklists.desktop: No such file or directory
roger@main-desktop:~$

---

### Post by flint5 on 2012-10-30
I have it installed on my ubuntu 12.04, and it works fine.
Are you sure you got it installed?

---

### Post by flint5 on 2012-10-30
Try to download the .deb file from here: 
[https://launchpad.net/~alanbell/+archive/unity/+sourcepub/2310146/+listing-archive-extra](https://launchpad.net/~alanbell/+archive/unity/+sourcepub/2310146/+listing-archive-extra)

Install it, use the fix, and reboot the system.

---

### Post by RogerD on 2012-10-30
It's working!

Many thanks for your help.

Roger D

---

### Post by flint5 on 2012-10-30
You're welcome!!!

---

