---
title: "All of a sudden my resolution kicked up to"
date: 2021-03-16
forum: Desktop Environments
---

### Post by garnold on 2021-03-16
I have Ubuntu 20.04 Gnome installed on my Macbook Pro with Retina screen. I'm guessing the latest update to my system installed some display drivers because now my screen resolution is 2880 x 1800. Now on a good note, the screen is crystal clear at this rez but it is way to small to work. The problem I'm having is that when I go into the display settings I only have one option for rez which is the current 2880 x 1800. When I run xrandr I get the following.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 2880 x 1800, current 2880 x 1800, maximum 2880 x 1800
default connected primary 2880x1800+0+0 0mm x 0mm
   2880x1800     91.00* 

For a video card, the machine is running
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M Mac Edition] (rev a1)

any thoughts on what I need to do to get more rez options?

Thanks you!

---

### Post by CatKiller on 2021-03-16
> **garnold said:**
> any thoughts on what I need to do to get more rez options?
You don't want more resolution options: you should run your display at its native resolution. What you want is to scale the interface elements to a more comfortable size.

---

### Post by garnold on 2021-03-16
I ended up needing to change the display driver and all is well. Just took a little time to figure it all out since I'm so new to Ubuntu.

---

### Post by remenary on 2021-11-22
Hi Garnold,

I am having the same problems as you with the resolution, can you please explain me the process of changing the display driver?

Thank you.

---

