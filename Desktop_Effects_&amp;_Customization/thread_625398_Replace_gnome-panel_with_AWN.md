---
title: "Replace gnome-panel with AWN"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by fbolduc on 2007-11-27
I would like to know how to completely replace gnome-panel with AWN on Ubuntu 7.10.

I have installed AWN using the instructions found on the AWN wiki at:
[http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository](http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository)

I'd like to know how to setup Gnome so that AWN start automatically.

Also, I'd like to know how to prevent gnome-panel from starting.

I've tried various things, but I did not succeed. Anybody has an idea how to accomplish this?

---

### Post by BLTicklemonster on 2007-11-27
There's another dock similar to awn, but it has the icons bounce around when you move your mouse over them. I though awn was it, and installed it, but it's not what I was thinking. 

Anyway, you have some good questions. I'd like to know how you put everything you want on the dock, as far as stuff like the log out button, network icon, etc. I guess I'll right click each icon on the gnome dock and look at them that way, or perhaps the link you have tells all this.

Okay, I got my foot in the door to keep an eye on this, and maybe ... ah, kiba. Never mind.

---

### Post by santiagoward2000 on 2007-11-28
> **fbolduc said:**
> I would like to know how to completely replace gnome-panel with AWN on Ubuntu 7.10.

I have installed AWN using the instructions found on the AWN wiki at:
[http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository](http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository)

I'd like to know how to setup Gnome so that AWN start automatically.

Also, I'd like to know how to prevent gnome-panel from starting.

I've tried various things, but I did not succeed. Anybody has an idea how to accomplish this?

HI!
Just right-click on the panel, click on customize and then on remove.

---

### Post by santiagoward2000 on 2007-11-28
> **BLTicklemonster said:**
> There's another dock similar to awn, but it has the icons bounce around when you move your mouse over them. I though awn was it, and installed it, but it's not what I was thinking. 

Anyway, you have some good questions. I'd like to know how you put everything you want on the dock, as far as stuff like the log out button, network icon, etc. I guess I'll right click each icon on the gnome dock and look at them that way, or perhaps the link you have tells all this.

Okay, I got my foot in the door to keep an eye on this, and maybe ... ah, kiba. Never mind.

I'm using Kiba and it has that bounce effect, but I know that effect is on AWN too. Perhaps all you need is to configure it...
Still, if you want to try Kiba go ahead, it's great! :guitar:

---

### Post by BLTicklemonster on 2007-11-28
lmao, now my desktop effects quit working. 

I'll stop while I'm ahead.

---

### Post by santiagoward2000 on 2007-11-28
> **BLTicklemonster said:**
> lmao, now my desktop effects quit working. 

I'll stop while I'm ahead.

Really? When did this happen? What were you doing?

---

### Post by BLTicklemonster on 2007-11-28
:) When? Last night.

What was I doing? The usual: trying to install something cool.

It happened gradually. The machine started slowing way down, then got totally unresponsive. It was like it had just eaten wedding cake or something, I mean no cooperation, it just sat there staring at me. So the instant I got some sign of life out of it, I restarted, and it decided not to get to X, not even failsafe.

I've got two versions of Gutsy going, so at least I'm okay. Thank goodness for spare hard drives :)

I'll look again tonight and see what's going on.

---

### Post by SyITec on 2007-11-29
I have the same setup. I'm running 7.10 and installed AWN from the same link you provided.

What I did was added AWN to the startup in "Sessions" under your preference menu. The command I used was "avant-window-navigator" and what ever you want to use for name and comments. When I rebooted, it launched AWN. I'm not sure if it was my install or what, but the icons slid across the screen onto the AWN bar. I hope that helps.

Do you know how to remove the panel? :)

---

### Post by BLTicklemonster on 2007-11-29
I looked around, and all I could find was where the last thing I'd done from the terminal (before trying to reconfigure from non-x) was where I'd attempted to install awn. Oh, and trying to dpkg-reconfigure /etc/X11/xorg.conf did no good. I was told that /etc/X11/xorg.conf was not installed, yet I could nano /etc/X11/xorg.conf all day long and see everything that was in it.

Seeing as how there was no real need to try to save it, I just reinstalled it. Which is great, because I can start beating my head against the network from scratch once again. Yay me.

So I'm all cool now. sorta.

---

### Post by fbolduc on 2007-11-30
> **SyITec said:**
> I have the same setup. I'm running 7.10 and installed AWN from the same link you provided.

What I did was added AWN to the startup in "Sessions" under your preference menu. The command I used was "avant-window-navigator" and what ever you want to use for name and comments. When I rebooted, it launched AWN. I'm not sure if it was my install or what, but the icons slid across the screen onto the AWN bar. I hope that helps.

Do you know how to remove the panel? :)

I did succeed at starting AWN at startup by putting it in Preference->Session.

However, I'd like to prevent gnome-panel from starting at startup, not remove my custom panel. I did remove it, but I could not get it back afterwards. I had to fix it with the following commands:

(alt-F2)
gnome-terminal


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &


To put it simply, I want to test AWN a bit before switching. I'd like to keep my old configuration at hand if I have any problem. Therefore, I'm simply looking for a way to prevent gnome-panel from starting.

---

