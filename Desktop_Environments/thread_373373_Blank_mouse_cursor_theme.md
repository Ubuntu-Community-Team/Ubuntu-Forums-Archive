---
title: "Blank mouse cursor theme?"
date: 2007-03-01
forum: Desktop Environments
---

### Post by shewf on 2007-03-01
I'm running Ubuntu 6.10 as a kiosk with a touchscreen and I'd like to be able to hide the mouse cursor in Gnome. Firefox launches in full fullscreen and users can press the hyperlinks on the screen to navigate.

Could anyone point me in the direction of a "blank" cursor theme that would not show the little hand/pointer? Failing that, how would I create a blank cursor (doesn't sound like this is in the gtkrc file)

Thanks,

Mark

---

### Post by mdgjim on 2007-03-02
> **shewf said:**
> I'm running Ubuntu 6.10 as a kiosk with a touchscreen and I'd like to be able to hide the mouse cursor in Gnome. Firefox launches in full fullscreen and users can press the hyperlinks on the screen to navigate.

Could anyone point me in the direction of a "blank" cursor theme that would not show the little hand/pointer? Failing that, how would I create a blank cursor (doesn't sound like this is in the gtkrc file)

Thanks,

Mark

You could try adding style rules to the profiles  /chrome/userChrome.css and /chrome/userContent.css like this:
* {
    cursor: url:/url.to.a blank cursor image; 
}

The other way (that I use) is to patch firefox to add a new cursor that is all blank

You will also need to make a blank cursor for X and use 'xsetroot -cursor pathToCusor.bmp pathToCursor.bmp
the second pathToCursor.bmp is for the cursor mask. You can use the bitmap program to make the cursor.bmp and do not forget to add a hotspot to the bmp.

---

