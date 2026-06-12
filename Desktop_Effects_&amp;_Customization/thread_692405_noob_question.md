---
title: "noob question"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by aalr1986 on 2008-02-09
ok, so I have 2 small problems:

1) when I open a window, the default is that it appears on the top of the screen...... how do I make it appear on the center?!?!?

2) I can't see my title bar when desktop effects are enabled, it's like invisible... and plus, when I double clic on it, it doesn't maximize/restore, but it all shrinks and I can just see the "invisible" title bar, and I don't want this to happen....

which of the effects do I have to tweak with, or disable in order to fix this?!?!?

thanks!!! :)

---

### Post by overdrank on 2008-02-09
> **aalr1986 said:**
> ok, so I have 2 small problems:

1) when I open a window, the default is that it appears on the top of the screen...... how do I make it appear on the center?!?!?

2) I can't see my title bar when desktop effects are enabled, it's like invisible... and plus, when I double clic on it, it doesn't maximize/restore, but it all shrinks and I can just see the "invisible" title bar, and I don't want this to happen....

which of the effects do I have to tweak with, or disable in order to fix this?!?!?

thanks!!! :)

Hi and for the first question you can go to compizconfig settings manager located under system, preference, and if you are using gutsy then it is advance desktop settings. Then window management, place windows. There you can check the box and set your windows. 
   The second question, you may look for the window decoration in CCSM also. What is the model of your graphics card?

---

### Post by aalr1986 on 2008-02-09
I have an NVidia GeForce 8600GT 256mb..

now my titlebar dissapeared...... lol what do I do now?!??!?!

---

### Post by overdrank on 2008-02-09
> **aalr1986 said:**
> I have an NVidia GeForce 8600GT 256mb..

now my titlebar dissapeared...... lol what do I do now?!??!?!

Ok did you check the window decoration in the advance desktop effects settings? You may check your xorg to see if you need to add these to your xorg. Use the command ```
gksudo gedit /etc/X11/xorg.conf
``` 
You may add these two lines
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Here is a example 
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

Then save the file and restart x with the ctrl, alt, backspace keys at the same time.

---

