---
title: "ET running slow on ubuntu"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by retaliator666 on 2007-05-15
My ET runs very slow on ubuntu (I can compare it to my ET on windows, which runs fast!)
I have an nvidia 6600GT 256MB, pentium 4 640 (3.2Ghz), 2048 ram
when I check the console, the nvidia is used for rendering etc. I also have installed the nvidia drivers in feisty.
What else can be the problem?

---

### Post by mbradlcu on 2007-05-18
ET runs well on my old craptop so it should be running well on your system. what numbers do you get if you run glxgears, here's my output: 6141 frames in 5.0 seconds = 1228.043 FPS
you're should be much higher,, 
turn off or disable any compiz or beryl if you're running it, and also check glxinfo to make sure direct rendering is a "yes"
 daturan@cpr3:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

let me know you're findings,
back in the day I ran q3 on windows and the performance on linux was actually a little higher, I believe ET is a q3 based games so the #s should be comparable.

---

### Post by asipi on 2007-05-19
aggree, I have 10-20 fps more under linux

---

