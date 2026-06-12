---
title: "Issue with Beryl(fairly new)"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by Tanikaze on 2007-07-05
Hi,

I am currently using Ubuntu version Feisty Fawn(7.04). My video card is an nVidia GeForce 7600GT, running the drivers from nVidia's website. I attempted to install beryl using these instructions:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Ubuntu)

Everything appeared to go fine. I restarted X, logged in, and I have the neat little red gem in the top right. I can click on it and get a drop-down menu. However, when I go to Select Window Manager and select Beryl, my windows flash for a few seconds, then I am sent back to Metacity.

Does anyone know what might be happening?

Quick edit:

Additionally, when I go to System->Preferences->Desktop Effects, a window pops up which says, verbatim:
"The Composite extension is not available"

I think this may be a clue as to what is going on.

---

### Post by Waappu on 2007-07-05
You can try these solutions by modifying sections of /etc/X11/xorg.conf :


1. Try changing DefaultDepth to 24 in the ' Screen ' section.

2. Delete, if existing, these entries in ' Section "Module" ' :

 Load "dri"
 Load "GLCore"

3. Add this entry in ' Section "Module" ' :

 Load "glx"

4. Change in Section "Device" the ' Driver "nv" ' entry to :

 Driver "nvidia"

5. Add this entry in ' Section "Screen" ' :

 Option "AddARGBGLXVisuals" "True"

6. Add this section at the end of the file:

 Section "Extensions"
     Option "Composite" "Enable"
 EndSection

---

### Post by Tanikaze on 2007-07-05
Thank you, the last suggestion fixed it.

---

