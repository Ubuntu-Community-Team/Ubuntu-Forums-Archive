---
title: "can't select beryl window manager after updates/kiba-dock"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by ttamez on 2007-07-18
after i installed kiba-dock and did some updates, i was trying to add some icons to kiba-dock and they weren't adding right away, so i did cntl+alt+backspace and when it came back, metacity was the window manager.  now i can't select beryl as the window manager I've tried reinstalling beryl as well as the 915 drivers from synaptics but nothing.  if i try to run beryl from terminal it gives me this:

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

beryl: symbol lookup error: /usr/lib/beryl/libjpeg.so: undefined symbol: jpeg_std_error

and then my window bars disapear and i can't move windows around.  i have to fix it by running beryl-manager which starts using metacity. i'm using the 915 drivers since i'm using a laptop with the intel integrated graphics.  i don't know if it's from the updates or from kiba-dock, but what the hell is goin on?  i can post my xorg.conf if needed.

---

### Post by hyperair on 2007-07-18
Strange error you have there. Could you try reinstalling beryl-plugins?
```

sudo apt-get install --reinstall beryl-plugins

```

and after that if you still have the error, check if that file exists.

---

### Post by ttamez on 2007-07-18
i did what you suggested but it didnt fix anything, and the file is there.  i just did a rm settings in the ./beryl directory and it fixed it...but now i have to redo my settings again.  not so bad.  thanks for trying to help though.

---

