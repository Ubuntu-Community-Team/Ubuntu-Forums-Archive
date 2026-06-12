---
title: "fcron forces uninstall of ubuntu-desktop, etc. Help!"
date: 2008-12-26
forum: General Help
---

### Post by quixote on 2008-12-26
Fcron sounds great, but when I try to install it, I get a message about uninstalling anacron, gnome-schedule, ubuntu-desktop, kubuntu-desktop, and kubuntu-kde4-desktop. 

Fcron replaces anacron, so that makes some sense.  But a few months ago, some other package wanted to remove ubuntu-desktop and I had annoying problems with gnome-desktop, as I recall. It wasn't easy recovering, either.  I'm not sure what gnome-scheduler does, but it sounds like it might be important if it's scheduling things for the OS, not me :) .  I'm not using kde right now, so I could live without those.

This behavior is listed as [bug #59893]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/59893") almost 2 years ago and was supposedly fixed.  I'm running Hardy and getting the same error.  Is this really a bug?  Is there any workaround?

I gather ubuntu-desktop is a metapackage one supposedly can live without, but I also gather it's necessary for easy updating, so I'd rather not live without it.

What's the best thing for me to do?

Thanks for any help you can give me!

---

### Post by dcstar on 2008-12-27
> **quixote said:**
> Fcron sounds great, but when I try to install it, I get a message about uninstalling anacron, gnome-schedule, ubuntu-desktop, kubuntu-desktop, and kubuntu-kde4-desktop. 

Fcron replaces anacron, so that makes some sense.  But a few months ago, some other package wanted to remove ubuntu-desktop and I had annoying problems with gnome-desktop, as I recall. It wasn't easy recovering, either.  I'm not sure what gnome-scheduler does, but it sounds like it might be important if it's scheduling things for the OS, not me :) .  I'm not using kde right now, so I could live without those.

This behavior is listed as [bug #59893]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/59893") almost 2 years ago and was supposedly fixed.  I'm running Hardy and getting the same error.  Is this really a bug?  Is there any workaround?

I gather ubuntu-desktop is a metapackage one supposedly can live without, but I also gather it's necessary for easy updating, so I'd rather not live without it.

What's the best thing for me to do?

Thanks for any help you can give me!

If you want to know about packages simply use Synaptic and look at the dependencies of the package, gnome-scheduler depends on anacron so it will be removed if you remove anacron.

All the others are meta-packages (and all probably have anacron in them). If you don't want to keep all the included components then you have to remove the meta-packages, otherwise they are no longer as the developers intend, so there is no "bug".

---

### Post by quixote on 2008-12-27
> If you don't want to keep all the included components then you have to remove the meta-packages

Okay, so it's not a bug.  It's not exactly a feature either....

Seriously, that's exactly my problem:  I don't know what else is in the metapackages.  What's going to happen when I uninstall all that?  I'd like to have fcron, but not at the price of losing I-don't-know-what.  

As I say, when I ran into this a few months ago, I remember having very annoying problems, although it's too long ago for me to remember exactly what they were.  I suddenly lost gnome-panel?  ??  It was something that was not minor, at least to me.  And I seem to remember losing a bunch of settings when I reinstalled ubuntu-desktop. I think, also, I may have still been on Feisty at the time.  Maybe things are different under Hardy?

So I guess my question becomes what's the best way to try fcron, but be able to backtrack if things don't work without losing stuff along the way?  For instance, I've heard that using aptitude instead of apt can make it easier to get back to previous settings after an uninstall.  Would that apply here?

---

