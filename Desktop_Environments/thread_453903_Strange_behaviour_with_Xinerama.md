---
title: "Strange behaviour with Xinerama"
date: 2007-05-24
forum: Desktop Environments
---

### Post by Beamerboy on 2007-05-24
Hi,

I have some strange behaviour since switching to Feisty last night.  I have done 3 fresh installs and I got the same problem each time.

My system spec is:

[INDENT]AMD64 X2 4400+ Toledo[/INDENT]
[INDENT]2GB RAM[/INDENT]
[INDENT]Dual Nvidia 6600GT 128MB SLI Graphics Cards[/INDENT]
[INDENT]Dual 19" LCD Monitors[/INDENT]

I run a single monitor on each card and don't have the SLI bridge enabled.  In order to give a single desktop across both monitors I need to use Xinerama.  This has worked fine in Dapper and Edgy but it is causing problems in Feisty.

I have nvidia-glx-new package installed and glxinfo confirms that the nvidia kernel module is working fine.  However, as soon as I enable Xinerama things start to break.  For example, I cannot open any terminal (whether it be gnome-terminal, eterm, terminal) from within Xorg.  I get a task open on the taskbar saying "Starting GTerm" (or whatever) but after about 10 seconds the task disappears from the taskbar (crashed I presume).

It is not just opening a terminal that has problems though, for example, I tried to open a file manager yesterday and the same behaviour occurred.  As soon as I disable Xinerama, everything works fine again.

Some might say "So don't use Xinerama" but that is not a viable option, without Xinerama I have 2 seperate Desktops (one on each monitor), which means I cannot drag windows from one monitor to another, if I have firefox open in one monitor, I can't launch it in the other monitor without closing the existing firefox session.  Also no chance of using XGL/AIGLX/Compiz or Beryl, as soon as I launch any desktop effects I lose my window decorations on both monitors because the window manager doesn't know how to work with 2 seperate xsessions at the same time (I presume).

As I said, I never had this problem with Edgy or Dapper, so I am not sure what is going on and wondered if anyone else has experienced similar issues with Xinerama.  I would hate to have to reinstall Edgy after spending hours doing multiple fresh installs of Feisty, but the Desktop is not workable for me under the current circumstances.

Any help appreciated

Paladine

---

### Post by Beamerboy on 2007-05-24
Hey peeps,

I managed to fix this problem now by adding the following to my xorg.conf

Section "Extensions"
        Option "Composite" "false"
EndSection

Of course this adds another problem now in that I can't use AIGLX/Compiz (not sure about XGL but I presume it will be the same problem) as it requires composite to be enabled.

It is a little frustrating considering I never had these problems in the past, having written a rather popular HOWTO for XGL+Compiz+Nvidia based on my own experiences of getting it working, seems odd that things have now changed to the point where it won't work.

Does anyone know whether this is a bug?  Why does composite need to be disabled to run "terminal" applications with Xinerama enabled?

Paladine

---

### Post by Rosenrot on 2007-05-25
also to add to this i had a similar problem to this earlier with xinerama where i had the same symptoms as the OP in addition to cloned monitors

and i also had to disable composite

in other distros and earlier versions of ubuntu i've never have had this problem

- I am using a single ATI x850XT PE

---

