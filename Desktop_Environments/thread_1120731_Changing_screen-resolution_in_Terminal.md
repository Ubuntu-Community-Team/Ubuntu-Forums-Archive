---
title: "Changing screen-resolution in Terminal?"
date: 2009-04-09
forum: Desktop Environments
---

### Post by mathiasdk on 2009-04-09
Hi

I'm new to Linux and I accidently messed the screen-resolution up, so now I cant change it back because the screen is not "large" enough to display "apply". Pretty silly :)

Is the any way in the Terminal to change the resolution from 640x480 back to 1024x768?

Thanks and happy easter!

Mathias

---

### Post by jojo1224 on 2009-04-09
> **mathiasdk said:**
> Hi

I'm new to Linux and I accidently messed the screen-resolution up, so now I cant change it back because the screen is not "large" enough to display "apply". Pretty silly :)

Is the any way in the Terminal to change the resolution from 640x480 back to 1024x768?

Thanks and happy easter!

Mathias

I have had that happen on my netbook with xfce, the xfce font window is to big for the screen so I have to use tab to get to apply (which i cant even see). You don't need to use terminal for this. If you can make it into System>Preferences>Screen Resolution click on the Resolution drop down box and change it back to 1024x768 then hit tab 6 times and hit enter once and It should be changed back to 1024x768.

---

### Post by sisco311 on 2009-04-09
> **mathiasdk said:**
> Hi

I'm new to Linux and I accidently messed the screen-resolution up, so now I cant change it back because the screen is not "large" enough to display "apply". Pretty silly :)

Is the any way in the Terminal to change the resolution from 640x480 back to 1024x768?

Thanks and happy easter!

Mathias

Hold down the Alt key, then Left Click on the window, hold down the mouse button and drag the window. ;)

or:
```
xrandr -s 1024x768
```

---

### Post by mathiasdk on 2009-04-09
It works!

Thanks to both of you :)

Mathias

---

### Post by drummerchrissk on 2009-04-11
I would also like to thank the both of you for your quick replys. I just had to go and mess around with my settings and ended up with a screen resolution that couldn't reveal my entire window to me. But after a little searching on good ol' Ubuntu Forums, I found my answer. Thanks!

---

### Post by jmszr on 2009-04-15
sisco311,
          Thanks, I was playing Alien Arena and when I closed it the resolution was all screwy. This ```
xrandr -s 1024x768
``` fixed it. 
My lettering is small but I'll figure it out or live with it. Thanks again.

---

### Post by jonathanroz on 2009-04-21
Exact same thing happened to me.  Thanks guys I didnt think of Tab :)

---

