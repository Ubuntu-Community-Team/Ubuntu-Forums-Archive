---
title: "Beryl XGL removal.. not going well"
date: 2006-11-24
forum: Desktop Environments
---

### Post by Lem on 2006-11-24
I'm running Edgy with the latest Nvidia drivers from the Amaranth repos.
Been running Beryl/Xgl with no problems. However, I wanted to remove the XGL to enable mythtv etc to run correctly.

So, I removed xgl-server, commented out the XGL bits in /etc/gdm/gdm.conf-custom and edited my xorg.conf to look like this;
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "true"
# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Acer AL1916W"
    DefaultDepth    24
    Option         "UseFBDev" "true"

#Option "DisableGLXRootClipping" "True"
```

Beryl manager starts up ok, says Nvidia is present, and then everything goes a bit..er.. black. Any open windows go very dark on the interior, and things run very slowly. One of the panels usually goes black. I can usually hunt around in the black for the beryl icon and switch to metacity and normality returns.

I love to have Beryl back without the XGL issues. GLX is enabled, my xorg.0.log doesn't have any nasties in it, and i get 1200fps in glxgears with my onboard nvidia 6150.

Everything looks ok, but I've obviously missed something here.

---

### Post by Lem on 2006-11-24
I tried going back to XGL in the meantime and that just goes reeeeeaaallly slow, despite working fine before. I've reinstalled nvidia-glx, beryl and emerald.. and tried going minus xgl and am now back where I started.

Ever wished you'd not started fiddling with something?

---

### Post by stupidkid on 2006-11-24
Don't you need 

Section "Extensions"
        Option "Composite" "Enable"
EndSection

in your xorg.conf for beryl to work?

---

### Post by Lem on 2006-11-24
From what I understand that's no longer needed. I might try it though.

---

### Post by Lem on 2006-11-27
Nope- that didn't help!..

Weird.

---

