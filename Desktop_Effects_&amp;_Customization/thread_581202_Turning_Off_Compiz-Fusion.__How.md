---
title: "Turning Off Compiz-Fusion.  How?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by alligoodw on 2007-10-19
If my understanding is correct, Compiz-Fusion is a window manager for Ubuntu 7.10.  Granted this understanding is correct, how does one go about turning it off?  I have a Nvidia card and I'm just to exhausted with the try.  

What other window managers are available for Ubuntu that support transparent window borders?  Something tried and true, something which is easy to implement.

---

### Post by Forlong on 2007-10-19
> **alligoodw said:**
> If my understanding is correct, Compiz-Fusion is a window manager for Ubuntu 7.10.  Granted this understanding is correct, how does one go about turning it off? 
Just open [Alt]+[F2] and type
```
metacity --replace
```
(GNOME)
```
kwin --replace
```
(KDE)
```
xfwm4 --replace
```
(Xfce)

---

### Post by z0phi3l on 2007-10-19
> **alligoodw said:**
> If my understanding is correct, Compiz-Fusion is a window manager for Ubuntu 7.10.  Granted this understanding is correct, how does one go about turning it off?  I have a Nvidia card and I'm just to exhausted with the try.  

What other window managers are available for Ubuntu that support transparent window borders?  Something tried and true, something which is easy to implement.

CF is the only window manager to support transparent windows hat I'm aware of until KDE4 comes out officially



What's so wrong with CF that you don't want to use it? I have it working just fine with my 7800GX

---

### Post by alligoodw on 2007-10-19
> **z0phi3l said:**
> CF is the only window manager to support transparent windows hat I'm aware of until KDE4 comes out officially

What's so wrong with CF that you don't want to use it? I have it working just fine with my 7800GX

This is a good question.  With everything else working on my computer, all hardware devices and etc., and seeing that there are about as many remedies for the Nvidia Compiz-Fussion issue as there are stars in the sky, I'm a little skittish to go there.  I've followed a fews pieces of advice to get my video and Compiz in alignment with one another but alas, I just decided to turn it off.  

I've read that emerald should be installed and emerald shouldn't be installed.  With Compiz configured with extras, my video card information isn't right; when I change the screen resolution to what I want it to be, Compiz turns itself off.  I just don't have the time or patience to work with things of this nature. 

In all, I give Ubuntu 7.19 a thumbs up.  Again, everything else works flawlessly ie., keyboard, mouse, dvd's, music, memory stick, cam and etc.  It would have been easier if a wizard had been created which would have ask the appropriate questions when installing compiz-fusion, and set up the video information properly.

---

### Post by FredB on 2007-10-19
> **alligoodw said:**
> If my understanding is correct, Compiz-Fusion is a window manager for Ubuntu 7.10.  Granted this understanding is correct, how does one go about turning it off?  I have a Nvidia card and I'm just to exhausted with the try.  

What other window managers are available for Ubuntu that support transparent window borders?  Something tried and true, something which is easy to implement.

Very simply. System Menu / Preferences / Appearance / Visual Effects

And select none.

No need to use console or command line.

---

