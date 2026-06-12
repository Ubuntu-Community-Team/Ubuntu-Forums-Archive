---
title: "Feisty Fawn 7.04 - Desktop Effects Enabled, wobbly windows but no spinning cube?"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by Zegga on 2007-06-01
Howdy i finally got my nvidia drivers all working with all desktop effects working fine... but after changing the screen resolutions (1152x864) by using the command (sudo dpkg-reconfigure -phigh xserver-xorg) i no longer had window borders/the title bars vanished then i found a small solution in the forums by adding the line Option "AddARGBGLXVisuals" "True". Which made the windows wobble but now i have no spinning cube.. any help? 

If there is a better way to change screen resolutions also please let me know :)

---

### Post by snifer on 2007-06-01
This has been reported at launchpad: [https://bugs.launchpad.net/bugs/102309](https://bugs.launchpad.net/bugs/102309)

---

### Post by oneadvent on 2007-06-01
I was also baffled by this, because I could not find how to work it.

Here is what it does. (it works on my desktop)

If i take a gui app like the calculator, and I drag it over the the far left or right, like I was taking it off my screen, it moves to the next desktop, like a cube spinning.

It works fine on my laptop, which has 7.04.

---

### Post by pacman2440 on 2007-06-01
I have gotten the cube to spin by enabling it in the Beryl Manager shortcut keys, but I have not been able to get an outside view of the entire cube like you see on all the youtube videos of Beryl. I don't know if its because I am using an Intel integrated graphics card or what, but I love the rain effect!

---

### Post by sailor2001 on 2007-06-02
in windows management behavior, slide Zoom bar

---

