---
title: "[SOLVED] old school rxvt - don't want window borders"
date: 2008-12-12
forum: General Help
---

### Post by gnu2tux on 2008-12-12
Hi,


 Waay back when most people in these forums were in their diapers, I used to hack up fvwm scripts and mess with things that people have forgotten about like .Xdefaults files and the such. Anyhoo, I need to go back to a time of old when things were that little bit harder... just because they were..

I used to remember having to hack up some file to change the way that rxvt (my terminal of choice) behaved in certain circumstances. In this case, I want my rxvt (but I guess can be gnome-terminal or xterm if must be) to have no window decorations.

Anyway, my brain is an old, rusty and I forget completely how to do such a thing. If you remember how to do it, please let me know so I can live in xterm peace again.

Oh, btw, my wm is pwm if that makes any difference. Ubuntu 8.10.

TIA.

---

### Post by tdrusk on 2008-12-12
> **gnu2tux said:**
> Hi,


 Waay back when most people in these forums were in their diapers, I used to hack up fvwm scripts and mess with things that people have forgotten about like .Xdefaults files and the such. Anyhoo, I need to go back to a time of old when things were that little bit harder... just because they were..

I used to remember having to hack up some file to change the way that rxvt (my terminal of choice) behaved in certain circumstances. In this case, I want my rxvt (but I guess can be gnome-terminal or xterm if must be) to have no window decorations.

Anyway, my brain is an old, rusty and I forget completely how to do such a thing. If you remember how to do it, please let me know so I can live in xterm peace again.

Oh, btw, my wm is pwm if that makes any difference. Ubuntu 8.10.

TIA.

[This]("http://bbs.archlinux.org/viewtopic.php?pid=133122#p133122") might help.

---

### Post by steveneddy on 2008-12-13
I believe that you can launch xterm without window borders or decorations.

You will just have to play around with the placement on your desktop because the default will put it under the top Gnome task bar.

I've done this in the past and it really is cool looking, especially if you make it transparent and slightly grey it looks like it is floating on your desktop.

---

### Post by jpkotta on 2008-12-13
Or you could install Fvwm.
```
Style rxvt !Title, !Borders
```

---

### Post by gnu2tux on 2008-12-15
Thanks to all.

In the end, it wasn't a change to .Xdefaults as I was guessing, it was infact a tweak to the window manager config file that sorted it. As I am using PWM (I'm sure a lot of you haven't even heard of PWM), it was the first ever tabbed window manager. It's still pretty good today.

Anyway, enough rubbish, this is how it's done in case anyone cares:

winprop "XTerm.*" {
        wildmode yes
}

that goes in /usr/local/etc/pwm/pwm.conf on a Debian/Ubuntu system or in your own ~/.pwm config file

Tata,

gnu2tux

---

