---
title: "Faster X server?"
date: 2012-07-02
forum: Desktop Environments
---

### Post by wacossusca34 on 2012-07-02
Hey, I've just decided to jump straight into Ubuntu without question since it's the only distro that supports my computer's hardware and because it has made itself the most common Linux distribution out there.

However, I'm used to the lightweight Puppy Linux. I used it for a long period of time, I got addicted to it's performance, but I was disturbed by how it only seemed to perform nicely on older computers. This one is built with a GTX 560, 8GB of DDR3 ram, an Intel i7 processor, and my motherboard's network chipset seems to be very picky on which OS it wants to run on.

I also found Ubuntu has a very CPU hungry desktop environment, and I also found graphically accelerted applications ran a few hundred FPS lower than what I'm used to on Windows 7. I'm not going to resort to using Windows all the time, just for miscellaneous gaming. Puppy Linux has a graphics environment that conserves so much CPU, you can barely tell it's running on htop, even with an old PC.

So, I have two questions, should I be using a different distro than Ubuntu (I'm totally open now), and if not, is there a much more simplistic and faster X server for Ubuntu 12.04?

Any reply is appreciated!

---

### Post by ajgreeny on 2012-07-02
If it must be one of the *ubuntu family, take a look at Xubuntu (XFCE) or Lubuntu (LXDE), both of which run faster than Ubuntu, though with the specs you talk of there should be no problem at all running Ubuntu with unity.

Have you got the most up-to-date graphic driver for your card?

---

### Post by wacossusca34 on 2012-07-02
Yeah, I expected my computer to run the desktop environment with ease, and yes, I have installed the latest proprietary drivers for my card, but the performance in openGL accelerated applications is horrid (I code with the LWJGL library, so I use my own code to test the performance). I will take a look at Lubuntu and Xubuntu, but I want to keep the same setup I have for my OS now. I know there is a way to install different graphics environemnts on Puppy Linux, is there a way on Ubuntu?

---

### Post by cortman on 2012-07-02
> **wacossusca34 said:**
> Yeah, I expected my computer to run the desktop environment with ease, and yes, I have installed the latest proprietary drivers for my card, but the performance in openGL accelerated applications is horrid (I code with the LWJGL library, so I use my own code to test the performance). I will take a look at Lubuntu and Xubuntu, but I want to keep the same setup I have for my OS now. I know there is a way to install different graphics environemnts on Puppy Linux, is there a way on Ubuntu?

You can install any DE or WM you want on Ubuntu; they're almost all an apt-get away.
Or you could try [Bodhi Linux]("http://bodhilinux.com/"), for a really fast, lightweight, but polished experience.

---

### Post by wacossusca34 on 2012-07-02
> **cortman said:**
> You can install any DE or WM you want on Ubuntu; they're almost all an apt-get away.
Or you could try [Bodhi Linux]("http://bodhilinux.com/"), for a really fast, lightweight, but polished experience.

Thanks, I posted before searching. Bad habit.

I'm running my favourite LXDE, I'm already familiar with it, so my desktop is already configured to my normal setup :D

However, it seems that I'm still receiving the same performance through accelerated applications, but my speed on the system overall increased dramatically. It did that same with KDE as well, sort of strange. I guess I'm not running graphics acceleration, but I never wanted a fancy DE in the first place.

I guess I'l work on getting the drivers from the Nvidia website working.

---

### Post by wacossusca34 on 2012-07-02
> **wacossusca34 said:**
> 
I guess I'l work on getting the drivers from the Nvidia website working.

I was able to kill my desktop environment before with:

```
sudo stop lightdm
```

But now I'm using a different DM. How would I go about exiting this desktop environment so I can work purely from commandline?

---

### Post by PNY on 2012-07-02
if your addicted to the performance of puppy i suppose im addicted to desktop environments. Try apt-geting lubuntu-desktop or kubuntu-desktop or just lxde or try awesome(my personal favorite)

---

### Post by black veils on 2012-07-02
the keyboard shortcuts **Ctrl** + **Alt** + **F2** to go into CLI, then **Ctrl** + **Alt** + **F7** to go back to GUI

---

### Post by MG&amp;TL on 2012-07-02
> **wacossusca34 said:**
> I was able to kill my desktop environment before with:

```
sudo stop lightdm
```But now I'm using a different DM. How would I go about exiting this desktop environment so I can work purely from commandline?

A similiar process. What DM are you using?

E.g. for gdm:

```
sudo service gdm stop
```

---

### Post by wacossusca34 on 2012-07-02
> **black veils said:**
> the keyboard shortcuts **Ctrl** + **Alt** + **F2** to go into CLI, then **Ctrl** + **Alt** + **F7** to go back to GUI

No, I need to actually kill the X interface for my driver to install. It's a CLI only installer.

---

### Post by PNY on 2012-07-02
thats a good question. i never did get a clear answer on how to exit x to the command line. the app to end all apps!

---

### Post by black veils on 2012-07-02
then i think lxde uses lxdm

---

### Post by sudodus on 2012-07-02
Try ***ctrl + alt + backspace*** in LXDE (to exit) *Edit: Works in some distros running LXDE, but not Lubuntu.*

By the way, I also recommend Lubuntu and or Xubuntu, depending on your taste. And if you want to play demanding 1920x1080/50p videos, Mplayer2 is a good player (not fancy, but efficient).

Another alternative is Knoppix, which is very good at detecting hardware. It can be installed to an 'almost-debian' system. I guess the nvidia drivers from the manufacturer's web site work also for that distro.

---

### Post by wacossusca34 on 2012-07-02
> **MG&TL said:**
> A similiar process. What DM are you using?

E.g. for gdm:

```
sudo service gdm stop
```

I'm using LXDE.

---

### Post by sudodus on 2012-07-02
> **wacossusca34 said:**
> I'm using LXDE.
In Lubuntu I can stop the desktop environment with
```
sudo /etc/init.d/lightdm stop
```

---

### Post by MG&amp;TL on 2012-07-03
> **sudodus said:**
> In Lubuntu I can stop the desktop environment with
```
sudo /etc/init.d/lightdm stop
```

Lubuntu 12.04 and above uses lightdm. Otherwise, it uses LXDM. You can start/stop either with:

```
sudo service [DM] start/stop
```

Replacing [DM] with your display manager (lightdm or lxdm), and start/stop with what you want to do with it.

---

