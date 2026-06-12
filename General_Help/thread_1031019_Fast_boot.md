---
title: "Fast boot?"
date: 2009-01-04
forum: General Help
---

### Post by slughappy1 on 2009-01-04
Hello, I currently use a dual boot ( Ubuntu and Vista ), but I am looking for one thing. I want to add a third that will be pretty much just for internet usage. I want the third to boot fast and be able to use my hardware easily. Any thoughts? Maybe have it installed on the hdd, but load itself into RAM when booting to be fast? Any thoughts?

---

### Post by Bucky Ball on 2009-01-04
The involved way would be to build a kernel with the necessary drivers for the monitor, keyboard, mouse, card and comp and an app or two for your internet requirements.
A desktop manager like Openbox or Fluxbox could also be the go for this setup up as they are extremely lightweight (and you could probably find lighter if you dug more).

The less involved way (which could, of course, become fairly involved!) is to see if you can tweak something like Puppy Linux or Damn Small Linux to do what you require.

---

### Post by slughappy1 on 2009-01-05
Alright, any place in particular that would be a good base for me to start at?

---

### Post by Bucky Ball on 2009-01-05
[http://avinesh.googlepages.com/howtobuildcustomkernelonubuntu](http://avinesh.googlepages.com/howtobuildcustomkernelonubuntu)

[https://wiki.ubuntu.com/ZenKernel#Introduction](https://wiki.ubuntu.com/ZenKernel#Introduction)

There's a start. Have a good look around for 'custom kernel linux' and see what you can dig up. The main thing is, you are going for an absolute minimum and building up from there. There is Ubuntu Mini, but I couldn't get that working and is still probably too bloated for what you want.

There is another piece of software that lets you trim the fat whilst running Ubuntu (ie every driver for every piece of compliant hardware etc seems to be in the kernel - who needs intel stuff if you are running amd and vice versa). I am on the wrong computer and can't remember what it's called. It runs from the terminal if that gives you a clue for finding it. I'll have a look later.

---

