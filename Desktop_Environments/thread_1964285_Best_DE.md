---
title: "Best DE?"
date: 2012-04-23
forum: Desktop Environments
---

### Post by codingman on 2012-04-23
Hi, I have been using Ubuntu for about 6 months, and I have tried multiple DEs and I have been wondering which is the fastest? (I have heard that fluxbox is fast but it hangs on my computer for some reason :( .
BTW, I am new to this forum :)

---

### Post by theos911 on 2012-04-23
Are you talking DEs or Window Managers?

The generally accepted knowledge is:

Heavyweight:
Gnome/Unity - The default that everyone is accustomed to.
KDE - The second most popular.

Middleweight:
Xfce - The historical "lightweight", but lost that title to LXDE.

Lightweight:
LXDE - Lightest, Fastest, but fewest extra features.

---

### Post by techsupport on 2012-04-23
> **codingman said:**
> Hi, I have been using Ubuntu for about 6 months, and I have tried multiple DEs and I have been wondering which is the fastest? (I have heard that fluxbox is fast but it hangs on my computer for some reason :( .
BTW, I am new to this forum :)

Fastest I knew was Crunchbang Openbox back on 9.04. But they switched to pure Debian and it is no longer Ubuntu.  You can install Lubuntu, and then install Openbox for a very similar DE. Madbox Ubuntu is good too, but it is only a 32-bit version. :S

Crunchbang 
[http://crunchbang.org/download/](http://crunchbang.org/download/)

---

### Post by jldoll on 2012-04-23
> **theos911 said:**
> Are you talking DEs or Window Managers?

The generally accepted knowledge is:

Heavyweight:
Gnome/Unity - The default that everyone is accustomed to.
KDE - The second most popular.

Middleweight:
Xfce - The historical "lightweight", but lost that title to LXDE.

Lightweight:
LXDE - Lightest, Fastest, but fewest extra features.
I've been using Lubuntu on my machines for awhile and haven't missed too many extras. You can add just about anything you want within the limits of your tolerance for performance versus convenience. I've left one older machine as pretty much pure Lubuntu to keep it snappy, and added most of the extras I do like about Ubuntu to my everyday machine as I like lxde better than unity. The thing most noticeably missing are widgets, but it doesn't take much googling to figure out how to turn simple scripts into desktop files to make psuedo-widgets and taskbar shortcuts.

---

### Post by dniMretsaM on 2012-04-23
LXDE is light weight. It uses the Openbox window manager my default. Razor-qt is a lighteight Qt-based desktop (it doesn't come with a WM, but the officially recommended one is Openbox). You could also go with only a window manager like Awesome, Sawfish, XMonad, etc. I would recommend Lubuntu (LXDE), as it comes with a nice set of default programs. If you want to roll your own, though, you'll probably end up with a lighter environment. Razor-qt isn't really "finished" yet, so it's not ideal (I like it though, as I'm a fan of Qt).

---

### Post by Max Blyss on 2012-04-23
IMO, the best DE all - around is XFCE.  You have speed, functionality, lightwieght composting for neat-o transparencies, a lot of options for customization, and a good selection of panel applets...  

I've used it both as an additional DE and in it's native Xubuntu, works great every time.

Oh, and at least on my box, it ran just as fast as LXDE... (2.8G Pentium4 dual core / 3g RAM / and 256MB ATI Raedon card).

---

### Post by RichardCain on 2012-04-24
I used Xfce for a long time, but got annoyed by the restrictive nature (i.e. only Thunar can control the desktop).  I have tried KDE, Gnome 3, Unity and LXDE, but none felt just right.

I recently installed *Cinnamon* and am really impressed.  It's quick, customisable and very easy to use.  It's a fork of gnome 3 made by LinuxMint, but available for Ubuntu and other distros [here]("http://maketecheasier.com/cinnamon-alternative-for-gnome-shell/2012/03/19").  It will be my DE for the foreseeable future.

---

### Post by theos911 on 2012-04-24
Sorry, I didn't mean that as LXDE *lacks* features. I just meant that unlike Xfce, Gnome, or KDE, they aren't at your fingertips. They can be added with a bit of a work, but part of the speed gained is by not using them in the first place.


My personal vote goes to Xfce. It is fast, lightweight, and provides enough basic eye candy features to not require extra work, while not having them enabled by default so as to slow you down with ones you don't want.

---

### Post by cortman on 2012-04-24
This question has a thousand answers.
My personal favorite DE/WM?

Gnome shell
Openbox
LXDE

Crunchbang is a wonderful distro, with a very well tweaked openbox/tint2 environment, and is extremely fast.

---

### Post by rewyllys on 2012-04-24
> **RichardCain said:**
> I used Xfce for a long time, but got annoyed by the restrictive nature (i.e. only Thunar can control the desktop).  I have tried KDE, Gnome 3, Unity and LXDE, but none felt just right.

I recently installed *Cinnamon* and am really impressed.  It's quick, customisable and very easy to use.  It's a fork of gnome 3 made by LinuxMint, but available for Ubuntu and other distros [here]("http://maketecheasier.com/cinnamon-alternative-for-gnome-shell/2012/03/19").  It will be my DE for the foreseeable future.
Thanks, Richard, for your comments on Cinnamon and the link to an article on it. 
 
Cinnamon looks very good to me too, and I'll probably adopt it myself after LinuxMint 13 is released in May.

---

### Post by theos911 on 2012-04-24
Yah, I've revisited Gnome & LXDE in the past week and tried Xfce & KDE in the past week. Cinnamon is still on my list. (As is MATE. [which I eventually need to get ported to PPC...])

---

### Post by codingman on 2012-04-24
> **theos911 said:**
> Are you talking DEs or Window Managers?

The generally accepted knowledge is:

Heavyweight:
Gnome/Unity - The default that everyone is accustomed to.
KDE - The second most popular.

Middleweight:
Xfce - The historical "lightweight", but lost that title to LXDE.

Lightweight:
LXDE - Lightest, Fastest, but fewest extra features.

^^ I meant both, sorry:popcorn:

---

### Post by codingman on 2012-04-24
How do set a thread as solved?

---

### Post by collisionystm on 2012-04-24
I did some FPS testing with DE's and glx render.

LXDE, XFCE, KDE and gnome classic were all equal without any kind of compositing enabled.

unity 2D and 3D ranked the same.

When compositing was enabled, KDE, XFCE, Gnome and Unity were all equal.

LXDE just takes less cpu cycles to run because there are far fewer libraries to make up its environment, hence the reason everything loads faster.

Memory is also a factory. Something like LXDE would use a smaller foot print than KDE or Gnome Classic. I have found however Gnome classic and XFCE use the same footprint, probably because xfce uses a lot of the gnome libraries to run.

Good luck

---

### Post by codingman on 2012-04-24
Never mind:KS

---

