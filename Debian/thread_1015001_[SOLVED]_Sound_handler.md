---
title: "[SOLVED] Sound handler"
date: 2008-12-18
forum: Debian
---

### Post by Izek on 2008-12-18
Does Debian allow one to choose a sound handler before any sound can be played? For example: Pulseaudio or esound.

---

### Post by gettinoriginal on 2008-12-18
If you have pulse audio installed, then you can go to System > Pref > Sound > Devices and set pulse as the default.  Try this how to:  :p

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Izek on 2008-12-18
> **gettinoriginal said:**
> If you have pulse audio installed, then you can go to System > Pref > Sound > Devices and set pulse as the default.  Try this how to:  :p

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Not really what I was looking for. I asked whether or not Debian installs pulseaudio by default or can I choose a sound handler.

---

### Post by p_quarles on 2008-12-18
> **Izek said:**
> Not really what I was looking for. I asked whether or not Debian installs pulseaudio by default or can I choose a sound handler.
Debian's "defaults" are not that simple. It ranges from the net install CD (which installs nothing by default) to a full installation, which varies further based on which options you choose. 

But to answer your question, yes, you have the option of using whatever Linux sound software you desire.

---

### Post by Izek on 2008-12-18
So if I choose the net installation, I can choose many things to install myself because it doesn't choose anything by default.

But with a full installation there will be a choice prompt for me to choose a sound handler? If so, it will show that esound is selectable?

I really don't like pulseaudio because it takes up cpu/etc. when running totem.

---

### Post by p_quarles on 2008-12-18
> **Izek said:**
> But with a full installation there will be a choice prompt for me to choose a sound handler? If so, it will show that esound is selectable?
I can't say that there isn't such a prompt, because I've never done a full installation, but I really doubt there is. The install-helpers generally allow you to select things like which db server and which desktop environment -- it doesn't go into the kind of detail your looking for. 

> I really don't like pulseaudio because it takes up cpu/etc. when running totem.
You don't have to use it in any distro. To me, reconfiguring an existing setup to run how you want it is a lot easier than installing a new distro from scratch.

---

### Post by Izek on 2008-12-18
Thanks, when jaunty comes out, I may try to do that. Uninstall pulseaudio and install esound.

---

