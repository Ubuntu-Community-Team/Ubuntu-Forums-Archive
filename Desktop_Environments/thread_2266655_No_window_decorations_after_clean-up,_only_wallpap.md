---
title: "No window decorations after clean-up, only wallpaper"
date: 2015-02-24
forum: Desktop Environments
---

### Post by pearj2 on 2015-02-24
I cleaned up my system (**10.04**), rebooted and was left with only the desktop background.. It looks like metacity, gdm and xorg are having issues.

I did three extra things I don't usually do.. Organize the 'start' menu, clear /var/logs/ and remove Urban Terror from my home folder.

Start menu:
I'm referring to the Gnome (2) start menu. I removed entries that weren't being used and moved some entries to different sections using the menu editor.

Clear /var/logs/:
Usually I only remove "rolled over" logs from here. This time I removed all. I'm used to RH environments where I normally clear all without issue (folders / files are recreated at boot, or the log isn't written). I'm not sure about Debian though.. If it can't create a log or folder, it may hose other things?

Remove Urban Terror (UrT) from home folder:
Going from memory.. I installed the UrT client years ago from the repos. A new version that wasn't in the repos came out, I installed from the UrT site (.deb). Then playdeb came out and there was a new version, so I installed it from there. I also ran a UrT server from my server. The next updated client wouldn't run on 10.04, so we stopped playing and I pulled down the game server. We'll look at it again after upgrading our hardware and installing the latest Ubuntu.

All the various UrT client installs and a backups of my modified UrT server were in my home folder. I removed them, forgetting I may of installed some of the client versions from the repos or with the package manager. This also could of hosed things.


Steps taken:
I've tried many steps found here and on askubuntu while following the errors. I've tried updating Ubuntu and booting older kernels. I've tried reinstalling UrT. I'm not used to apt-get CL, but have tried to reinstall metacity, gdm etc in hopes they'd re-create a missing file (those only tell me installed version is the latest version).

Errors:
I can't copy paste the errors because I'm using a different tty session to work from.

dpkg was throwing an error for missing UrT packages. I removed the entries, it's not erroring now. All other errors relate to the xserver, metacity and gdm...

Moving the xorg backup file to the xorg.conf file doesn't work. Generating a new xorg.conf file says "Undefined device refferenced".

The gconf-editor "fails to parse arguments cannot open display".

Restarting X says "Window manager error: Unable to open X display".

mountall: "Disconnected from Plymouth."

GTK: "Failed to initialize GLX extension. Compatible nvidia driver not found."

"HID failed to initialize for relative axis" (mouse) but later uses absolute axis.


What to do?
I'm assuming the issue is caused from something I did while cleaning out the computer.. In other words, I don't think it's a bad nvidia driver as I didn't mess with it and it worked fine before. I don't think it's suddenly my Ubuntu version, hardware etc. It has to be something I did while cleaning up, the next boot is when the issue started.

My hunch is that at boot, the chain of xorg / gdm / metacity isn't starting because it can't write to /var/log/. Or, dpkg is misconfigured and it doesn't get to starting the chain of xorg / gdm / metacity.

Could apparmor keep programs from writing to var/log? How can I search for anything UrT related within Ubuntu's package manager via CL? Those may not be the issue. It may be a misconfigured file due to xorg / gdm / metacity not responding?

Any help is greatly appreciated - thank you in advance!

---

### Post by deadflowr on 2015-02-24
Ubuntu Desktop 10.04 has hit end of life.
(Ubuntu Server 10.04 is still supported, for now --only a few months left)

[We highly recommend updating to a supported desktop release]("http://ubuntuforums.org/showthread.php?t=2229730")

---

### Post by pearj2 on 2015-02-24
Thank you for responding. I'm aware 10.04 isn't supported by Canonical.

From the OP: "I don't think it's suddenly my Ubuntu version". I'm specifically wanting to solve the issue created by me cleaning up, not upgrade.

However... If it helps, let's say I run the latest Ubuntu version, and always have Unity and Gnome3 disabled. I use Gnome2 instead. Switching to Gnome3 / Unity won't help because the xorg server doesn't start..

What to do? I made a change, it stopped working, how do I undo it?

---

