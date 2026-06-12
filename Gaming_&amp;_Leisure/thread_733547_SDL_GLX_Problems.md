---
title: "SDL GLX Problems?"
date: 2008-03-23
forum: Gaming &amp; Leisure
---

### Post by Xavieran on 2008-03-23
Whenever I launch XMoto or Uplink I get this error:
Could not initialize SDL Video: Couldn't find matching GLX visual.

And the game does not work...I have reinstalled anything to do with sdl and have xserver-xgl installed correctly...


Any ideas what's wrong or what I could do to fix it?

---

### Post by compiledkernel on 2008-03-23
system specs, specifically your video card? 

also, what are you using for a video driver.

---

### Post by Xavieran on 2008-03-23
I have an nvidia geforce 7500 of which it does not work because I'm running gutsy...could that be the issue?

---

### Post by compiledkernel on 2008-03-23
hmmmm, did you install the nvidia-glx-new package? 

after which then you run 

sudo nvidia-xconfig 

from a terminal and then restart X.

---

### Post by Xavieran on 2008-03-24
Will Do!

---

### Post by forrestcupp on 2008-03-24
You need to get rid of Xgl.  You don't need it with nvidia, and if you're running an Xgl session, dri and glx won't work.  Don't confuse **glx** with **Xgl**.

```
sudo apt-get --purge remove xserver-xgl
```
And reboot.

Then go to System->Administration->Restricted Drivers Manager and make sure you have the drivers enabled for your nvidia card.

---

### Post by BigSilly on 2008-03-24
It could be that the drivers simply need updating now in Ubuntu's repo. The current 100.14 ones are from September last year, and there is a newer stable release from last month on Nvidia's site (169.12) which fix all sorts of problems people are reporting. They're a complete nightmare to install manually though, so I'm going to wait until Ubuntu gets them in the repo. Which will be soon hopefully. Mandriva have them in theirs, so I'm crossing my fingers that Ubuntu follows suit. 

Are they likely to be updated for Hardy? Anyone know?

---

### Post by Xavieran on 2008-03-25
Gutsy's support of video cards has really sucked...
A few of my friends have had to forfeit the use of their video cards or install a different distro on a separate partition...
I'll just wait for Hardy...let's hope hardy fixes it...:)

---

### Post by BigSilly on 2008-03-26
Well, I guess I've just been lucky. I've been really pleased with the 3D experience in Ubuntu Gutsy. Between the 3D desktop and my favourite 3D games it's performed just as I would want. I've just done a minor upgrade to the graphics card and was really happy to find Ubuntu recognise it immediately without any tinkering. The only bit I was slightly disappointed with was the older Nvidia drivers in the repo. As I say, on my Mandriva install it downloaded the very latest ones (169.12), but here on Ubuntu it's the somewhat older 100.14 drivers. Still, it's not something I'd get too bothered about, but it might explain why some people are having issues with their 3D. I'm sure they'll update them for Hardy.

---

