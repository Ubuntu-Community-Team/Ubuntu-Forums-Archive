---
title: "urban terror 100% cpu usage"
date: 2009-08-18
forum: Gaming &amp; Leisure
---

### Post by shrndegruv on 2009-08-18
hi all

i got urban terror running, but it always runs with 100% cpu on both cores.  is there a way to get it to not do that?  I get ~90fps, seems like the cpu is working unnecessarily hard...

---

### Post by rhchia on 2009-08-18
yupz... same here... 
another problem i faced is often the full screen window will turn windowed and i couldn't control my mouse. solution to this is i need to on and off my mouse touch pad on my laptop.
i believe i have quite a reasonable system - C2D 2.4ghz with 3gb ram

---

### Post by doorknob60 on 2009-08-19
taskset -c 0 urban-terror

Replace urban-terror with whatever the command to start the game is (I don't remember, and too lazy to check). This will set it to only use your first core. You can use 1 instead of 0 to use your second core.

---

### Post by tatrefthekiller on 2009-08-19
Games usually use 100% CPU to get as much FPSs as possible. This is not a problem, your CPU is made to support it !

---

### Post by SigmaSanti on 2009-08-19
You can use the taskset +
Urban Terror has a frame rate (fps) limit option in the settings menu you can set to 60fps or less

You can try enabling vertical sync in the nvidia-settings menu if you have an nvidia graphics card, I dont know how to do this with intel or ati.
Urban Terror also has a vertical sync option which forces the framerate to be 60 fps (I think)

The above options I listed (except taskset) may not help since its mostly graphics card related, but disabling compiz will definatly lower cpu usage too, just run "metacity --replace" before the game, and "compiz --replace" after to get desktop effects back. 

If you dont understand these options search them on google "fps", "vertical sync", "metacity and compiz".

Somewhere in the forums is a script that you can run with any program that will automatically disable compiz for you.

I had this problem for a while, and use all of these fixex/options to get 1 of my AMD 2.8 ghz cpus at full usage and 60 fps normally.

I had to do this because my cpu fan is a little to weak for the cpu I purchased (my bad) and as a result it runs too hot at max load.

rhchia, I had a similar problem with it going into windowed randomly, the metacity --replace before running a game fixed this.

---

### Post by Dark Aspect on 2009-08-19
> **tatrefthekiller said:**
> Games usually use 100% CPU to get as much FPSs as possible. This is not a problem, your CPU is made to support it !

+1

Even some older games take 100% of my CPU.

---

