---
title: "failed to initialize HAL"
date: 2008-03-07
forum: Dell  Ubuntu Support
---

### Post by icorey on 2008-03-07
I keep getting the message "**failed to initialize HAL**" after booting up.  So, network-manager, the power manager, and any usb devices are not working (also, it takes a long time for the Quit dialog to pop up...don't know why).  I've read a number of threads on the issue and none of the fixes work or they don't apply to me (nothing about samba in /etc/fstab).

BTW, I'm running 7.10 on an e1505.

---

### Post by fragos on 2008-03-07
I haven't seen that message in a long time.  Reintiating boot always worked for me.  Establishing network connections with Samba or NFS is much slower than mounting a local drive which may be causing yoy some trouble.  I always initiate network mounts with a shell script which keeps these mounts from slowing the boot process.  Ther is some parralell activities during boot which can effect the order those activities are completed.

---

### Post by icorey on 2008-03-08
Well, like I said, I'm not using Samba or anything.  The only drives being loaded are the hard drive and and the optical drive.  And, rebooting has done nothing.  I've done it like a million times since I first got the message (two times after leaving it off all night) and I still get the HAL error.

I thought of another problem.  IDK why, but whenever I restart X with Ctrl Alt Backspace, X crashes.  At least I assume it's X, the error I get is just a bunch of rectangles.  Hopefully this is just related to the HAL error and not something completely different.

---

### Post by terry_gardener on 2008-03-09
i have just starting getting this message and i solved it by opening synaptic and reinstalling the package HAL

hope this helps

---

### Post by coco banderos on 2008-04-29
Found a solution that worked for me (thinkpad X61 running 8.04)

I was getting this error all day today, with the following message in dmesg:

"Failed to connect to socket /var/run/dbus/system_bus_socket:"

I finally ran all of the commands in the third post of this thread:

[http://ubuntuforums.org/showthread.php?t=692817](http://ubuntuforums.org/showthread.php?t=692817)

I ran all of the commands, except for these changes:

[LIST]
[*]Change lines 2 and 3 to update-rc.d
[*]I only ran "sudo apt-get install --reinstall hal", not hal-info or hal-device-manager
[*]Didn't need to run "sudo mkdir /var/run/dbus"
[*]ran "sudo chown messagebus:messagebus /var/run/dbus" and "sudo chown messagebus:messagebus /var/run/dbus/*" (or just "sudo chown -R messagebus:messagebus /var/run/dbus")
[/LIST]

Seems to be working.  We'll see how long it lasts...

---

