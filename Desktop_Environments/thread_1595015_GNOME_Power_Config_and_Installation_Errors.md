---
title: "GNOME Power Config and Installation Errors"
date: 2010-10-12
forum: Desktop Environments
---

### Post by ConfigYourLifeLoser on 2010-10-12
A couple of days ago on my Fujitsu Laptop which was nearing its end (in about 2 more years, I'll have to send it to the scrap pile:() I had a GNOME Power Configuration error. This is the story of my struggles and my thread of cries for help:

I was booting after installing an update for Maverick Meerkat, and I got a message during the load screen that said:

INSTALLATION PROBLEM:
The configuration defaults for Gnome Power Manager
have not been installed correctly. Please Contact
your system administrator.

So I dropped into GRUB During my 5th boot (while trying to boot once more in hopes it was just a boot error) and I selected the latest/updated version of Ubuntu, but I dropped into the recovery mode version so I could attempt some commands to try and fix it. Then, I dropped into the root terminal to attempt more commands to avoid specifying my networking device, and typing sudo before the commands.
I got on my alternate computer and searched my problem. I installed a whole bunch of crappy commands that didn't do anything, and ended up purging GNOME completely and doing:
sudo apt-get install kubuntu-desktop
Problem? It wouldn't boot. I would log on but it wouldn't load. Of all the sites I've visited to attempt to find the cure, a VAST majority of them said it was due to Ubuntu not letting you boot unless you have ATLEAST 180mb of free space on your root partition.
My last issue is that when I attempted to purge Kubuntu and reinstall GNOME, it says Kubuntu is uninstalled and GNOME IS installed. But both statements MUST be untrue because it boots Kubuntu, not GNOME.
What can you do?
1. Tell me how to purge/uninstall Kubuntu and get GNOME Ubuntu back.
2. Tell me how to free up space on root partition for future reference.
3. Tell me how to stop the Gnome Power Manager Default Settings error if the Root-Partition-Doesn't-Have-Enough-Disk-Space-To-Boot-Ubuntu isn't really the issue!

Oh my GOD thank you to whoever can fix at least ONE of the issues displayed above. I <3 whoever can fix this ISSUE!

---

### Post by ConfigYourLifeLoser on 2010-10-12
One more thing; The Gnome Power Manager errors DO NOT occur during log in. These occur when you enter the loading screen. Thankz

---

