---
title: "Gnome not obeying ACPI events?"
date: 2008-02-04
forum: Desktop Environments
---

### Post by iceparrot on 2008-02-04
I followed some advice from this, admittedly, old, thread when trying to disable the "Sleep" and "Power" buttons on a keyboard.  

[http://ubuntuforums.org/showthread.php?t=45368](http://ubuntuforums.org/showthread.php?t=45368)

I also tried following the advice of this blog post, which takes a similar approach:

[http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

It detailed how to go and change your /etc/acpi/events/powerbtn and sleepbtn files so that they don't call the powerbtn.sh or sleepbtn.sh script anymore.  However, even after doing this (and trying a reboot of both acpid and the whole box) Gnome still pops up the Power menu when I press the power button on my keyboard, and goes to sleep when I press the sleep button.

I logged into a KDE session as a sanity check and the buttons are definitely disabled there.  I'm now wondering if Gnome now handles those ACPI events in it's own configuration and thus I need to edit another set of files for Gnome, or if I'm just completely overlooking something obvious.

I'm running Ubuntu 7.10.

---

