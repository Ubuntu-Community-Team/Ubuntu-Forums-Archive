---
title: "KDE/M not working after dist-upgrade"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Anakashar on 2005-10-14
I am wondering if I should go and reinstall Kubuntu to a clean partition.

After changing my sources.list file to reflect the "breezy" form, I did sudo apt-get update, then sudo apt-get dist-upgrade.  At this point, it told me that it needed to uninstall/remove a lot of libs and I even saw, I think it was, "kde-desktop."

After a series of update and dist-upgrade, I managed to get to the "Nvidia" splash-screen, then it goes back to the console.  Typing sudo /etc/init.d/kdm start produces "KDM already running" and kdm restart  produces "restarting KDM," Nvidia splash-screen, then back to the console.

I did sudo apt-get install Kubuntu-desktop, and that didn't do anything.

In a previous post I read about sudo dpkg-reconfigure xserver-xorg, and tried that, but nothing really changed.

I'm sure I have "dri" and "GLcore" disabled in the xorg.conf file.  The bit-depth is the same as it was with Hoary, as are the resolutions.

This is an Nvidia card. (6600 GT, PNY)

Should I just go ahead and format the partition and reinstall, or is there something I can do to correct this?

---

### Post by Jonathan2007 on 2005-10-14
I don't know if this will help but...
[http://ubuntuforums.org/showthread.php?p=400498](http://ubuntuforums.org/showthread.php?p=400498)

---

### Post by Anakashar on 2005-10-14
Well, I can get into the KDM if I change the "Driver" from "nvidia" to "nv" but then it starts to mess up and all sorts of things.

I'm venturing a guess I need to reinstall the nvidia drivers?

---

### Post by quique on 2005-10-15
A few days ago I had problems whit a kernel update and the nvidia drivers, The correcy way was apt-get install nvidia-glx, maybe the answer.

---

### Post by f1dave on 2005-10-15
Make sure you have:

linux-restricted-modules-2.6.12-9
nvidia-glx
nvidia-glx-dev

Those first two will be needed from memory, the last might not be.

---

### Post by Anakashar on 2005-10-16
I decided to just format the partition and reinstall, but it told me it had to make a swap directory, so I let it make it itself.

I managed to get in for about 30 minutes, before the screen went glitchy and now I need to install the ubuntu source or something to compile the nvidia drivers.

That's not the bad part.

The bad part:  The creation of the swap file and the new partition decided to eradicate my other logical partitions of that harddrive.  This drive included my normal Windows installation.  I'm trying to recover the data, but it's a seemingly fruitless experience.

---

### Post by greatshape on 2005-10-16
[QUOTE=Anakashar]
The bad part:  The creation of the swap file and the new partition decided to eradicate my other logical partitions of that harddrive.  This drive included my normal Windows installation.  I'm trying to recover the data, but it's a seemingly fruitless experience.[/QUOTE]

The perfect time to forget windows forever :)

---

### Post by Anakashar on 2005-10-16
I would like to, but the graphical difficulties of Kubuntu are holding me back.

I need windows for some things, though.

Just wish I knew this would happen..

---

