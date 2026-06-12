---
title: "The big upgrade and random .debs"
date: 2005-07-30
forum: Desktop Environments
---

### Post by maruchan on 2005-07-30
Posting this here because I'm currently using Hoary....

I read that the upgrade to Breezy might be "painful" if I haven't been careful about what .debs I have installed on my machine while using Hoary. Is there a way I can be sure (now that I have installed these packages) that when I do upgrade, the upgrade will go well? 

This makes me a little nervous :)

 :-?

---

### Post by jasmuz on 2005-07-30
Wasnt you that said that "Installing unstable builds caracther" ?

If you are going to install then do so :P

---

### Post by maruchan on 2005-07-31
> Wasnt you that said that "Installing unstable builds caracther" ?

Say what? I don't recall saying that.  :|

---

### Post by bored2k on 2005-07-31
True. Some files could simply _not_ upgrade. That is Jdong's long battle with users posting custom debian packages. Let's say I make a package called "firefox1-7.deb". When I upgrade, the package manager won't be able to upgrade because the naming presents a trouble for it. That's why sometimes (Specially a couple of months ago) if you used the Backports there was a slight chance that you would not get 100% upgrade (doesn't happen anymore with backports). If you download a package like my [xmms-scrobbler](http://www.freewebs.com/bored2k/xmms-scrobbler_0.3.6-1_i386.deb) and this package enters Universe, there's a big chance you would never even know this.

---

### Post by Amaranth on 2005-07-31
[QUOTE=bored2k]True. Some files could simply _not_ upgrade. That is Jdong's long battle with users posting custom debian packages. Let's say I make a package called "firefox1-7.deb". When I upgrade, the package manager won't be able to upgrade because the naming presents a trouble for it. That's why sometimes (Specially a couple of months ago) if you used the Backports there was a slight chance that you would not get 100% upgrade (doesn't happen anymore with backports). If you download a package like my [xmms-scrobbler](http://www.freewebs.com/bored2k/xmms-scrobbler_0.3.6-1_i386.deb) and this package enters Universe, there's a big chance you would never even know this.[/QUOTE]
 Not sure if it's just Synaptic but it chooses the one in the repos over the local install if they have the same name and version. So even that shouldn't be an issue.

---

