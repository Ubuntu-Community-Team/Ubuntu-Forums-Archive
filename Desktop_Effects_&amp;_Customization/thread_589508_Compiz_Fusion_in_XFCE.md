---
title: "Compiz Fusion in XFCE??"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by stevesutt89 on 2007-10-24
Hi!
I just recently install ubuntu gutsy with gnome.  I've now decided to switch to xfce simply by installing xfce by typing into terminal

apt-get install xfce4

Now when in xfce if it type into the terminal

compiz --replace

compiz sort of works but i lose my window borders and things like the desktop cube dont work when i enable them in compizconfig-settings-manager. Heres what the terminal outputs when i type compiz --replace 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

Also, ever since i tried this experiment (which i didn't think would work work in the first place) i now lose my window borders everytime i log into xfce so i have to type metacity --replace (yes i know that metacity is not the xfce window manager, but i can't remember what xfce's one is called) to get my borders back.  

Any ideas?

---

### Post by overdrank on 2007-10-25
> **stevesutt89 said:**
> Hi!
I just recently install ubuntu gutsy with gnome.  I've now decided to switch to xfce simply by installing xfce by typing into terminal

apt-get install xfce4

Now when in xfce if it type into the terminal

compiz --replace

compiz sort of works but i lose my window borders and things like the desktop cube dont work when i enable them in compizconfig-settings-manager. Heres what the terminal outputs when i type compiz --replace 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

Also, ever since i tried this experiment (which i didn't think would work work in the first place) i now lose my window borders everytime i log into xfce so i have to type metacity --replace (yes i know that metacity is not the xfce window manager, but i can't remember what xfce's one is called) to get my borders back.  

Any ideas?

Hi I use emerald with compiz-fusion. You can install it through synaptic and have you tried remove CSm and reinstall. Hope this helps. :KS

---

