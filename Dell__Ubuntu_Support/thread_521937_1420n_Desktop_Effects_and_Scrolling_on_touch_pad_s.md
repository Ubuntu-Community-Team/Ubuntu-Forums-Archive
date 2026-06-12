---
title: "1420n Desktop Effects and Scrolling on touch pad solution"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by phynix on 2007-08-09
**Desktop Effects**

How I got the desktop effects working, follow fd9_ 's guide

[http://ubuntuforums.org/showthread.php?t=506744]("http://ubuntuforums.org/showthread.php?t=506744")
*****Note make sure you read the post by ghindo at the bottom which goes something like this **

sudo apt-get remove xserver-xorg-video-i810

sudo apt-get install xserver-xorg-video-intel

number 6.  Had to do this because it would only boot up into command line

**Side Scrolling on Touch Pad**

Worked like a charm and now the scrolling works vertically and the horizontal in firefox works for fowards and backwards

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work")

I hope this helps. If this is wrong please tell me because it is my first try at this.

---

### Post by lynchman on 2007-08-11
Thanks for the info about the scrolling on the trackpad - it worked perfectly - and was a lot easier than the kernel patch solution that is also on here.

Thanks!

---

### Post by lynchman on 2007-08-11
Actually, I spoke too soon.  It stops working after I suspend/hibernate.  Once I restart X it is back tho...  :(  Are you seeing the same behavior?

---

### Post by lynchman on 2007-08-11
I now have it working a bit better.  I downloaded a pre-patched kernel from here:

[https://bugs.launchpad.net/redfish/+bug/129477](https://bugs.launchpad.net/redfish/+bug/129477)

And that works sometimes after resuming from suspend.  Other times not.

---

### Post by geirha on 2007-08-11
You could try blacklisting the module. The module will then be unloaded just before the suspend, and loaded when the system is resumed.

To add a module to the blacklist, edit /etc/default/acpi-support and add the module to the MODULES variable.

---

### Post by phynix on 2007-08-11
I just did that and I didn't get the effects. Sorry. The only problems I have ever had with suspend is that sound quits working but that has only happened once.

---

