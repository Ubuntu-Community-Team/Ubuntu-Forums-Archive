---
title: "Poor 3D Performance 13.10 Nvidia mainly Steam and Virtualbox"
date: 2014-03-21
forum: Gaming &amp; Leisure
---

### Post by i0ls on 2014-03-21
OK I have a  I3 3.1, GTX 650 TI Boost, 8 GB ram, ssd and play a fair share of games with steam. I recently installed windows 7 on a secondary hard drive to see if there was anything I was missing aside from access to some titles. 

Take TF2 for example because I play a lot of it.
Ubuntu has tearing with or without vsync enabled in both nvidia untility, and ccsm. When enabled in the game it self it stops tearing a little bit but still feels sort of choppy if i watch corners of walls and doors etc.
With windows (which i really don't like) there was tearing until I enabled vsync in the nvidia utility and then everything was fine without negative effects on the rendering speed.

So how do I go about making the experience better on ubuntu? I really don't like having to go anywhere near windows and I refuse to do anything more than the 30 day grace period.

---

### Post by sffvba[e0rt on 2014-03-21
The obvious first question, are you running the proprietary nVidia drivers installed via the additional drivers dialogue?

---

### Post by oldrocker99 on 2014-03-21
I have a 650ti, using nVidia 331 drivers, and Stema games work fine for me.

---

### Post by ajgreeny on 2014-03-21
Where does the virtualbox figure in your question?

If you are running games in a VM you will never get good 3D graphics as it is totally limited by the virtual graphic chip used nby VBox.

To do 3D games justice you MUST run them on real hardware not a VM.  I can't comment on steam, nor your nvidia graphic card as I have no experience of either.

---

### Post by efflandt on 2014-03-22
If must be something about your configuration or maybe not having proper video drivers (or if it is in a virtualbox). I have run steam games, including TF2 on a 64-bit 13.10 laptop @ 1080p smoothly (no tearing) once I figured out how to get steam to find 32-bit libs and parameters for optirun to launch TF2 with Nvidia graphics (dual Intel HD 4600/Nvidia GTX 765M). TF2 was dismal with Intel HD 4600 graphics (pauses with audio repeating in short loops). And no problems for GTX 550 Ti on my 64-bit 12.04 desktop @ 1080p which runs TF2 a bit faster. I never use vsync or sync to vblank or whatever it is called.

---

