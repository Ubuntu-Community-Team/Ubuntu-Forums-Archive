---
title: "No visual effects"
date: 2008-07-20
forum: Desktop Environments
---

### Post by JJR12 on 2008-07-20
I am new to all this and just trying to learn.  I did some searches and didn't come up with much, or maybe I did but didn't know it.

Anyway, I am using a Dell Smartstep 250n laptop...  Yeah I know.. older laptop, but it works like a champ with Ubuntu...  Ubuntu actually resurrected this machine from being an outdated underpowered windows machine to being a very productive up to date ubuntu machine.

Anyway back to the question...  

I am unable to enable the Visual Effects.  Is this because my video card doesn't have drivers installed??  This is where I need a little direction.

Thanks for the help in advance...

---

### Post by Tim Sharitt on 2008-07-20
Your video card may not be supported or the correct driver isn't installed. What kind of card is it?

---

### Post by JJR12 on 2008-07-21
ATI Rage Mobility - M6

---

### Post by Sef on 2008-07-21
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=764633").

---

### Post by kahlil88 on 2008-07-21
If your laptop is *too* old, you might be better off without the visual effects.

---

### Post by Melcar on 2008-07-21
The open source ati driver should support that card.  Make sure Ubuntu is loading the ati wrapper for the device.  Edit your Device section in xorg.conf to include the following:

Section "Device"
...
Driver "ati"
Option "GARTSize" "32"    #optional, but it helps when running 3D stuff
EndSection

As for Compiz itself, while how well it runs depends largely on your GPU, most of the effects are very CPU intensive, so if you have anything less than 800MHz I wouldn't bother running anything above the minimum configuration.

---

