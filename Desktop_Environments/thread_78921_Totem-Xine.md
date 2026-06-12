---
title: "Totem-Xine"
date: 2005-10-19
forum: Desktop Environments
---

### Post by markr on 2005-10-19
I'm trying to install Totem-Xine to see if it improves my DVD/Media file playback, but when I try to install it (via dpkg) I'm told that it confilcts with totem-gstreamer (no problem, I'll just uninstall totem-gstreame me thinks!!)

When I Synaptic to mark Totem-Gstreamer for removal,  it also tells me it will remove Rhythbox, totem and ubuntu-desktop.

Totem I can understand,  but I'm very worried about the removal of Rhythmbox and ubuntu-desktop as I can't understand why.

Does anyone have advice or recommedations on how to proceed?

Thanks

Mark.

---

### Post by wellmt on 2005-10-19
I think Ubuntu-desktop is some kind of meta-package. I *think* it can safely be removed.

Never used rythmbox but I assume it has some dependency on something in the totem-gstreamer package?

---

### Post by RAOF on 2005-10-19
Ubuntu-desktop is a metapackage - it has all of the standard ubuntu packages as dependencies, so if you install it, you'll be guaranteed to have at least a base ubuntu system.  It doesn't actually **do** anything, so having it removed is harmless(*).  

That said, why are you using dpkg?  By far the easisest way to install stuff is with synaptic (or, if you're a terminal junkie, apt-get).  They handle all of the dependency/conflict madness themselves - if you mark totem-xine for installation, synaptic will automatically mark totem-gstreamer (and only totem-gstreamer) for removal.  Unless you've built something by hand, there's no reason to stray from the synaptic/apt-get fold :)

Oh, and I see no reason why removing totem-gstreamer would remove rythmnbox.  It doesn't do that here.  Are you sure you weren't removing gstreamer itself, or something to that effect?

(*) It is a good idea to have ubuntu-desktop installed should you upgrade between releases, for example from Hoary to Breezy.  This just ensures that all of the additions and changes get installed.

---

### Post by markr on 2005-10-19
I'm using dpkg because I don't have an internet connection on the Ubuntu machine (yet, but my wireless woes are documented elsewhere).

Can you use apt-get if you have the debs on a local HDD?

---

### Post by Cathbard on 2005-10-19
Normally you'd just use dpkg like you said.
Type: man apt-cdrom
for the info on what you're asking.



{Edit} oops, you said hdd not cd didn't you...................I need a coffee

---

