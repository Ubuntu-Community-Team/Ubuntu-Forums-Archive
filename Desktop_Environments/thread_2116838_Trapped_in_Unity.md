---
title: "Trapped in Unity"
date: 2013-02-16
forum: Desktop Environments
---

### Post by n4pgw on 2013-02-16
I installed 12.04 and when I would boot, it would stop and ask for a password.

I then installed Gnome fallback.  It boots to the password prompt so i can choose what GUI to use.  

Then I installed Virtualbox from the software options and wound up with a problem.

In Gnome, when I would start VB, it would immediately log me out and drop me back to the password entry.  

I tried uninstalling and reinstalling from Synaptics.  No change.

I tried logging into unity.   In unity, when I would click on the dash, I would be returned to the log-in screen.  

After reporting this to the VB forum, I was informed that my ubuntu installs of VB were edited so they would not support so I installed the Debian version from their website.

This fixed the logout problem, only maybe too well.

It worked in Gnome.  So just to check it out, I logged into unity.  After working here in Unity a while, I decided to drop back to Gnome again, where I can find my way around.

My problem is that I can shut down or reboot, but it ignores my logout or switch user account.  

Now, when I boot, it automatically executes Unity without my logging in!  I don't remember telling it to autolog me in.  

I guess I need to find where to turn off autologin and how to go back to gnome.

---

### Post by n4pgw on 2013-02-17
Solved: 

One of my problems is that I have a card with three monitor outputs.  The VGA is connected to my Vizio TV, which is normally off or looking at my BluRay player HDMI output.  The DVI is connected to my Compaq monitor, which I use for my primary computer video, and the HDMI output is not used at all at this time.

When using 10.04 I was able to default the boot to use only the Compaq monitor and when I desired to use the Vizio as a monitor, I would set Nvidia X Server Settings to use the second monitor.

However, 12.04 always defaults to using both monitors, even if the Vizio is off or watching the HDMI input.  So I end up with a hidden window. 

I switched to Gnome and my HPLIP software is looking for a system tray which does not exist, therefore, after about 45 seconds of boot, it pops up a dialog box in the hidden window that cannot be seen.  It allows me to do most tasks in Unity or Gnome, but it will not allow me to log out without being closed first.

This is probably a very unique problem since it is probably extremely rare that someone with multiple monitors would want to default their boot to only one.  However, I hope this thread helps that one other person out there who does this also.

---

