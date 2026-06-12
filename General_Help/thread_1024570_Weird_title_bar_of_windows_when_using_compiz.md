---
title: "Weird title bar of windows when using compiz"
date: 2008-12-29
forum: General Help
---

### Post by Scarlath on 2008-12-29
Hello!

I just installed my  graphics drivers, activated compiz and so on and I believe windows decorating is messing up or something because it looks really weird. However, when I turn windows decorating off (in the advanced settings thing) my minimize/maximize/close buttons disappear completely. 

I attached a screenshot so you can see exactly what it looks like. It seems to happen when I hover my mouse over it and when another window is in front of another one (the one behind will do this).

Also, could someone explain how the compiz-icon works? If I for instance need to disable it (Compiz, that is) as it's causing problem for another program, what do I do?

Thanks!

---

### Post by ajgreeny on 2008-12-29
I use the compiz-switch which is available from forlong's webpage here.  One click allows you to switch compiz on and then off.
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)  (This now not working - see below)
I have just tried it and can not get into the page so it may have moved or be down at the moment.  Try again later if needed, or do a google search for compiz-switch

EDIT:  The webpage address above has changed to 
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by Scarlath on 2008-12-29
> **ajgreeny said:**
> I use the compiz-switch which is available from forlong's webpage here.  One click allows you to switch compiz on and then off.
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)  (This now not working - see below)
I have just tried it and can not get into the page so it may have moved or be down at the moment.  Try again later if needed, or do a google search for compiz-switch

EDIT:  The webpage address above has changed to 
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Thanks, might try that later. 

You dont happen to have any idea about the main problem though? :D

---

### Post by ajgreeny on 2008-12-29
Sorry, but I think it is simply an incompatibility between compiz, or at least a combination of compiz plugins,  and certain hardware.  I suspect it may be possible to get a plugin combination that will allow you to use compiz to a degree, without loosing all your window decorations.  You can also try using the *compizconfig-settings-manager* to ensure that *Window Decoration* is enabled, though you say that removes the Close, Minimise and Maximise buttons completely.

Perhaps also worth looking at emerald along with various themes for emerald, that you can download and use.  They seem to be more compatible with compiz and are very good looking as well.  You can get emerald from the repos and various themes from lots of places.  Google for *emerald themes* and I'm sure you'll find something.

---

### Post by Usufruct on 2008-12-29
> **Scarlath said:**
> Hello!

I just installed my  graphics drivers, activated compiz and so on and I believe windows decorating is messing up or something because it looks really weird. However, when I turn windows decorating off (in the advanced settings thing) my minimize/maximize/close buttons disappear completely.

And... I'm guessing they were nVidia drivers? ;)

This is a bug in the nVidia driver that has been fixed in recent beta releases, beginning with 180.06.  You can download the most recent beta if you feel up to it, version 180.17, for [x86]("http://www.nvidia.com/object/linux_display_ia32_180.17.html") or [AMD64/EM64T]("http://www.nvidia.com/object/linux_display_amd64_180.17.html").  The installation is easy:

1. Stop gnome:

```
sudo /etc/init.d/gdm stop
```

2. Install the driver (it will build a kernel for itself):

```
sudo sh NVIDIA-Linux-x86_64-180.17-pkg2.run
```

3. Reboot, or re-start gnome:

```
sudo /etc/init.d/gdm start
```

The other option is to wait for nVidia to release the driver.  Cheers!


Edit: And OT, your username isn't a reference to a Brian Jaques novel, is it?

---

### Post by Scarlath on 2008-12-29
> **ajgreeny said:**
> Sorry, but I think it is simply an incompatibility between compiz, or at least a combination of compiz plugins,  and certain hardware.  I suspect it may be possible to get a plugin combination that will allow you to use compiz to a degree, without loosing all your window decorations.  You can also try using the *compizconfig-settings-manager* to ensure that *Window Decoration* is enabled, though you say that removes the Close, Minimise and Maximise buttons completely.

No, no. It's when I **disable** "Window Decorations" that bar with the close-button and everything dissapears, it's really weird. When it's enabled (not sure if it has anything to do with it though) the bar flickers when I hover over it back and fourth with the mouse and so on.

Are there perhaps some settings I can tweak?

> **Usufruct said:**
> And... I'm guessing they were nVidia drivers? ;)

Yup. Chose the recommended one, I believe it was called "177" (had three options for nVIDIA drivers in the proprietary driver manager, cant remember which ones exactly it was though). Was that a poor choice perhaps?

> **Usufruct said:**
> This is a bug in the nVidia driver that has been fixed in recent beta releases, beginning with 180.06.  You can download the most recent beta if you feel up to it, version 180.17...

Ugh, I dont really like betas. :(

> **Usufruct said:**
> The other option is to wait for nVidia to release the driver.  Cheers!

Is there any (estimated) release date for that?


It's not really that big of a deal, I can live without Compiz and all it's flashy-ness. It sure does make things look cool though x)




> **Usufruct said:**
> Edit: And OT, your username isn't a reference to a Brian Jaques novel, is it?

Indeed it is, or well... I read the books a whole lot of years ago. Thought the name was cool and my regular usernames were already taken on this forum, remembered this one as was like "Why not?" :p

Thanks for the answers guys!

---

### Post by jessecollins on 2009-03-05
I've been having the same problem.  I figured this had to be a bug with the driver.

You can get the 180 driver via Synaptic.  Here are the steps:

1) Go to Synaptic and install nvidia-180-kernel-source & nvidia-180-modaliases. Note: This will uninstall 177.
Or you can just run the following in the console:
```

sudo apt-get install nvidia-180-kernel-source
sudo apt-get install nvidia-180-modaliases

```
2) Reboot. (At least I had to before I saw 180 in the list of restricted drivers.)
3) Check out the restricted drivers (System -> Administration -> Hardware Drivers) and you should now see 180. ;)

Jesse

---

### Post by mollylilb on 2011-01-15
> **Scarlath said:**
> Hello!I just installed my graphics drivers, activated compiz and so on and I believe windows decorating is messing up or something because it looks really weird. However, when I turn windows decorating off (in the advanced settings thing) my minimize/maximize/close buttons disappear completely. I [[COLOR=#000000]attached[/COLOR]](http://www.itposts.net/pt/cell-phones/sony-ericsson-m600i-one-gadget-for-various-tasks.html) a screenshot so you can see exactly what it looks like. It seems to happen when I hover my mouse over it and when another window is in front of another one (the one behind will do this).Also, could someone explain how the compiz-icon works? If I for instance need to disable it (Compiz, that is) as it's causing problem for another program, what do I do?Thanks!Something error occurs when opening the link, Is the link invalid?

---

