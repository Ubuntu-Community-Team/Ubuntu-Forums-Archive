---
title: "logitech g5 g5_hiddev?"
date: 2007-10-11
forum: Gaming &amp; Leisure
---

### Post by ykram on 2007-10-11
I just got a Logitech G5 to replace my Logitech MX518 and have my key maps working, all except the DPI on the fly ones. Looking online for a solution, it appears as though lomoco can't do G5 yet, although a hack exists called g5_hiddev.c. Sadly, it relies on /dev/usb/hiddev0, where as I'm missing /dev/usb/ altogether on Dapper 6.06.1. Any ideas?

---

### Post by Naegling23 on 2007-10-11
the g5 dpi adjustment is done on the mouse itself, meaning that you dont control it through the software.  On windows, you can edit the settings to custom dpi's but Im not sure if there is a similar thing for linux.  What I did was set my mouse curser speed to a comfortable setting under the medium dpi setting.  When I game, I go the the lower dpi, and in gimp, the higher one.  

You should be able to shuffle through the three setting on the mouse, customizing them is a different story.

---

### Post by ykram on 2007-10-11
That's what I thought as well, that the 3 default DPI's, 400, 800 and 2000 are stored automatically in the mouse, and switching through them is trivial as you just hit the sensitivity buttons. What I can't figure out is why my DPI doesn't change when I hit my sensitivity buttons, the + or the - both do nothing and I'm stuck in 2000 DPI. Oddly, when I boot up at first, it starts at 800 DPI, and trying to lower it doesn't work, but raising it to 2000 works fine, I just can't switch back. I'm losing my mind here :(

---

### Post by Bokonon on 2007-10-12
Hmm, the button works for me on lappy and desktop.

I have G5 (rev1), G5 (rev2) and G7.  All 3 allow you to adjust on the fly, but boot to the middle setting each time.

---

