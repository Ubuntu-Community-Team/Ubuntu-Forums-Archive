---
title: "Video settings messed up after update"
date: 2013-08-22
forum: Desktop Environments
---

### Post by mbongiov on 2013-08-22
I have been running 12.04 for a number of years now without any issues, using the update manager whenever it showed that there were updates.  Recently, I ran update manager and it took forever to run.  It appeared to be updating/installing nvidia-304 although I already had 319 installed.  After the update, it requested a reboot, after which I was presented with a command line screen.  I have tried purging nvidia packages uusing "sudo apt-get purge nvidia*" and then rebooting.  This gives me back a graphical display, but there is no nvidia installed so I can't use nvidia-settings to change the resolution.  Every time I use some of the suggestions from this forum to re-install nvidia drivers, I end up with the text-only command line screen again.  HELP!!!

---

### Post by papibe on 2013-08-22
Hi mbongiov.

I just recover my laptop from the same situation.

These are the steps I took in text mode:
[LIST]
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Star purging the nvidia-* packages using this structure:```
sudo apt-get purge nvidia-304
```
[*]Remove all packages separately except for these two:```
nvidia-cg-toolkit
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*]At this point you can reboot, and you'll be using by default the Open Source driver (nouveau).
[*]Go to 'Additional drivers' and reinstall the recommend Nvidia driver from there.
[*]When finish, create a new X conf file:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig
```
[/LIST]
Now restart so that the Nvidia driver can take effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by mbongiov on 2013-09-06
Sorry, but that didn't help.  I just ended up re-installing Ubuntu and now all is well.

---

