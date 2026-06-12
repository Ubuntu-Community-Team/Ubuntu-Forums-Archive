---
title: "Ubuntu 20.04 always increase font size at reboot"
date: 2020-08-14
forum: Desktop Environments
---

### Post by nicolas-roduit on 2020-08-14
At each reboot, the text size on the toolbar and on the desktop is very large.
I can't figure out which configuration changes this. I've tried without success:
```
gsettings reset org.gnome.desktop.interface text-scaling-factor
```

If I turn on "Large Text" in Universal Access and after turn off then the text size returns to normal it works until I reboot the machine. The same when increasing the scale factor in gnome-tweaks and after setting to 1.0.

---

### Post by tongerks on 2020-08-27
up for this after an update. this was also happening to me

---

### Post by flix3 on 2020-08-29
The same is happening to me.
It started some weeks ago (before everything worked as expected).
I'm using Ubuntu 20.04, Nvidia driver version 390.138, and a Samsung SyncMaster 2333HD display.

Only switching "Large Text" on and off in "Universal Access" seems to fix the bug, but it does not persist across reboots.

In case it's relevant, this is what NVIDIA X Server Settings is detecting:
[IMG]https://user-images.githubusercontent.com/9608982/91638773-11f80800-ea12-11ea-9bbd-42e66be4769f.png[/IMG]
Not sure this is correct... it should be a 23 inches monitor, so 160x90 mm seems a bit too small to me...
...but I can't check that before (when everything worked) things were different...

Beside that, if I can fix the font size by toggling Large Text on and off in Universal Access, it should be an Ubuntu bug.

---

### Post by flix3 on 2020-08-31
According to this link:

[https://askubuntu.com/questions/1269090/ubuntu-20-04-interface-font-too-small-after-restart-even-with-high-scaling-fact](https://askubuntu.com/questions/1269090/ubuntu-20-04-interface-font-too-small-after-restart-even-with-high-scaling-fact)

it seems to be an NVIDIA driver bug, and it's affecting many users.

---

### Post by flix3 on 2020-08-31
After further reading this bug report:

[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440)

it seems that the problem is related to **libmutter,** and it affects Intel graphic cards too.

---

### Post by nicolas-roduit on 2020-09-13
Thanks you for pointing out the problem. The [workaround]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440/comments/17") works for me.

---

### Post by flix3 on 2020-09-14
For me too.
*Konrad (konradmb)'s [workaround]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1892440/comments/17"):*
> You can downgrade libmutter package temporarily as a workaround:

sudo apt install libmutter-6-0=3.36.1-3ubuntu3 gir1.2-mutter-6=3.36.1-3ubuntu3
sudo apt-mark hold libmutter-6-0

Remember to unhold after fix comes out!
I guess now we need to:
[LIST=1]
[*]Wait for somebody that tells us that the fix is ready. 
[*]Type something like: **sudo apt-mark unhold libmutter-6-0** 
[/LIST]
 I think it's going to take a lot of time... 
ATM they think the problem is: _Shell text is too small in mutter 3.36.4-0ubuntu0.20.04.2 (mostly on Nvidia)_
Anyway the "libmutter downgrade workaround" seems to work.

---

### Post by flix3 on 2020-10-11
**libmutter 3.36.3-1** is now available in Software Updater.

It solved the problem for me.

We can unhold libmutter-6-0.

---

