---
title: "How do you get it?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-26
From what I've heard, KDE is a more advanced environmenment than gnome, and distros that have both recommend you use KDE. I was unaware that ubuntu could run KDE until I stumbled across this forum. I then researched the download page, but couldn't find it.

Where do I get KDE for ubuntu? Thanks!

---

### Post by frs-design on 2005-05-26
Hi !

Here for the install CDROM and the live cd too:
[http://releases.ubuntu.com/kubuntu/hoary/](http://releases.ubuntu.com/kubuntu/hoary/)

bye ++

---

### Post by jasmuz on 2005-05-26
[QUOTE=Curlydave]From what I've heard, KDE is a more advanced environmenment than gnome, and distros that have both recommend you use KDE. I was unaware that ubuntu could run KDE until I stumbled across this forum. I then researched the download page, but couldn't find it.

Where do I get KDE for ubuntu? Thanks![/QUOTE]
 Download the following packages from your repositories:
kdebase - KDE Base metapackage
kdebase-bin - KDE Base (binaries)
kdebase-data - KDE Base (shared data)
kdebase-kio-plugins - KDE I/O Slaves

I think that is pretty basic, altough it will ask you to download several others as addons..

I do recomend you also try out XFCE, its a nice one also.

---

### Post by cutOff on 2005-05-26
[QUOTE=jasmuz]I do recomend you also try out XFCE, its a nice one also.[/QUOTE]
I agree. It is a light-weight enough desktop and very nice to use.

---

### Post by elsewhere on 2005-05-26
Might be easiest to install kubuntu-desktop, will pull all the necessary kde packages + the kubuntu customizations and default settings.

Cheers,
KV

---

### Post by Curlydave on 2005-05-26
I just burned a new CD with kubuntu and am posting from my new kubuntu install. Hmmm, It seems a tad bloated, and the included apps are (imo) inferior to the gnome ones, although I like the appearance much more. I'm still trying to figure out how to get it not to do web-style clicking. 

I think I"m going to give XFCE a try. Any info on that? Thanks!

---

### Post by GeneralZod on 2005-05-27
[QUOTE=Curlydave]e. I'm still trying to figure out how to get it not to do web-style clicking. 

I think I"m going to give XFCE a try. Any info on that? Thanks![/QUOTE]

```

sudo kcontrol

```

Then Peripherals -> Mouse, and follow your nose.  A bit obscure, but there you go! ;)

About XFCE - check out the homepage here:

[http://xfce.org/](http://xfce.org/)

It's a very nicely written, lightweight (but functional) DE.  Search Synaptic for xfce, then install xfce4 and any of the other related goodies that take your fancy.  Then log out of KDE, and start a new session as XFCE (or just pick Start New Session from the "K"-Menu's "Switch User" command).

Hope this helps,
Simon

---

### Post by 23meg on 2005-05-27
xfce has become so good that as a long time gnome user i'm eyeing it as a full time wm. how "advanced" a certain environment is may not be a deciding factor if you'll not be making use of those advanced features day to day.

---

### Post by mohaham on 2005-05-27
Here's a simple way to install KDE and XFCE:

sudo apt-get install kubuntu-desktop

sudo apt-get install xfce4 xfmedia xterminal xfce4-theme-brushedchrome

---

