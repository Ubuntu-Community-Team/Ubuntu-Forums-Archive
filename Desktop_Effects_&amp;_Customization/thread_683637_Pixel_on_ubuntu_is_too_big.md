---
title: "Pixel on ubuntu is too big"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by rtsask on 2008-01-31
Hi , I installed 7.10 on my desktop and I'm using ASUS Video card based on ATI but pixel is too big on myscreen actully rverything is three times bigger than normal size, can someone please help me?

Thanks

---

### Post by Fraktyl on 2008-01-31
Did you install the ATI drivers?   Sounds like your resolution is set too low.

Either use the restricted drivers, or download Envy from here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then click System->Preferences->Screen Resolution

Make sure it's set at the resolution you want.

---

### Post by rtsask on 2008-01-31
Ok,but when I go to system/preferences/screen resolution it gives me this message: The X server does not support the XRANDR extensionn runtime resolution changes to the display size are not available. what should I do?

---

### Post by Fraktyl on 2008-01-31
Did you install the ATI drivers?  Sounds like it's stuck using the default VESA modes which are very limited.

---

### Post by rtsask on 2008-01-31
When the computer boots up some NVIDIA pages appear on screen ,I'm not sure if it os installed or not

---

### Post by Fraktyl on 2008-01-31
Do you have an ATI based card, or an Nvidia based one?

Either way, click System->Administration->Restricted Drivers Manager

Is there anything listed in the window that pops up?

---

### Post by rtsask on 2008-01-31
It says NVIDIA accelerated graphics driver(least cards)     not in use

---

### Post by Fraktyl on 2008-01-31
Ok.  That means it doesn't recognize your card as one that requires a restricted driver.

What's the ouput of this command:
```

lspci | grep VGA

```

That should say exactly what card you have.  Might as well start at the beginning, and get you set up right.  Should have done that from the beginning.  Sorry for the hoops.

---

