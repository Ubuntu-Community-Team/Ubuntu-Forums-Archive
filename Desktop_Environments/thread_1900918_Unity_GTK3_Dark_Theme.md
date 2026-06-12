---
title: "Unity GTK3 Dark Theme"
date: 2011-12-27
forum: Desktop Environments
---

### Post by lads on 2011-12-27
Hello everyone,

I've been looking for a decent dark theme for Unity, but they seem quite scant. Here's what I found so far:

[LIST]
[*][Plastiq]("http://www.upubuntu.com/2011/12/plastiq-amazing-gtk3-dark-theme-for.html") - not a real dark theme, leaves a lot of stuff with white/light backgrounds.
[*][Elegant-Arch]("http://www.upubuntu.com/2011/12/elegant-arch-elegant-gtk3-dark-theme.html") - looks very pretty in snapshots but it doesn't work, you get an horrible white theme.
[*][Malys-revolt2]("http://www.upubuntu.com/2011/12/malys-revolt2-amazing-dark-gtk-3-theme.html") - works in general, but a few minor issues reduce usability.
[/LIST]

Are there any other GTK3 dark themes that work? Thanks.

---

### Post by Frogs Hair on 2011-12-27
Gnomish-Dark
AdwaitaWolfe AllDark
Blapple

---

### Post by lads on 2011-12-28
> **Frogs Hair said:**
> Gnomish-Dark
AdwaitaWolfe AllDark
Blapple

Hi Frogs Hair. I appreciate your answer but I'm looking for themes for Unity, not for Gnome.

---

### Post by Frogs Hair on 2011-12-28
> **lads said:**
> Hi Frogs Hair. I appreciate your answer but I'm looking for themes for Unity, not for Gnome.

Those themes will work in Unity also as most GTK 3  themes . There are a few Unity specific GTK 3  themes at Gnome look . Ubuntu art had absolutely zero GTK 3 themes the last time I looked .

Many of the GTK 3 themes include  GTK 2 and Metacity inside the folder . Both Unity and the Gnome Shell run on top of Gnome 3 .

---

### Post by lads on 2011-12-29
Ok that's nice. How do I install one of those themes on Unity? I've tried before but it didn't work so I thought only Unity themes could be used. 

Thanks.

---

### Post by Frogs Hair on 2011-12-29
[http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml)

---

### Post by lads on 2011-12-30
> **Frogs Hair said:**
> [http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml)

Ok this is easy enough. Problem is, no Gnome GTK3 theme renders like it is presented in the snapshots. I'm realy fond of Atolm, but it only works with a few applications. It neither works with NetBeans or Eclipse, though does a good job of messing up those.

Anyway thanks for the reply. I guess we'll just to have to wait till someone at Canonical decides to spare our eyes.

---

### Post by cbowman57 on 2011-12-30
> **lads said:**
> Ok this is easy enough. Problem is, no Gnome GTK3 theme renders like it is presented in the snapshots. I'm realy fond of Atolm, but it only works with a few applications. It neither works with NetBeans or Eclipse, though does a good job of messing up those.

Anyway thanks for the reply. I guess we'll just to have to wait till someone at Canonical decides to spare our eyes.

Sounds like you might be missing the correct gtk3-engine-unico, alternatively there used to be a dark adwaita option if you poke around in the themes folder.  I think all you need to do to use it is rename gtk-dark.css to gtk.css, it looks real good with the Atolm-gtk windows theme.

You might also just want to use the Atolm-gtk package.

Also, if you poke around in the Unity theme of one you downloaded you may discover that modifying one of those is fairly simple, I don't use Unity so I haven't explored that.

---

### Post by lads on 2012-01-02
Hi cbowman,

> **cbowman57 said:**
> Sounds like you might be missing the correct gtk3-engine-unico,

```
$ sudo apt-get install gtk3-engines-unico
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk3-engines-unico is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```

> **cbowman57 said:**
> alternatively there used to be a dark adwaita option if you poke around in the themes folder.  I think all you need to do to use it is rename gtk-dark.css to gtk.css, it looks real good with the Atolm-gtk windows theme.

I replaced the css files as you suggested, but it only affects Nautilus, all other programs are rendered with a light gray background on menus and panels. The good thing is that doing this doesn't screw up NetBeans or Eclipse.

> **cbowman57 said:**
> You might also just want to use the Atolm-gtk package.

```
$ sudo apt-get install atolm-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package atolm-gtk

```

> **cbowman57 said:**
> Also, if you poke around in the Unity theme of one you downloaded you may discover that modifying one of those is fairly simple, I don't use Unity so I haven't explored that.

I understand I could make a theme on my own. But before Unity it was fairly straight forward to add new themes that actually worked. More than that, back then Ubuntu shipped with a dark theme that you could use by simply selecting it, without needing any tinkering.

---

