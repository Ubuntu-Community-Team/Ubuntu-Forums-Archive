---
title: "Repost from Mythbuntu forum - remove lock screen pw prompt on Hibernate Resume?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by mattsimis on 2009-04-25
Hi,

I need to remove lock screen on Hibernation resume.
Ive searched this all morning and found XFCE (as stock in Mythbuntu) at one point did not prompt for a password on Hibernate resume, buts its now "fixed". Problem is, I dont want the password prompt, Im installing in a Car and have an M3-ATX psu which emulates the power button press when 12v Ignition signal is cut. I have set the OS to Hibernate when power button is pressed, this bit is fine.

However on resume it prompts for a password which means I have to go rooting for the keyboard and type it in each and every time. Ive tried many, many fixes and none work.


Quite simply, how do I disable the Lock screen on Hibernate resume on Mythbuntu with **XFCE **(so gconf-edit fix doesnt apply here)?

---

### Post by BambooClaw on 2009-04-29
Install gconf-editor:
sudo apt-get install gconf-editor

Then run the editor:
gconf-editor

Use the tree view to navigate to apps->gnome-power-manager->lock.  Then remove the tick from the senarios where you do not require locking.

---

