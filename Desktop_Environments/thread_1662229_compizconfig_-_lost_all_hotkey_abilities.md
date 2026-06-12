---
title: "compizconfig - lost all hotkey abilities"
date: 2011-01-07
forum: Desktop Environments
---

### Post by Ubuntnoob13 on 2011-01-07
Big surprise, I want t desktop cube, so I followed the youtube guide [here]("http://www.youtube.com/watch?annotation_id=annotation_84304&v=Y772Zrjwgws&feature=iv"). 

When I enter simple compiz config and start to change the Ultimate profile, then I lose the ability to do key commands like alt+tab and consequently I cannot use things like the switcher, or cube.  The only desktop hotkeys that I can currently do (that I know of) is ctrl+alt+left/right to move to next desktop.  How do I enable hotkeys to work again?

Thanks in advance.

---

### Post by Krytarik on 2011-01-08
Then try to enable/configure the plugins with "CompizConfig Settings Manager".

---

### Post by Ubuntnoob13 on 2011-01-10
[FONT=Arial Black]So, it seems like the issue is that I have an ATI video card and I cannot enable Visual Effects: Custom.  When I try to enable it says, "Desktop effects could not be enabled"

Doing some research and fiddling, it seems like I'm having ATI driver issues. I am trying to completely remove the drivers, but I'm coming across the following issues:

[/FONT]                      [FONT=Arial Black]sudo apt-get remove --purge xorg-driver-fglrx fglrx* [/FONT]
 [FONT=Arial Black]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) [/FONT]
 [FONT=Arial Black]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? [/FONT]
 [FONT=Arial Black]
[/FONT] 
 [FONT=Arial Black]sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases [/FONT]
 [FONT=Arial Black]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) [/FONT]
 [FONT=Arial Black]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? [/FONT]
 [FONT=Arial Black]
[/FONT]
[FONT=Arial Black]sudo apt-get install --reinstall xserver-xorg-core[FONT=monospace]
[/FONT][/FONT][FONT=Arial Black]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/FONT]
 [FONT=Arial Black]
sudo apt-get install --reinstall xserver-xorg-core
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/FONT]
Any suggestions? Thanks in advance.
[FONT=Arial Black]
[/FONT]

---

### Post by Ubuntnoob13 on 2011-01-10
Not sure if this is worth anything either:

apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Krytarik on 2011-01-10
1.) You have to close any other package managers (like Synaptic) before you enter those commands.

2.) You have always to run them with "sudo" as prefix.

3.) Check this guide regarding your driver issue: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

