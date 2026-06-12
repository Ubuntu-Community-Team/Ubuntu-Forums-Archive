---
title: "Unable to get compiz to work in Kubuntu 8.10"
date: 2009-03-14
forum: Desktop Environments
---

### Post by nachoparker on 2009-03-14
Hello,

After a long day of reading howtos and tutorials I haven't been able to do it.

I have and AMD64 Dual Core @ 1.6GHz, running Kubuntu 8.10 64bits. I have an ATI Mobility Radeon X1600 with the propietary drivers installed.

I have the compiz, compiz manager and emerald packages installed, but

*The settings in the manager just are not saved. Go back to their default values when I close and open it.

*When I try "compiz --replace &" I get no window frames and no effects at all. It is just not working.

*If I set it in the Session Manager as default, KDM does not start 

I just ran out of resources... Please, I need some help!!

---

### Post by nachoparker on 2009-03-14
I have also tried "emerald --replace &"
"
EDIT: Using "Desktop Effects" and restarting I managed to make it begin to work somehow. I already got some effects, like windows transitions, minimize, wall desktop... but still unable to change the configuration with compizconfig-settings manager, so no wobbling, no cube...

I am getting closer...

---

### Post by txcrackers on 2009-03-14
If you're running KDE 4, don't use Compiz. KDE has most of the golly-gee-whiz eye-candy built into it. Trying to force it to use Compiz will usually be an exercise in frustration.

---

### Post by nachoparker on 2009-03-14
Mmmm, so you think that maybe the problem resides in KDE 4? That would narrow the causes (or let me rest in peace incidentally).

I've seen videos KDE 4 with Compiz, that is why I am trying it. I really like this new KDE, but I miss Compiz (the cube!!)

Thx mate!

---

### Post by Zorael on 2009-03-14
Hmm, I don't remember having any particular issues getting Compiz to work. What about error output? Do you enter those commands in a terminal or from a run box?

```
$ compiz --replace &
```

---

### Post by syms on 2009-03-14
ensure that all compiz plugins are installed (something like compiz-plugins-main)

---

### Post by jacksaff on 2009-03-14
KDEs own window manager has a cube, wobbly windows, fancy switchers etc already. Give it a try.

---

### Post by nachoparker on 2009-03-15
Hi, thanks for your replies.

I actually like the KDE4 effects, but I miss the cube and some other things. KDE4 does not have the cube anymore (apparently they took it out).

I have executed "compiz --replace" from the console and using "Desktop Effects". It runs, but the cube and other effects do not work, and I cannot change any configuration in the compiz settings manager (not even disable the things that currently work). All changes are ignored and discarded.

In the console I get the error "(core) Warn: unable to parse XML file from file core.xml", and the graphics server hangs.

My packages... 

compiz
python-compizconfig
compizconfig-settings-manager
compiz-fusion-bcop
compiz-plugins
compiz-wrapper
desktop-effects-kde
compiz-core
compiz-gnome
compiz-kde
(emerald packages)
libdecoration0
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
fusion-icon
simple-ccsm
compizconfig-backend-gconf
combizconfig-backend-kconfig
compiz-fusion-pluggins-unsuported

Any hint?

---

### Post by syms on 2009-03-22
daradib wrote:
> compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
To solve this problem, you can do the following:

Uninstall Compiz

sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
then

sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
Put this whole string in terminal, if it fails remove the filenames that it fails on and run it again until it works.

Then follow this howto ([http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)) to install a backported "stable" compiz from Gutsy.

Read the howto and do the setup stuff at the end carefully where he covers the window frame problem.

Taken from the following post on Ubuntu Forums ([http://ubuntuforums.org/showpost.php?p=3317998&postcount=32](http://ubuntuforums.org/showpost.php?p=3317998&postcount=32))

---

### Post by nachoparker on 2009-03-22
Thanks again for your answers.

I had already came across that article. I tried again, step by step and still get the "unable to parse core.xml" message, and still hangs when I type "compiz --replace", "--ignore-desktop..." etc...

Looks like won't work on my Kubuntu 8.10

---

### Post by txcrackers on 2009-03-23
KDE 4 certainly **does** have the cube desktop switcher.

System Settings -> Desktop -> Desktop Effects,select *Enable desktop effects*. Then select the "A_l_l Effects" tab and there's a **lot** of eye-candy options in there... including the cube.

---

### Post by nachoparker on 2009-03-23
Not my KDE 4 mate, I read that it was removed in the updates because it was not fully stable, may be you did not update yours.

Also since my last update the windows flip and cover switch effects stopped working (but I can still see the checkboxes). I never got all the effects working anyway, it looks like I will have to wait for a more mature version.

The cube does not appear at all, is not that it does not work, but I am positive that it will come back.

thanks though!

---

