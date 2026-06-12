---
title: "DirectX Compatability?"
date: 2010-04-15
forum: Gaming &amp; Leisure
---

### Post by tyblogger5 on 2010-04-15
Hi "Ubuntu-ers",

I just helped someone install Ubuntu 9.10 on their machine.  We were able to set up duel-monitor support on his machine running an NVidia Graphics Card.  Now he has a question, is there any DirectX support on Ubuntu?

Thanks,
tyblogger5

---

### Post by Technophobia on 2010-04-15
No. DirectX is only for Windows(not even for a Mac). You can install Wine, which is a tool that can run a fair amount of the Direct X games out there. I do have to give you a fair warning that performance will not be the best with Wine, and the newest games are not likely to work.

To install just look for Wine in the Software Center or type "sudo apt-get install wine" in the console.

If your friend is looking for some native(built for Linux) games for Linux they can try looking here [http://ubuntu-gamers-arena.org/](http://ubuntu-gamers-arena.org/) or [http://www.mobygames.com/browse/games/linux/](http://www.mobygames.com/browse/games/linux/).

Good luck

---

### Post by hikaricore on 2010-04-16
Wine actually converts/interperates DirectX as OpenGL however.  ^_^
So this isn't even actual "support" per se.

---

### Post by tyblogger5 on 2010-04-18
OK, so the only way to use DirectX on any non-Windows OS is to wait for VirtualBox to come out with DirectX support or use Wine?

---

### Post by efikkan on 2010-04-18
Yes, Virtualbox or Wine/Crossover Games/Cedega.

---

### Post by MaraShylaStewart on 2010-04-19
Microsoft DirectX is a collection of application programming interfaces (APIs) for handling tasks related to multimedia, especially game programming and video, on Microsoft platforms. Originally, the names of these APIs all began with Direct, such as Direct3D, DirectDraw, DirectMusic, DirectPlay, DirectSound, and so forth. The name DirectX was coined as shorthand term for all of these APIs (the X standing in for the particular API names) and soon became the name of the collection. When Microsoft later set out to develop a gaming console, the X was used as the basis of the name Xbox to indicate that the console was based on DirectX technology.

---

### Post by meborc on 2010-04-19
> **efikkan said:**
> Yes, Virtualbox or Wine/Crossover Games/Cedega.

i don't think virtualbox is any good with 3d stuff ;)

wine actually runs all my games fine... check out [http://appdb.winehq.org](http://appdb.winehq.org) and search for the games you are interested in

---

### Post by Crazedpsyc on 2010-04-19
I have been trying to figure this out too! i want to run Sketchup and Spore, but one uses directx and flash, and the other uses opnegl. I have tried both in wine and I get Sketchup failed to initialize directx in one, and the Spore simply doesn't work! (well spore itself might work but I can't get through the initial stuff like checking for updates without a microsoft version of flash [which I can't install on wine])

---

### Post by hxcobd on 2010-04-19
Sketchup uses OpenGL and supposedly works fine on relatively new-ish versions of Wine.

[http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

---

