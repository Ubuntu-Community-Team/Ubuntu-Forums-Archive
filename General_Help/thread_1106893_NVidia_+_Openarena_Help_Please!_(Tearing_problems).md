---
title: "NVidia + Openarena Help Please! (Tearing problems)"
date: 2009-03-26
forum: General Help
---

### Post by TheExplorer on 2009-03-26
First things first: I'm running Intrepid Ibex and always having the latest stable NVidia driver installed for my GeForce 7600 GT on a TFT Monitor LG "19.
Nevertheless, I'm having that ugly tearing while running Openarena. I've googled out really nothing about that problem... There are some tips, in NVidia driver Appendix help file as well, but that doesn't actually help. I'm loosing my nerve actually. I've enabled all the settings concerning syncing (Sync to VBlank, TripleBuffer in xorg.conf etc etc.) but all in vain... I have no Compiz running if that can help you sort things out. No effects, just a clean working system. No tweaks made to it also.
There are no problems in Widoze btw. I have enabled an option to Force Vertical Sync in applications.

COULD PLEASE SOMEONE HELP ME? PRETTY PLEASE!

---

### Post by TheExplorer on 2009-03-26
bump :(

---

### Post by skymera on 2009-03-26
Try forcing vSync using Nvidia Settings.

What driver is installed?
How did you install it?

---

### Post by TheExplorer on 2009-03-26
Well, I said I've enabled all the settings concerning syncing, even Triple Buffering in xorg.conf as referenced in the NVidia Driver Appendix Help file.

I don't know what it is.

The driver is installed manually, the standard way:

1) Ctrl+Alt+F1
2) stop gdm
3) uninstall the previous driver with sudo
4) become root
5) sh NVIDIA-Linux-x86-180.41-pkg1.run (compile it myself without downloading the headers 'cause I have them)
6) start gdm

That is all. The standard way, nothing special.

OpenGL games just don't run smooth as they do in Windows.

[B] Could any of you who play Openarena tell me if you have got tearing or not?


[/B]

---

### Post by TheExplorer on 2009-03-26
bump please...

---

### Post by Slim Odds on 2009-03-26
Dude,   ease up on the bumps.....

---

### Post by TheExplorer on 2009-03-26
Otherwise what? :popcorn:

---

### Post by overdrank on 2009-03-26
> **TheExplorer said:**
> Otherwise what? :popcorn:

It is not polite to bump so quickly. Have you tried any of the other nvidia drivers?

---

### Post by TheExplorer on 2009-03-26
Yes. Stable, Betas, Prereleases, everything. I'm actually waiting for someone who fixed this. Sorry for bumping then if it's not polite.

---

### Post by skymera on 2009-03-27
ok i found the best way to do drivers in to use Envy

```
 sudo apt-get install envyng-core 
```

```
 sudo envyng -t 
```

Choose uninstall/install Nvidia.

Worked for me since Ubuntu 7.04

---

### Post by TheExplorer on 2009-04-22
You simply do not understand that there is no difference between Envy and manual installation, dude. Don't offer me this tool 'cause I do the same with my own hands.
The problem is that NVidia hasn't implemented that yet in Linux.
There IS STILL tearing in OpenGL apps and games.

---

