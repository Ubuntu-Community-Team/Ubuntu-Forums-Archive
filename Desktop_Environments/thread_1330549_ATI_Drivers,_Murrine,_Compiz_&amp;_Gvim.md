---
title: "ATI Drivers, Murrine, Compiz &amp; Gvim"
date: 2009-11-18
forum: Desktop Environments
---

### Post by robrobbins on 2009-11-18
Hello Ubuntu forums. I just did a fresh install of Karmic on a Dell 1555 studio. I was running Fedora 11, but the ATI support was not as well implemented as Karmic's (I have used both, Karmic wins. My card is a Radeon 4500 HD 256). Anyway, everything is working great except for one thing, an issue with slooooow screen redraws with Gvim when using the NERDTree (i love that script, hence the post), using tag list,  and to a lesser degree opening and closing tabs. Now, I have installed from the PPA the vim and gvim versions which have the fix for the 'gtk static blah blah' error and that fixed that (thankfully -- what an annoying bug that was). If I run vim in terminal mode there is no lag in opening and closing tabs, using nerdtree or tag lists. 

So to recap. Gvim has some really slow screen redraws when using scripts which open and close other windows like NERDTree, Tlist, and tabs. I am using the ATI drivers for video, as well as compiz for desktop effects (turning that off and or switching between murrine, clearlooks, and other various gtk & metacity themes don't seem to change the problem)

The magnitude of the slowness is just a few seconds (maybe 2) but that's loooong for gvim, not to mention totally against the reason for learning to use it (speed and more speed).

Anyone else seeing this?

---

### Post by qiyeshu on 2009-11-26
I'm facing the same problem, my laptop is Thinkpad T500 also with ATI video card and I am using ubuntu 9.10.

The command-line based vim works quite well in my laptop. But gvim is very slow (when redraw screen like PageUp and PageDown). It should not be like that. I tried the gedit, which is much faster than gvim. There must be some problems.

Although I use vim (command line) in most of time, I do hope someone can fix the problem of gvim.

---

