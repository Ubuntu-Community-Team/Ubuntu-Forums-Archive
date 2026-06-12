---
title: "Compiz Blurring the wrong thing in Gaussian Mode"
date: 2010-01-23
forum: Desktop Environments
---

### Post by MadnessRed on 2010-01-23
I am experimenting with Murrine and transparency, and I am aiming at an aero-ish kind of look. The problem is that sometimes it is hard to read the foreground window because the background is obstructing it so I want to blue the background window. 4x4 Bilinear seems to work except that its not blurring it enough, and mipmap blur even less. Gaussian blur however is blurring everything it shouldn't and not what it should. So basically all windows are blurred, except for the windows behind an alpha frame, which are perfectly clear.

I have attached a screenshot, any help would be great. TY

---

### Post by MadnessRed on 2010-01-23
I have recompiled Murrine with a higher opacity which works for now, but I would still like to know how to get gausian blur to work, but no urgency.

---

### Post by MadnessRed on 2010-03-03
any suggestions?

---

### Post by MurkMenthaa on 2010-05-23
Bump.
Same issue. Did you solve it yet ? I'm using fresh new 10.04
Could it be ATI (latest drivers) ? It worked fine on my nvidia.

---

### Post by MadnessRed on 2010-05-23
> **MurkMenthaa said:**
> Bump.
Same issue. Did you solve it yet ? I'm using fresh new 10.04
Could it be ATI (latest drivers) ? It worked fine on my nvidia.

No, I still have it, I fresh installed Ubuntu 10.04 too and still nothing.
ATi 3200

---

### Post by stinkeye on 2010-05-24
Gaussian mode works for me using this guide to [**_[COLOR="DarkRed"]Enable RGBA Transparency[/COLOR]_**]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html")

I'm using the nvidia drivers though.

---

### Post by MurkMenthaa on 2010-05-24
With nvidia it worked for me too (with **and** without RGBA enabled). I think ATI is the problem here, because several other compiz plugins which worked fine with nvidia are also not working.
Can someone with ATI drivers confirm they have same issue with gaussian blur ?
> **stinkeye said:**
> Gaussian mode works for me using this guide to [**_[COLOR=DarkRed]Enable RGBA Transparency[/COLOR]_**]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html")
I'm using the nvidia drivers though.
Thanks for reply. Does it work for you ***only*** if you enable RGBA transparency ?

---

### Post by stinkeye on 2010-05-24
> Thanks for reply. Does it work for you only if you enable RGBA transparency ?

Blur windows also works if I disable rgba and use the compiz plugin 
*opacity, brightness and saturation* to set the transparency of windows.

---

### Post by digitalchemystery on 2010-06-07
Hey, this has been a pretty annoying issue for me these past few months. Unfortunately, the ATI card I've got in my laptop has drivers which broke Gaussian blur functionality after version 9.11. It works fine on my machines that have nVidia cards (and if I'm using the 9.11 driver on my ATI laptop). I *need* Gaussian blur  :)

---

### Post by MadnessRed on 2010-07-07
yh, it is a really big problem you could try the open source drivers, but that may not be an option. Very annoying, hopefully ATi will release some better drivers soon.

---

