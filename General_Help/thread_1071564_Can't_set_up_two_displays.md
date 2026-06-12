---
title: "Can't set up two displays"
date: 2009-02-16
forum: General Help
---

### Post by Zalbor on 2009-02-16
Hello everyone, I'll try to describe my problem as best as possible.

My video card is an nvidia geforce 5700 LE. It has 3 outputs: VGA, DVI and S-VIDEO.
Up until now I was using only one display, connected to the DVI output. Today I connected a new one (an LCD tv) to the VGA output. Since then, Ubuntu only displays on the TV and has a very low resolution.
I try to use nvidia-settings and this is what I saw:
1)The utility recognizes the old monitor as it should (its full model name appears in the list) but the TV as a CRT display.
2)I can't change the TV's display to anything bigger than 640x480 (in windows it can use the video card's highest resolution: 1768x992).
3)Originally, the TV was enabled and the old monitor disabled. I was able to change these settings, but after restarting X it's back to how it was before.
4)I tried to boot in recovery mode and choose "xfix"; this made the old monitor display correctly and the TV to show random colours and characters, but it replaced the nvidia driver with VESA. Changing it back to nvidia created the same problems as before.

The drivers I have installed are 173.something, installed with envyNG. It also has the option to use 177.something, but it caused some problems when I tried it (back when I had one monitor).

Using both displays isn't important to me (while it would be good to have) but what I do need is a way to display on my normal monitor without the TV showing anything and without having to disconnect the cable to do so.

Thank you.

---

### Post by bodhi.zazen on 2009-02-16
Try running nvidia-settings :

```
gksu nvidia-settings
```

---

### Post by Zalbor on 2009-02-17
I did that, it had the same effect whether I used root permissions or not.

---

### Post by Zalbor on 2009-02-17
I sort of came past the first problem. I thought I had clicked on "Save to the X configuration file" but I guess not.

Things aren't fine however. I enabled Xinerama and both screens worked, but the TV still had a very low resolution and compositing was disabled. Disabling Xinerama has re-enabled compositing but now the TV shows nothing (except the X cursor if I move the mouse to it).

At least now I can work on my normal monitor, but still: Does anyone know how to make both work, make compositing work at the same time, and have the TV use a high resolution?

---

