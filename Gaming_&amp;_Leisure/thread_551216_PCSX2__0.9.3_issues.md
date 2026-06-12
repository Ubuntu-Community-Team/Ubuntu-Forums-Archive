---
title: "PCSX2  0.9.3 issues"
date: 2007-09-14
forum: Gaming &amp; Leisure
---

### Post by EldrinOS on 2007-09-14
Hi all, first ever post on Ubuntu forums.  Hope I don't screw this up.  Anyway, I've finished compiling PCSX2 on my laptop with Feisty on it.  It won't however, load any graphics plugins, and this message pops up upon starting:

"Could Not Load GS Plugin 'plugins/':plugins/: cannot read file data: Is a directory"

This of course sucks, because no graphics plugin equals no game.  I'm using a Dell Inspiron 6000 with the (admittedly) crappy integrated chipset.  I know that has nothing to do with the real problem, but I suppose that helps.

If there's anything to do to resolve this issue, I'd seriously appreciate it.

---

### Post by process91 on 2007-10-06
This issue almost always has to do with the cg toolkit not being installed.

Feisty Instructions:
Install alien
```
sudo apt-get install alien
```
Go [here]("http://developer.nvidia.com/object/cg_toolkit.html") and download the correct RPM for your architecture.
Use alien to convert the RPM into a DEB file.
Use dpkg to install the DEB file.

Gutsy Instructions:
The cg toolkit is available in the multiverse repos
```
sudo apt-get install nvidia-cg-toolkit
```

Make sure to install this even if you don't have an nvidia card

---

### Post by wishyjr on 2007-11-04
ok, i tried this bud it didn't work - any other things i might have forgotten?

---

### Post by Sockerdrickan on 2007-11-04
Recompile

---

### Post by wishyjr on 2007-11-04
cheers!

---

### Post by Sockerdrickan on 2007-11-05
=) What's your FPS?

---

### Post by Zyphrexi on 2007-11-06
I'm getting around 6.3 fps... wth?

---

### Post by go_beep_yourself on 2007-11-12
> **process91 said:**
> This issue almost always has to do with the cg toolkit not being installed.

Feisty Instructions:
Install alien
```
sudo apt-get install alien
```
Go [here]("http://developer.nvidia.com/object/cg_toolkit.html") and download the correct RPM for your architecture.
Use alien to convert the RPM into a DEB file.
Use dpkg to install the DEB file.

Gutsy Instructions:
The cg toolkit is available in the multiverse repos
```
sudo apt-get install nvidia-cg-toolkit
```

Make sure to install this even if you don't have an nvidia card

I never installed the nvidia-cg-toolkit, and it compiled for me. Why do you say that is needed? Does pcsx2 need to be recompiled after nvidia-cg-toolkit is installed?

---

### Post by process91 on 2007-11-14
If you're not getting the error at the beginning of this post then don't worry about installing the cg-toolkit. All I know is that when I got this error and installed the toolkit and recompiled PCSX the error went away.

---

### Post by disturbedite on 2007-11-14
(the emulator) pSX is better.  (no plugins required for one thing).

let the flames begin.  ;)

---

### Post by go_beep_yourself on 2007-11-23
> **process91 said:**
> This issue almost always has to do with the cg toolkit not being installed.

Feisty Instructions:
Install alien
```
sudo apt-get install alien
```
Go [here]("http://developer.nvidia.com/object/cg_toolkit.html") and download the correct RPM for your architecture.
Use alien to convert the RPM into a DEB file.
Use dpkg to install the DEB file.

Gutsy Instructions:
The cg toolkit is available in the multiverse repos
```
sudo apt-get install nvidia-cg-toolkit
```

Make sure to install this even if you don't have an nvidia card

I verified that I have the nvidia cg toolkit installed.

$ dpkg -l | grep nvidia-cg
ii  nvidia-cg-toolkit                      1.5.0.0019-1                         NVIDIA Cg Toolkit installer

I am still getting the same error as the guy you were replying to.

[http://img162.imageshack.us/img162/1233/pcsx2noworkyaz9.png](http://img162.imageshack.us/img162/1233/pcsx2noworkyaz9.png)

[http://img162.imageshack.us/img162/424/screenshotpcsx2msguy4.png](http://img162.imageshack.us/img162/424/screenshotpcsx2msguy4.png)

---

### Post by dfreer on 2007-11-23
> **disturbedite said:**
> (the emulator) pSX is better.  (no plugins required for one thing).

let the flames begin.  ;)

pSX doesn't emulate playstation 2 games, which is what this thread is about. How's that for flames? :lolflag: I <3 disturbedite

---

### Post by keyboardslave on 2008-01-11
Greetings,

I suggest you start from scratch and you follow this guide here,

[http://lulug.wordpress.com/2007/05/17/guides-xxihow-install-pcsx2-emulator-sony-playstation-2-on-gnulinux-ubuntu-os/](http://lulug.wordpress.com/2007/05/17/guides-xxihow-install-pcsx2-emulator-sony-playstation-2-on-gnulinux-ubuntu-os/)

it works flawless for me.


B.T.W  I cant recall anything disturbedite saying ever being relevent he puts random posts in every emulation or gaming topic iv been to since iv been a user of ubuntu.
explains his post count i spose, no point posting if u dont have anything important or relevant to say ^_^, 

Best of Luck,

---

