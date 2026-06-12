---
title: "The panel encountered a problem while loading....."
date: 2012-01-06
forum: Desktop Environments
---

### Post by ChrisOfBristol on 2012-01-06
I'm getting a regular error message when my computer starts up - about one in three starts:

[I]**Error**
The panel encountered a problem while loading "WnckletFactory::WindowListApplet".
Do you want to delete the applet from your configuration?[/I]

I can't manage without the window list, so have to restart. I'm on Ubuntu 11.10 but I'm not using Unity, I've installed gnome-session-fallback.

---

### Post by Tamlynmac on 2012-01-06
> ChrisOfBristol

I'm not using gnome 3, but I've had this problem on a few installs of earlier versions. Generally, I've been able to simply uninstall the window list applet - reboot and re-install it.

Simple enough to try and hopefully it solves the problem.

Good Luck

---

### Post by ChrisOfBristol on 2012-01-08
> **Tamlynmac said:**
> simply uninstall the window list applet
Thanks - I've removed it from the panel and replaced it - I'll wait and see what happens!

---

### Post by Tamlynmac on 2012-01-13
> ChrisOfBristol

Have you had any more problems with the windows list applet? I recently had this happen again with a friend and found that it occurred when the system was inadvertently powered down. After restart, when the error came up he chose not to delete it from their configuration and immediately rebooted.

After the system rebooted I told him to removed the applet, re-installed and re-boot. Since that time (4 days ago), the issue has not surfaced again.

---

### Post by ChrisOfBristol on 2012-01-15
> **Tamlynmac said:**
> Have you had any more problems with the windows list applet?

No - not since a week ago when I followed your advice. Note that I didn't actually un-install and re-install the software as I didn't know how to do that, all I did was to remove it from the panel and then replace it.

Anyway - it's fine so far, thanks!

---

### Post by Tamlynmac on 2012-01-15
Sounds exactly like what I've seen before. You don't need to un-install the software, just remove it - reboot and reassign the applet to the panel. That updates the Gnome configuration manager and also corrects for any issues from when the Window list applet was initially placed in the panel.

I've seen this with other applets (especially the "Trash"). Should you find a problem with any other applets, I'd try the procedure before anything else.

Good Luck and if you think the issue has been resolved, please mark this thread as solved.

---

### Post by ChrisOfBristol on 2012-01-19
It's at it again! System automatically updated 2 days ago - could it be related to that perhaps? I deleted and added it again and it was ok until.....

my weekly system update today - it's doing it again, so probably related to the update.

---

### Post by ChrisOfBristol on 2012-02-04
I've now found a way of avoiding this problem.

---

