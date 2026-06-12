---
title: "gThumb refuses to import my camera's images anymore"
date: 2007-04-06
forum: Desktop Environments
---

### Post by MysticAurora on 2007-04-06
For a while, I've been using gThumb 2.7.9 (gotten from the official Ubuntu repos) in order to get images from my Canon PowerShot A430. Everything was pretty much plug and play, when I go to import images from my camera as usual today and get this error spat at me:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Nothing has changed in my hardware setup. The transfer cable's been in the same USB slot for a while now, and I haven't upgraded much of anything; definitely not a new kernel. I'm using (X)ubuntu Edgy, for reference.

Any ideas as to what I can do?

---

### Post by yabbadabbadont on 2007-04-06
> **MysticAurora said:**
> Any ideas as to what I can do?

Yes, please search the forums.  ;)

This issue has at least a dozen threads already and most have the solution(s).

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

---

### Post by MysticAurora on 2007-04-08
I followed those bug links and their directions the best I could and still could not get either gtkam or gthumb to import my images.

Here's my camera's 'lsusb' entry:

Bus 001 Device 005: ID 04a9:30f8 Canon, Inc.

This is the line that I added to /etc/udev/rules.d/45-libgphoto2.rules and restarted after saving:

SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f8", MODE="0660", GROUP="plugdev"

Whatever program I use locks up when it tries to get images from my camera (it won't even display them) until I turn the camera off. Then it spits this at me:

```

Could not list folders in '/'.

PTP Protocol error, data expected
```

Should I consider using digikam? Since it's KDE it would use a different library, yes? I don't care what it takes to get this stuff to work as long as it works.

---

### Post by goonies on 2007-04-09
> **MysticAurora said:**
> For a while, I've been using gThumb 2.7.9 (gotten from the official Ubuntu repos) in order to get images from my Canon PowerShot A430. Everything was pretty much plug and play, when I go to import images from my camera as usual today and get this error spat at me:



Nothing has changed in my hardware setup. The transfer cable's been in the same USB slot for a while now, and I haven't upgraded much of anything; definitely not a new kernel. I'm using (X)ubuntu Edgy, for reference.

Any ideas as to what I can do?


[http://ubuntuforums.org/showthread.php?t=385505](http://ubuntuforums.org/showthread.php?t=385505)

read my thread ^^

---

### Post by DavidFourer on 2007-04-09
Did you get gThumb to download photos yet?  I found this kind of fix very perplexing when I started using linux for a home computer.  I couldn't locate files and I couldn't edit files owned by root--just that took me hours to figure out because such simple things were not in the instructions.  I'm not a programmer or IT person or anything.

Following above mentioned thread, I solved the cameral problem according to:
> Binary package hint: libgphoto2-2
The file /etc/udev/rules.d/45-libgphoto2.rules says in line 3:
BUS!="usb*", GOTO="libgphoto2_rules_end"
while recenly updated udev doesn't produce BUS properties in corresponding event. Thus this line makes the whole file useless, because BUS!="usb*" is never true.
Something like
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
instead would work.
Replace line 3 as described.

---

### Post by goonies on 2007-04-11
ive completely solved any issues with my cam by downgrading libgphoto2-2 and libgphoto2-port0, 

i can use any program to import pictures from the camera and all permissions are fine

---

### Post by Tulsapoke on 2007-04-11
I am not sure how to downgrade those.  I don't see any option for that in synaptic.  

I hope they push this out as a fix via the updates soon.  This is the type of problem that I will get complaints on from the relatives I have converted over to Ubuntu.  "Hey I cant download photos anymore!"

---

### Post by DavidTangye on 2007-04-12
i have replaced line 3 of /etc/udev/rules.d/45-libgphoto2.rules to
> SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end" as per advice on other threads. Now the error > An error occurred in the io-library ('Could not claim the USB device'):... etc does not appear, but gthumb cannot find the photos on the camera. It seems to me that libgphoto2 or whatever is still broken. I have the backport repositories on, and I think that killed the photo import (a few weeks ago). I shall wait for Feisty and hope it is fixed there. I am not impressed with this situation though.

---

### Post by RobMBaker on 2007-04-13
I replaced line 3 of /etc/udev/rules.d/45-libgphoto2.rules to read:-

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

Now my Canon Powershot A540 works fine with gThumb2.7.9 in Edgy.

Thanks for whoever put that solution up first!

---

### Post by twowheeler on 2007-04-15
> **MysticAurora said:**
> 
```

Could not list folders in '/'.

PTP Protocol error, data expected
```


I have this issue as well in Dapper, but the suggestions above do not fix it.  My udev rules file already says

> # udev rules file for libgphoto2
#
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"


I would downgrade libgphoto2-2 etc. but the old ones are  not in synaptic.  Any other ideas?

---

### Post by goonies on 2007-04-16
> **twowheeler said:**
> I have this issue as well in Dapper, but the suggestions above do not fix it.  My udev rules file already says



I would downgrade libgphoto2-2 etc. but the old ones are  not in synaptic.  Any other ideas?


im at work so cant give u detailed instructions but I did downgrade my packages through synaptic.  Look around, the option is there somewhere.

---

### Post by twowheeler on 2007-04-16
No, actually they are not, on my machine anyway.  [ Here]("http://www.pennswoods21.org/SSlibgphoto2.png") is a screenshot of synaptic open with libgphoto2-2 showing.  No other versions are shown in the properties dialog, and the Package --> Force Version choice is grayed out.  Again, this is dapper, is there something available in edgy that has not been backported?

---

### Post by goonies on 2007-04-16
[[IMG]http://alpha.zshare.net/thumb/1591005/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-png-73v.html)[[IMG]http://kappa.zshare.net/thumb/1591008/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-1-png-n0p.html)[[IMG]http://kappa.zshare.net/thumb/1591010/thumb.png[/IMG]](http://www.zshare.net/image/screenshot-2-png-x0t.html)

yeah i see, i have 2 options under mine in Edgy, my bad that i couldnt help u

---

### Post by twowheeler on 2007-04-17
Thanks anyway, goonies.

---

### Post by DavidTangye on 2007-04-18
Actually, I can now get photos via a root session, ie commandline "sudo gthumb". Then I change ownership of the imported jpgs and move them to the normal user area. Its a kludgey workaround, but it will do until I upgrade to Feisty. I do not have time to go buggering around looking for whatever hack is needed to fix it, and so for now I shall hope that the problem is fixed in Feisty.

---

### Post by yabbadabbadont on 2007-04-19
> **DavidTangye said:**
> Actually, I can now get photos via a root session, ie commandline "sudo gthumb". Then I change ownership of the imported jpgs and move them to the normal user area. Its a kludgey workaround, but it will do until I upgrade to Feisty. I do not have time to go buggering around looking for whatever hack is needed to fix it, and so for now I shall hope that the problem is fixed in Feisty.

What is returned if you run: ```
grep usb_device /etc/udev/rules.d/40-permissions.rules
```

---

### Post by twowheeler on 2007-04-20
I am temporarily working around this with the good ole' command line:

> gphoto2 -P

which works fine.  So it is not a permissions problem in my case.

---

### Post by goonies on 2007-04-20
I just did a clean install of Feisty and im glad to say my Canon SD600 just works. =)

---

### Post by DavidTangye on 2007-04-21
SUBSYSTEM=="usb_device",                MODE="0664"
Should I try 0666, or set a sticky bit or something?

---

### Post by yabbadabbadont on 2007-04-21
> **DavidTangye said:**
> SUBSYSTEM=="usb_device",                MODE="0664"
Should I try 0666, or set a sticky bit or something?

Use sudo to edit that file and change that line so that it looks like this:
```
SUBSYSTEM=="usb_device",                GROUP="plugdev", MODE="0664"
```
The first user created when you install Ubuntu is a member of the plugdev group by default so that change will give your user read/write access to all usb devices unless another udev rule specifically overrides it for a device.  I've found that this fixes a lot of usb permissions issues while still providing some security as write access is only allowed if a user is a member of plugdev.  You may need to reboot for the change to take effect.

---

### Post by HyperY2K on 2007-04-30
I've got the same error with my EOS 350D, since upgrading to feisty. In Feisty I didn't have an old version which I can force to use. Any ideas?

---

### Post by DavidTangye on 2007-05-14
I have run this command ...

rm -rf ~/.gconf/desktop/gnome/volume_manager

 and now I can get the gthumb import dialog to start. The correct camera is now automatically recognised, but it takes two attempts to see photos though.

---

### Post by HyperY2K on 2007-08-12
any updates for the issue?

---

