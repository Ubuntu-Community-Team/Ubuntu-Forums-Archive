---
title: "How to switch to GDM to switch user logon?"
date: 2007-11-25
forum: Desktop Environments
---

### Post by bliffle on 2007-11-25
After running this system for a month I tried to switch users (for the first time) and got this message:

"GDM (GNOME Display Manager) is not running."
"You might be using a different display manager...you will need to be configured to use GDM instead"

The screens always look like Gnome, just as on my other 3 ubuntu/gnome/gutsy systems.

I started this system as a 7.04 KDE and Xfce, but after a couple weeks decided to switch it to ubuntu/gnome, so I used 'psychocats' instructions.Worked pretty good but the system still splashed the 'kubuntu' screen at startup. Then, I upgraded to Gutsy 7.10 via internet connection. 

How can I get past this? How do I configure to run GDM?

---

### Post by PeterJS on 2007-11-25
Run this in a terminal to bring up a menu to switch login managers.

```

sudo dpkg-reconfigure gdm

```

---

### Post by bliffle on 2007-11-26
Tried that on two computers, one is awaiting a restart, the other gave me this:

```
$ sudo dpkg-reconfigure gdm
[sudo] password for john:
 * Reloading GNOME Display Manager configuration...                             
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

```

---

### Post by PeterJS on 2007-11-26
> **bliffle said:**
> Tried that on two computers, one is awaiting a restart, the other gave me this:

```
$ sudo dpkg-reconfigure gdm
[sudo] password for john:
 * Reloading GNOME Display Manager configuration...                             
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

```

That shouldn't happen, try opening up synaptic and reinstalling gdm, and then trying again, hopefully that'll fix it. If not I've got an idea of where to start looking to fix things by hand.

---

