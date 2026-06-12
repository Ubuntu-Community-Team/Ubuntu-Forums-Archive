---
title: "Intellimouse Explorer Custom Buttons"
date: 2005-09-06
forum: Desktop Environments
---

### Post by tweak on 2005-09-06
I have already configured my intellimouse's 4th and 5th buttons to use forward and backward in firefox/nautilus, but I always preferred that they perform copy and paste functionality when I was using windows. Is this kind of functionality still a possibility or should I resign myself to forward/backward?

---

### Post by sandmanfvr on 2005-09-06
[QUOTE=tweak]I have already configured my intellimouse's 4th and 5th buttons to use forward and backward in firefox/nautilus, but I always preferred that they perform copy and paste functionality when I was using windows. Is this kind of functionality still a possibility or should I resign myself to forward/backward?[/QUOTE]
 How did you update the buttons for forward and back?

---

### Post by ad noiseam on 2005-09-07
I've set up the additional buttons of my mouse to copy and paste this way:
1. use [this wiki](https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons?highlight=%28mouse%29)

2. add this to /etc/X11/imwheel/imwheelrc:
```

".*"
None,Up,Control_L|C
None,Down,Control_L|V

```

---

### Post by tweak on 2005-09-07
Ahhh!
You're a champion and a legend!
Had to do a little ducking and diving, putting the code into ~/.imwheelrc instead, and swapping the buttons around, but it works a treat now.

Thanks :)

---

### Post by EnderTheThird on 2005-09-07
Hmm, I have my forward and back buttons working just fine in Firefox, but maybe I'll follow that so I can get them going in Nautilus too.

---

### Post by ad noiseam on 2005-10-18
I just installed Breezy from scratch, discarding everything Hoary, and I can not get this to work anymore. I did exactly the same thing (configuring Xorg.conf, Imwheel, and xmodmap), and here is what I get:

-in everything but Firefox, the side button are copy (left) and paste (right): exactly what I want
-in Firefox, these buttons are back and forward: what I do not want.

Has anybody been able to configure their mouse to have the extra button copy / paste in **Breezy**?

I am using this mouse, and the whole thing worked in Hoary.
[img]http://www.nmit.se/images/ms_trackball-opt.jpg[/img]

Nicolas

---

### Post by ad noiseam on 2005-10-18
I have been trying to solve this all day, but Breezy just doesn't play nice at all...

Actually, does anybody *really* understand how imwheel and xmodmap work? I have been changing everything a few times, and basically the functionnality never change , just the layout of the mouse. It's always scroll up / down and back / forward in Firefox, and up / down somewhere else. The copy / paste (or anything else) function don't seem to work anymore.

Can somebody explain to me what goes where in the imwheel and xmodmap files? I am trying to solve the same problem as the original poster, this time in Breezy.

---

