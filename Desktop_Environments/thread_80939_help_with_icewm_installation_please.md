---
title: "help with icewm installation please"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kewler on 2005-10-23
So I thought I'd try to install icewm. I've only had ubuntu for a couple of days so I'm not very good at using it. Anyway, here is what I did: I opened a terminal and typed in ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install icewm
``` well apparently that wasn't the name of the package so I did ```
sudo apt-cache search icewm
``` but nothing was returned. So I've also downloaded the icewm-1.2.23.tar.gz, but I don't know how to install it from the tar. I looked at the FAQs and manuals at icewm.org but I didn't understand anything. Also searching these forums I didn't find any help.

So, how do I get IceWM to work?

---

### Post by yourmanpann on 2005-10-23
You need to enable universe in /etc/apt/sources.lst

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

then

sudo apt-get install icewm icewm-themes

Good luck!

---

### Post by Peter76 on 2005-10-24
When added universe repository:
sudo apt-get update ( so apt-get can see universe packages )
sudo apt-get install x-window-system-core gdm icewm
Good luck

---

