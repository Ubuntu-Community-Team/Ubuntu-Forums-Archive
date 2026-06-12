---
title: "Need help switching from binary nvidia to proprietary"
date: 2006-08-22
forum: Desktop Environments
---

### Post by vavoem on 2006-08-22
Hi there
I'm trying to get rid of my nvidia binary driver because i want to look in to all this xgl compiz stuff.
I'm not really sure i have to but cause of all the howto's mentioning the proprietary i thought not to bother with the binary.

Now i did  
./NVIDIA-Linux-x86-1.0-8762-pkg1.run --uninstall

because it is probably a good way to get rid of the binary.
And yes it is gone

After that i did (like all the wiki's mention)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
sudo /etc/init.d/kdm restart

But X will just not start 
can somebody help me please

---

### Post by vavoem on 2006-08-22
nevermind

---

