---
title: "compiz disabled, theme settings crashed"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by gsb521 on 2007-12-08
Compiz fusion (the custom option in themes) has disabled, and any attempt to get back to the themes tab under appearance preferences crashes my system.  I've tried reboots, and immediately after logging in, I can get to the themes tab.  I tried changing it to custom, it then changed, but the confirmation box didn't finish loading, so it reverted after a minute.  Whenever the Appearance Preferences box is open, gnome-appearance-properties is using all of my CPU.  


I'm using a recent install of Ubuntu, I had Compiz working for a few weeks.  I have an ATI card, with the proprietary driver enabled (only suspend/hibernate didn't work).  I've tried disabling that driver, and nothing changes, except that the graphics get really slow.

---

### Post by PatrickFisher on 2007-12-08
> **gsb521 said:**
> Compiz fusion (the custom option in themes) has disabled, and any attempt to get back to the themes tab under appearance preferences crashes my system.  I've tried reboots, and immediately after logging in, I can get to the themes tab.  I tried changing it to custom, it then changed, but the confirmation box didn't finish loading, so it reverted after a minute.  Whenever the Appearance Preferences box is open, gnome-appearance-properties is using all of my CPU.  


I'm using a recent install of Ubuntu, I had Compiz working for a few weeks.  I have an ATI card, with the proprietary driver enabled (only suspend/hibernate didn't work).  I've tried disabling that driver, and nothing changes, except that the graphics get really slow.

Go to synaptic and search for "Compiz". Reinstall any packages that are already selected. If that doesn't work, make sure the required libraries are installed.

---

### Post by gsb521 on 2007-12-09
reinstalling the packages i had didn't help.  How can I check if the right libraries are installed?

Again, it's been fine for a few weeks, I don't know why it stopped working.  I don't think I changed anything...

---

### Post by gsb521 on 2007-12-09
I still don't know what the problem was, but I fixed it.  If anyone has similar problems, here's what I did.

In terminal, I did these three commands (got them from a different thread):
(Recommend you backup your Compiz preferences if you can)

sudo apt-get remove compiz compizconfig-settings-manager
sudo apt-get update
sudo apt-get install compiz compizconfig-settings-manager

Then, go to preferences under the Compiz manager, and import your settings.  For some reason, some plugins may not be enabled or others will be, but you can just manually enable/disable those.  The settings will still be saved.

---

