---
title: "Can't lock launchers on panels."
date: 2010-02-28
forum: Desktop Environments
---

### Post by aj7360 on 2010-02-28
For some reason, when adding launchers to panels (I have three displays with 2 GPU's) they are not there are restarting X.

I've tried the "lock to panel" option after adding them but no luck.

I just installed 64bit 9.10 yesterday.

Prior to that I was running 32bit 9.10 which had started out as Kubuntu. I then switched to Gnome as I didn't like it. But I guess KDE was still underneath everything as I could see it when I rebooted or shut down.

Why does that matter? 

In preparation for the reinstall, I copied the contents of /home to an external USB drive with rsync. 

Then (stupidly) copied everything back the same way. So a lot of old dot files also got copied back which I suspect wasn't a good idea, or maybe not.  Even stupider was the fact I had the --delete command included. I stopped the rysnc before it was done but suspect the damage was done. 

I suppose I could just start over again but getting my 3 displays to work was a terrible pain (nvidia-settings refused to write to the xorg.conf file until I switched to a different driver)

And my vpnc does work like it did before, minimizing to the system tray.

All in the interest of being able to run 8GB of RAM to support VirtualBox. 

Any suggestions concerning the launchers would be appreciated.

Thanks

Alan

---

### Post by asmoore82 on 2010-02-28
Try logging out and back in and see if the launchers stick around.

If they don't, it's probably a problem with file permissions.
If they do, you may have found a bug in restarting whereby the panel is getting killed before it can save.

The big problem with USB drives is that the FAT filesystem cannot handle UNIX file permissions.

---

### Post by aj7360 on 2010-02-28
Definitely sounds like a permissions problem.  So I chmodded every single file and directory in home, logged out and back it... still the same thing.

Except... now VirtualBox tries to start up. (which I just reinstalled)

On the previous install it was not configured to autostart.

There are also two xterm windows open (those were there before)

At least I figured out the Vpnc problem. 

Oh.. the launcher for xterm does stay on the display0 desktop panel.

---

### Post by asmoore82 on 2010-02-28
> **aj7360 said:**
> So I chmodded every single file and directory in home,

How? remember that by default the wildcard ``*'' doesn't do hidden "dot" files.
Also, if you copied them back as root or with sudo, you will need to chmod **and** chown them.

---

### Post by aj7360 on 2010-02-28
Correction... I ATTEMPTED to chmod 'Em! &#58372;. Will try that later when I get home

---

