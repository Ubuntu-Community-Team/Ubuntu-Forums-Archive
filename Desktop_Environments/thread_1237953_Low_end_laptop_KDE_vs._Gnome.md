---
title: "Low end laptop KDE vs. Gnome"
date: 2009-08-11
forum: Desktop Environments
---

### Post by fjosh on 2009-08-11
My question is basically how much more demanding (regarding hardware) are the latest versions of KDE vs. Gnome.  Is the difference negligible or drastic?  I'm curious as to how it would run on my laptop.  Simple enough.

Celeron M 1.3
768Mb RAM
Intel 82852/82855 GM/GME

---

### Post by PC_load_letter on 2009-08-12
I don't have specific general stats, but neither Gnome or KDE is a light environment, in comparison say with XFCE. On my Dell Vostro 1400 dual core Gnome takes something like 180~230MB ram on startup, while running Sidux (a Debian Sid based distro) with XFCE on the same machine consumes about 100MB of ram on startup. 

Did you try running Xubuntu live cd? Even it runs from the cd, it's quite fast, just to give you an idea. Or you could install it in a virtual machine w/ Sun's VBox. Another option is the Linux Mint XFCE edition, version 6 is available and I believe they are working on version 7 to be released soon.

If you are just looking for a lighter window manager, you may wanna look into fluxbox, or enlightenment.

---

### Post by snowpine on 2009-08-12
> **fjosh said:**
> My question is basically how much more demanding (regarding hardware) are the latest versions of KDE vs. Gnome.  Is the difference negligible or drastic?  I'm curious as to how it would run on my laptop.  Simple enough.

Celeron M 1.3
768Mb RAM
Intel 82852/82855 GM/GME

They are about equal (probably your two slowest choices), and the best way to test performance on your laptop is to try it for yourself. I have run Ubuntu/Kubuntu on far worse... :)

---

### Post by andrea000 on 2009-08-12
I have a old dell c640 laptop set up as a test computer
it only has 512 mb of ram and it runs ubuntu 9.04 gnome
desktop with compiz with no problem at all.

---

### Post by aysiu on 2009-08-12
I used to run Gnome on 1 GB of RAM and an underclocked 900 MHz Celeron processor on my old Eee PC, and it worked just fine.

With 768 MB of RAM, it should be fine. Just don't run too many applications at once.

---

### Post by stumbleUpon on 2009-08-12
I think GNOME is better. I have 9.04 on an old DELL latitude C600 laptop with 512MB RAM and 800MHz processor. No probs at all. My graphics card does not support compiz though :(

---

### Post by Zorael on 2009-08-12
Yeah, try both and see. I'd recommend you disable nepomuk (and strigi) on KDE to get rid of its overhead. GNOME has its tracker indexer too, hasn't it?

Obviously the results also depend on what applications you run. If you absolutely have to use Firefox, you'd be loading the GTK libraries into memory as soon as you launch it. In a GNOME environment they'd already be loaded, whereas in a KDE environment everything would be using Qt, so you'd suddenly have both in memory.

So given GNOME, the optimal setup would be to disable services to as large extent as possible, and then only use GTK apps. Likewise given KDE, only use Qt apps. To boot, both GNOME has Bonobo and KDE has KParts to maximize code reuse.

And consider lighter browsers like Arora or Midori instead of Firefox or Konqueror. You should get it pretty lean.

---

### Post by XubuRoxMySox on 2009-08-12
I have an old Dell Dimension with a scant 512 or RAM and Gnome ran fine on it. Kubuntu crawwwwwled along on the same computer. I just wanted a look at KDE to see what all the fuss was about, but it seemed to be much more resource hungry than Gnome was.

I have a favorite desktop environment that I use on the old Dell now because it's a shared computer used by lots of kids during the day, so it had to be familiar-looking (like KDE), but fast and lightweight on that old hardware. 

If you are majorly concerned about "weight" and speed, and want a nice "familiar-looking" desktop for your parents, give LXDE a whirl (see my sig). It installs right from Ubuntu's repos:

```
sudo apt-get install lxde
```

But you needn't be concerned that Gnome will slow down that computer. It ran nice and swiftly on my old beast.

-Robin

---

