---
title: "Jaunty Fonts"
date: 2009-04-24
forum: General Help
---

### Post by change_mode on 2009-04-24
nevermind, seems that the update just messed up all my settings... this can be deleted.

---

### Post by GeekLove_JavaStyle on 2009-04-24
ditto.  I'm having issues as well.  Exact same scenario.

---

### Post by manuelb on 2009-04-24
You can follow the simple directions at [http://sharpfonts.com/]("http://sharpfonts.com/") and you'll have sharp fonts in minutes!

---

### Post by GeekLove_JavaStyle on 2009-04-24
Since change_mode removed the description...

I was running Intrepid Ibex...everything was displaying perfectly.  I was using the default settings.

Upgraded to Jaunty, now Firefox fonts look horrible on many pages.  They're definitely much smaller.  

What changed between versions?

I looked in appearance, but didn't notice the difference yet. I already changed the font size for "application" and "document"  and rendering settings (to "Best Contrast").  

Which font setting changes the rendering of HTML in webpages on firefox?

Thanks in advance,
Steven

---

### Post by manuelb on 2009-04-24
You may want to try this:

```

sudo fc-cache -f -v

```

then logout/login or reboot the machine.

---

### Post by cariboo on 2009-04-24
There are changes in Xorg-xserver that try to detect your monitor and set the best dpi for fonts.

Rick-click on the desktop and select Change Desktop Baground, then click the fonts tab, next click the details button and check the resolution, mine is set for 96 dpi

---

