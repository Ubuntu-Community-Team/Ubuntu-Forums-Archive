---
title: "Heretic 2"
date: 2008-04-28
forum: Game Specific Discussions
---

### Post by Knight on 2008-04-28
I'm not sure how I was able to install this in the past, and don't know why now suddenly I'm having problems, but it's like this. The install from CD goes without problems, but I need to get patched up to get back to multiplayer blading. The first step in patching was to

```
./heretic2-1.06b-unified-x86.run --keep
```

But right away it gives

```
Creating directory heretic2-1.06b-unified-x86
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 2317627392 4281850751
```

So can't even make it past the first step, how frustrating! Anyone know whats going on and how to work around it?

---

### Post by eragon100 on 2008-04-29
I just got this game in the mail from tuxgames. I have exactly the same problem.

I can't play without the updates, because it gives this error:

========================== Heretic II ===========================

Added packfile /usr/local/games/heretic2/base/htic2-0.pak (4347 files)
Executing global default.cfg
Executing /home/eragon/.loki/heretic2/config.cfg
NET Initialized
Loaded DLL /usr/local/games/heretic2/base/client_effects.so as 0x8a277c8
Setting default sound support "snd_sdl.so"
Loaded DLL /usr/local/games/heretic2/snd_sdl.so as 0x8a27c08
Console initialized.
VID: initial refresh soft
Loading /usr/local/games/heretic2/ref_soft.so 
Loaded DLL /usr/local/games/heretic2/ref_soft.so as 0x8a2ab20
Initializing VID module
Initialize software renderer
Setting mode x11 for device mouse
Initialized 648x480 16bit display
Shutting down sound.
Shutting down input handling
Shutting down sound.
Warning: currently only R5G6B5 mode supported

Exiting Heretic II...
recursive shutdown
eragon@Asgard:/usr/local/games/heretic2$ 

What is R5G6B5 mode and how on earth do I switch to it!?

How do I update it or get it to run without updates? HELP :(

---

### Post by Knight on 2008-04-29
> Warning: currently only R5G6B5 mode supported

Yeah I got this when trying to load it up too (unpatched). Still have not figured out a way to get the dang patches put on, but nice to know I'm not the only one trying to get Heretic 2 working again.

---

### Post by eragon100 on 2008-04-30
Solution:

Create a virtual machine woth virtualbox with ubuntu on it.

Modify /etc/X11/xorg.conf to a default bitdepth of 16 bit

install and play from inside the virtual machine. Any idea how I mke the keyboard behave nortmally though? It's very playable, but the keyboard is a little annoying :(

---

### Post by eragon100 on 2008-04-30
I have solved the keyboard problem !!!!!

Simply go to system -> preferences -> keyboard and disable "key presses repeat blah blah blah" in BOTH the real and the virtual ubuntu. Then select resolution 1024 X 768 in both the real and the virtual ubuntu, and set virtualbox to full-screen mode. Now the virtual ubuntu is fullscreen :)

Then select resolution 960 X 720 in heretic2 and it fulls almost the entire screen and runs perfectly, with sound !! :lolflag:

---

