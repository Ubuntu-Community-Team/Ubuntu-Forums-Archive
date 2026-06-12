---
title: "FYI Compiz Fusion with NVIDIA Cards"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by sparks0548 on 2007-07-30
I found some pretty good information on the Comiz site at the following address, which helped me my problems with getting Fusion up and running.  If this is duplicative I apologize, just want to share the wealth:

[http://www.compiz.org/How_to_compile_and_run_Compiz_for_nvidia_card_users](http://www.compiz.org/How_to_compile_and_run_Compiz_for_nvidia_card_users)

The sections that helped were these:

sudo nvidia-xconfig --composite
sudo nvidia-xconfig --render-accel
sudo nvidia-xconfig --allow-glx-with-composite
sudo nvidia-xconfig --add-argb-glx-visuals

and adding these lines to the device section of the Xorg.conf:

Option         "RenderAccel" "true"
Option         "AllowGLXWithComposite" "true"


Then I added the following lines in the screen section just after Default Depth:

Option         "AddARGBGLXVisuals" "true"
Option         "DisableGLXRootClipping" "true"

Saved the file and CTRL+ALT+Backspace and everything loaded and worked fine.

Hope this works for you

---

### Post by sparks0548 on 2007-07-30
Oh I forgot to add I set the Default Depth to 24 vs. 16 in the XORG.CONF.

That's what I get for posting to quickly....LOL

---

### Post by dreadlord_chris on 2007-07-30
Just so you know:
sudo nvidia-xconfig --render-accel == Option "RenderAccel" "true"
sudo nvidia-xconfig --allow-glx-with-composite == Option "AllowGLXWithComposite" "true"
sudo nvidia-xconfig --add-argb-glx-visuals == Option "AddARGBGLXVisuals" "true"

The nvidia-xconfig command just automates the addition of those options to xorg.conf

---

