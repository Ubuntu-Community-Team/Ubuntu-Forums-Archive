---
title: "Ubuntu on a Dell Optiplex GX620 Desktop"
date: 2009-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RookieUbuntuUser58 on 2009-02-24
Well Im thinking about completely switching to Ubuntu or some form of Linux on my old desktop (only use for engineering programs and Office, Photoshop). My computer specs are GX620 with Intel Pentium 4(3.0GHZ), 128MB ATI Radeon X600 SE, and 512 MB DDR2 RAM. Will I have any compatibility issues, I would like everything to completely work. Either out of the box or through a fix, as long as all features work. I searched and didn't find much about this desktop and linux. 

Now the thing is the computer is full of engineering programs that only run on Windows and a new version of Office which I bought and dont want to lose. I know that I can use vmware but how exactly would that work. Would this allow me to delete the XP Pro partition and still have access to those programs and files? What other options are available? Would dual booting be the best option? Thanks in advance for answering such a newbie question.

Another thing is my desktop runs my router and DSL modem. So will there be issues there?

---

### Post by Mordac85 on 2009-02-24
You should be able to work right out of the box.  The only issue may be if you want ATI drivers.  Since I normally have nVidia cards I couldn't tell you about any issue w/an ATI card.

If you want to keep the Windows programs, but don't want to re-install them you will need to dual boot.  If you don't mind re-installing the apps, you can either run a Windows VM or use something like [Crossover Linux]("http://www.codeweavers.com/products/cxlinux/").

As for the router & DSL, I don't understand what you mean my your desktop 'running' them, but it shouldn't be too terribly difficult to setup a configuration like what you have now.

I have a 620 in my lab so if I get time I'll load Ibex and see if there are any issues.

---

### Post by dfrandin on 2009-02-26
I have a GX620 that I've installed 8.04/8.10 on, and in my case, the only gotcha I found was that when I tried to install with my Nvidia GeForce8400 video card.. With this card installed, I installed without issue, but upon the first boot after installation, the gui failed to start, and a x-restart could not be done.. If I removed the Nvidia card, using the Intel onboard video, all worked just fine.. Wonder if I have a bad video card.. kinda strange because the card works perfectly under windows XP/Vista... As for the GX620, its pretty much a piece of cake to get Ubuntu installed on....

Hope this helps

Dave

---

