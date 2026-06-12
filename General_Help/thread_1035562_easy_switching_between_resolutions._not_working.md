---
title: "easy switching between resolutions. not working"
date: 2009-01-09
forum: General Help
---

### Post by anfractuosities on 2009-01-09
cannot switch resolution back manually
I am a web designer, and am trying to be able to switch between my asus z96j's 1680 x 1050 resolution and the standard 800 x 600, to test how my pages look.

Using the monitor resolution settings, I can switch to 800 x 600, but cannot switch back. I have to restart and it is restored to my default desktop res.

This is new to intrepid.

I don't know if this is pertinent, but the monitor resolution settings gui displays a box that says "unknown".

Thanks!

---

### Post by mikewhatever on 2009-01-10
I am not quite sure what you mean by 'I can not switch back'. Why not? Do you not get the desired GUI option? Do you get the option but it doesn't work?

---

### Post by anfractuosities on 2009-01-10
sorry...the option is there, I can select it in the pull down menu, but upon appling the option, it does nothing.

---

### Post by mikewhatever on 2009-01-10
Not sure why it doesn't work. Try the following command:
> xrandr -s 1680x1050

---

### Post by anfractuosities on 2009-01-10
that works but...

for some reason when I switch to 800 x 600 it changes all of my theme settings (like color and icons and such) I didn't notice until I changed the resolution back using xrandr. I don't think it is even the default ubuntu colors...the entire window is almost white...including all the title bars...

however if I change the res to 800x600 using xrandr all is fine.  I can even switch back to 1650 using the GUI resolution window...curious

---

