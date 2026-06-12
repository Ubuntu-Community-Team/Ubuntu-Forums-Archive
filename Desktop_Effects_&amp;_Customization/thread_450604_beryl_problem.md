---
title: "beryl problem"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by em11488 on 2007-05-21
whenever I open beryl all my windows lose the upper banner that has the minimize, maximize and exit buttons. since it doesnt have this outline or whatever you call it, I cant easily move windows and instead have to press a button in order to initiate it, rather than hold click and move. this is really annoying, please help. I would thnk the problem is in the beryl settings manager under window management and further under set window attribs by various critieria. I dont know what to do bc i am a complete /\/00/3 at linux, just started. please help!

---

### Post by Ateo on 2007-05-21
Sounds like your window decorator isn't on. Try the following:
```
$ emerald --replace&
``` from terminal.

---

### Post by dannyboy79 on 2007-05-21
this is listed in many FAQ and beryl troubleshooting. you realy should use gogle before posting. after a 10 second gogle search, here is the solution: [http://ubuntuforums.org/showthread.php?t=358318](http://ubuntuforums.org/showthread.php?t=358318)

---

### Post by Kobalt on 2007-05-21
You must be missingg the ArgbGLX option in your xorg.conf. Run this to fix it : ```
nvidia-xconfig -add-argb-glx-visuals
```
Restart X with Ctrl+Alt+Backspace and you should be done.

---

### Post by em11488 on 2007-05-21
whenever I open the terminal with beryl being the window manager its all white, i cant see anything.

---

### Post by compmodder26 on 2007-05-21
Okay, so disable beryl as the window manager and then use the terminal.  After making the changes, re-enable beryl as your window manager.

---

### Post by em11488 on 2007-05-21
kobalt, when i did your code i got 

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".

ERROR: Unable to write to directory '/etc/X11'.


compmodder when I did yours, it just closes right after I hit enter

---

### Post by skyhopper88 on 2007-05-21
This will probably get moved as beryl isn't considered beginner talk, but here's the fix from the beryl faq.
" My windows don't have any decorations (title bar, resize handles, minimize/maximize/close buttons)

Before try this, make sure that you have the window decoration enabled at your beryl-manager's settings. It can be the problem.

You can try these solutions by modifying sections of /etc/X11/xorg.conf :
(type gksudo gedit  /etc/X11/xorg.conf then enter your password)

1. Try changing DefaultDepth to 24 in the ' Screen ' section if it's not.

2. Delete or comment out with a #, if existing, these entries in ' Section "Module" ' :

 Load "dri"
 Load "GLCore"

3. Add this entry in ' Section "Module" ' if not present :

 Load "glx"

4. Change in Section "Device" the ' Driver "nv" ' entry to :

 Driver "nvidia"

if it's not already (assuming you have an nvidia card)
5. Add this entry in ' Section "Screen" ' :

 Option "AddARGBGLXVisuals" "True"
(this will probably be what fixes it)
6. Add this section at the end of the file if not present:

 Section "Extensions"
     Option "Composite" "Enable""

After that close everything on your desktop and save and hit control alt backspace (not delete) to restart X and try berl again.

---

### Post by em11488 on 2007-05-21
where is window decorator in the manager settings

---

### Post by compmodder26 on 2007-05-21
If you right click on the beryl icon in your taskbar, you should have options for the window decorator and window manager

---

### Post by em11488 on 2007-05-21
how can i enable it when it only gives me the option of reload window decorator, which does nothing, or select window decorator, and switching does nothing.

---

