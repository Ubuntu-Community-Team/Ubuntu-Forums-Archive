---
title: "Minimal Ubuntu for Gaming?"
date: 2014-10-26
forum: Gaming &amp; Leisure
---

### Post by UDroidie626 on 2014-10-26
Okay so I want to switch from Antergos to Ubuntu for offical Steam support, and was wondering, should I use Minimal or the regular Ubuntu install CD?
I would ideally just like to get rid of bloat apps, having a nice slim system with Unity, Steam and browser.

Thanks!

---

### Post by sudodus on 2014-10-26
If you want a light and very responsive system, I suggest that you try

- medium light ***Xubuntu*** or
- ultra light ***Lubuntu***,

which have lighter desktop environments than standard Ubuntu. The next step would be to start from the ***Ubuntu mini.iso*** and install only what you need, a window manager instead of the full desktop environment, for example

- ***openbox***
- ***fluxbox***
- ***jwm***

It is much easier to start with a very minimal system and add program packages (than to start with a full system and remove packages).

---

### Post by Bucky Ball on 2014-10-26
I start with a minimal install regardless of what I intend to use the machine for then load xfce4. I don't want anything on there I don't need (that I can avoid, that is). I imagine with just the base kernel, Unity, Steam and a browser your machine will fly, perfect for gaming. My only question would be why bother with Unity if this is all you're doing with your machine? But all a matter of taste.

If you go minimal, don't install *buntu-desktop anything after you install the base kernel. Defeats the purpose and you may as well just install Ubuntu or one of it's derivatives in the first place. 

Good luck.

---

### Post by oldrocker99 on 2014-10-26
MATE is also lightweight, and gves you that good old 8.04 feeling.

---

### Post by sffvba[e0rt on 2014-10-26
As long as the DE you use suspends rendering when an application goes full screen I don't see any benefit of the one over the other except for the amount of memory it may use.

---

### Post by pqwoerituytrueiwoq on 2014-10-27
we can go lighter than lubuntu with minimal lubuntu, the option is in the mini.iso install image. it is about 3gb installed after updates and a couple small apps installed
warning advanced users only, it is not joking about minimal, you get a GUI desktop, a panel, file manager, 2 terminals, and 2 settings apps. No calculator, web browser, software center, etc.
BTW pulseaudio is not even installed by default, you will probably want to install that and pavucontrol

---

### Post by Bucky Ball on 2014-10-27
> **pqwoerituytrueiwoq said:**
> 
warning advanced users only, it is not joking about minimal, you get a GUI desktop, a panel, file manager, 2 terminals, and 2 settings apps. No calculator, web browser, software center, etc.


Are you talking about a mini Lubuntu (which I'm not familiar with). On a minimal install you get none of the things you mention, only the base kernel if you don't choose a system profile (don't if you want minimal at its minimal-est). 

After install you reboot to a CLI, login and there you are. 'sudo apt-get install' to your heart's content. You need to install any desktop environment, terminal, or anything else manually. Including Pulse.

I generally start by installing a DE and some basics to get me started, then install other things as the need arises. This keeps it to a bare minimum of only things I use.

Did one of these installs for a friend on their new Toshiba Tecra with 8Gb RAM and a 7200rpm SATA hard drive. Flies. Like using an SSD.

---

### Post by dannyboy79 on 2014-10-27
> **Bucky Ball said:**
> 

I generally start by installing a DE and some basics to get me started, could you be more specific when you say you install a DE. I mean if you're just running
```
sudo apt-get install lubuntu-desktop

```
 than why not just start with lubuntu? i would think if you want it minimal you would install just the actual window manager (xfwm4, icewm, fluxbox, openbox) no DE.

---

### Post by Bucky Ball on 2014-10-27
> **dannyboy79 said:**
> could you be more specific when you say you install a DE. I mean if you're just running
```
sudo apt-get install lubuntu-desktop

```
 than why not just start with lubuntu? 

Exactly. That's not what I'm saying. I'm saying install a desktop *_environment_*, not the whole OS install, which is what *buntu-desktop would do. It's wording is misleading in my opinion. But keep in mind, it is not 'lubuntu-desktop-environment'. Which would be lxde. And that's all you want.

If you want the Lubuntu DE, then:

```
sudo apt-get install lxde
```

That's it. The DE only is what you get. You're exactly right, install lubuntu-desktop is identical to installing Lubuntu, so don't do it! ;)

PS: People always give the advice to do a minimal install and then install *buntu-desktop. It drives me nuts. Installing lxde and install lubuntu-desktop have two totally different outcomes and the doing the latter defeats the whole purpose of bothering with a mini install in the first place.

And yes, you could install just a window manager, but I generally don't run on them alone. I use xfce4, xfwm4, lxterminal, pcmanfm ... a mish mash really, but perfect for me and how I work. ;)

---

### Post by mastablasta on 2014-10-27
Tori OS got RAM down to below 50 MB.

Using tiled windows managers like i3 could probably get it even lower. :P

---

### Post by sudodus on 2014-10-27
I'm also looking forward to the release of ToriOS, which uses the JWM window manager :-P

Until then, look at the size (RAM-wise and disk-wise) of some small alternatives at this link

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

---

### Post by dannyboy79 on 2014-10-27
you could always have a normal ubuntu install for daily productivity but then create a separate session which only launches the minimum X server, openbox, and steam.

---

### Post by mastablasta on 2014-10-27
> **dannyboy79 said:**
> you could always have a normal ubuntu install for daily productivity but then create a separate session which only launches the minimum X server, openbox, and steam.

that would make most sense. 

when you login you can choose the session. 

so creating something like user: gamer and then selecting his default session: openbox or something similar and light would solve this.

I mean people don't usually game while they work. unless you "play" progress quest or something :)

---

### Post by sffvba[e0rt on 2014-10-28
Something of interest - [6-Way Ubuntu 14.10 Linux Desktop Benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1410_6desktops&num=1")

---

### Post by mastablasta on 2014-10-28
interesting. though it is not explained if KDE "stock settings" means that disable desktop effects on full screen (e.g. games) is set to off I believe.

---

### Post by sffvba[e0rt on 2014-10-28
> **mastablasta said:**
> interesting. though it is not explained if KDE "stock settings" means that disable desktop effects on full screen (e.g. games) is set to off I believe.

Yes, they are off (about a year ago there was a comparison when kwin got a major redo and it was in some instances faster than the other DE's (baring the ultra barebone ones))...

---

### Post by mastablasta on 2014-10-29
hmm... perhaps they fell asleep since they are moving to new plasma? I mean it used to be good fast and responsive but now others overtook it would be interesting to know why. 

KDE does have too many services integrated. I never need them yet they need to be running. which could be the cause...

---

