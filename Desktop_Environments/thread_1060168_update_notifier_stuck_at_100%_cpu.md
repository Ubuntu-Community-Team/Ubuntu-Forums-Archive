---
title: "update notifier stuck at 100% cpu"
date: 2009-02-04
forum: Desktop Environments
---

### Post by bailout on 2009-02-04
I have xubuntu installed on my laptop and find that after it has been on for a while the fan will start and stay on high. When I run top in the terminal the update-notifier process is running at 100% cpu. 

Had a searh here and on launchpad but couldn't find anything. Any ideas how to fix?

---

### Post by Hooya on 2009-02-04
First thought it to turn off the update-notifier service.  Not sure how to do this exactly, maybe you can remove it with no ill effects.  Whenever you want to update, just do this in a terminal:

sudo apt-get update && sudo apt-get upgrade

That will update all your currently installed packages.

---

### Post by BrownieBoy on 2009-04-29
> **bailout said:**
> I have xubuntu installed on my laptop and find that after it has been on for a while the fan will start and stay on high. When I run top in the terminal the update-notifier process is running at 100% cpu.

I'm seeing the same thing with Jaunty Xubuntu on my EEE PC 701.  I've now disabled Update Notifier via the Settings->Session and Startup menu.  It's under the Application Autostart tab on the dialog.  Just untick it.  I also turned of the Bluetooth Manager there, since I don't have it on this PC.

Anybody know what the underlying problem might be?

---

### Post by turutosiya on 2009-05-07
i got same problem. Jaunty Xubuntu on ThinkPad T41.

---

### Post by tlinsenm on 2010-07-21
The problem persists in Lucid (on a Portégé R200), too. Does really nobody have an idea what the underlying problem is?!

---

