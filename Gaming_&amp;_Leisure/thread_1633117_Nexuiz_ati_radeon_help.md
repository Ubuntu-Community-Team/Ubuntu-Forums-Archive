---
title: "Nexuiz ati radeon help"
date: 2010-11-28
forum: Gaming &amp; Leisure
---

### Post by Anomy on 2010-11-28
I'm trying to play nexuiz

Loading csprogs.dat
server detected csqc progs file "csprogs.dat" with size 408476 and crc 61283
Compressing csprogs.dat
Deflated: 71.6524%
drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.

I have no idea what's going on, except that it's likely something to do with my ATI Radeon graphics card. I can load the game, but when I try to load a map, it just disappears.

---

### Post by handy on 2010-11-28
Which ATi GPU are you using?

Nexuiz is much more difficult than games that use one of the Quake engines.

If you are using an old enough card then you will be stuck with the FOSS drivers that come with your Ubuntu install (which are so much better than they were a year ago you wouldn't believe it. :)).

If your card is young enough then you will be able to install the "Catalyst" proprietary driver stack for your card, which isn't perfect, but it does still offer faster 3D than the FOSS drivers do.

---

### Post by Anomy on 2010-11-28
*-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc

---

### Post by handy on 2010-11-29
> **Anomy said:**
> *-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc

You can't use the Catalyst drivers, only those from the FOSS Radeon stack, which you would have installed by default from Ubuntu.

You could try a later kernel & using the xorg-edgers PPA, repo, which may give you a slight performance improvement. See the how-to under "Ubuntu Stuff" in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

Your GPU is not really suited to gaming (& Nexuiz uses a tough on GPUs 3D engine) as per this link:

[http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html](http://www.notebookcheck.net/ATI-Radeon-Xpress-200M.2175.0.html)

---

### Post by Melcar on 2010-11-29
I got a RS480 here (also a Xpress 200M chip).  The latest Nexuiz does work, but incredibly slow (even at 800x600 on low details); 20fps max, though for most of the game I get 5-10fps.  Mind you I never tried the game with the stock open source drivers Ubuntu comes with, since the first thing I always do is install a new kernel and use the xorg-edgers ppa.

---

### Post by mastablasta on 2010-11-30
it's because these kind of computers are not really ment for gaming. ;-)

---

### Post by Melcar on 2010-11-30
Last time I tried Nexuiz with that chip under Windows, it actually ended up being playable; same settings, but was able to get upwards of 20fps.  Mind you that was a long time ago and on an older Nexuiz build.  Last time I checked, Mesa was around 50% slower than fglrx.  People say Gallium is a bit faster, so I don´t know (probably no more than 5-10% though).
This chip is like a slightly slower Radeon 9600.  I used to be able to play ToEE, Vampire Bloodlines, and Deus Ex (somewhat graphically demanding games in those times) on that 200M under Windows.  The driver is simply too slow right now, which makes small chips like the one discussed here terribly inadequate for most 3D.

---

### Post by handy on 2010-12-01
I previously made the suggestion (& gave a link to the how-to) that using a later kernel & the xorg-edgers PPA might give a slight increase in speed. (How much of an increase I don't know?)

The only way to find out is do it. It isn't hard & it is easy to undo.

Giving the newer Gallium driver stack may very well also be useful, though I don't at this moment have how-to to point to.

If anyone does, please point us to it & I'll add it to my OP in this this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by Melcar on 2010-12-01
With the r300g driver (Gallium3D) you get OpenGL2.1 compared to OpenGL1.5 with the "classic" drivers (what Ubuntu loads by default).  Granted, GLSL (what most 3D intensive Linux games use for eye candy) is a still bit flaky and does not work that well on some games, but overall you get better 3D support (WINE actually works now).  Performance wise, Gallium3D is a bit faster compared to classic Mesa drivers too:

[http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1]("http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1")

Still, these drivers are incredibly slow compared to AMD´s own drivers.  This performance gap is very noticeable on small chips like a 200M.

[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_q410&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_r600g_q410&num=1")

Gallium3D on these older chips (r5xx and older) is rather stable and there is no reason not to use it.  Installation, as pointed out earlier, is very easy in Ubuntu thanks to the ppa.

---

### Post by handy on 2010-12-01
Don't you need to do a little editing of at least one config file to be able to use Gallium?

I'm pretty sure that you do when using Arch.

---

### Post by Melcar on 2010-12-01
For r300g in Ubuntu you don´t.  If you use the xorg-edgers ppa, that´s the default driver it installs (they don´t package r300c anymore).  For r600g you do need to configure some files.

---

### Post by handy on 2010-12-02
> **Melcar said:**
> For r300g in Ubuntu you don´t.  If you use the xorg-edgers ppa, that´s the default driver it installs (they don´t package r300c anymore).  For r600g you do need to configure some files.

Can you point me to some info' on that please?

---

### Post by Melcar on 2010-12-02
It´s specified in the ppa intro/instructions:

> - r300g is now the only shipped driver and is in libgl1-mesa-dri...

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by handy on 2010-12-02
So you don't have to switch an environment variable or anything?

---

### Post by Melcar on 2010-12-03
Nope.  Provided you have a r300g compatible chip (r5xx and earlier), you only need to update your packages with the ppa.

---

### Post by handy on 2010-12-03
In Arch you have to change an environment variable. Though it gives you the ability to run both classic & Gallium on the machine & choose which you want to use if one is more suitable than the other for a given task.

---

