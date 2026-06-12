---
title: "Bug? Resizing save as -dialog (Ubuntu + Blackbox)"
date: 2007-08-19
forum: Desktop Environments
---

### Post by nolla on 2007-08-19
I set up Blackbox (0.70) window manager on my ubuntu (7.04) to get some speed out of it... Otherwise it works nicely, but the save as -dialog flickers on every program (well, at least gimp, inkscape, firefox...) It seems like its getting two different set of width and goes back and forth between the two values.

Ive got no idea where to look for these settings. Newbie with linux. I tried to change couple of settings in blackboxrc (about new window alignment) with no luck.

---

### Post by RedSquirrel on 2007-08-20
This is a gtk bug. Just click "Browse for other folders". Apparently this has been fixed in the version of gtk included with gutsy.

---

### Post by nolla on 2007-08-21
Oh, good to know. Thanks.

Do you know if this problem exists in current version of Fluxbuntu?

---

### Post by RedSquirrel on 2007-08-22
> **nolla said:**
> Oh, good to know. Thanks.

No problem.

> **nolla said:**
>  Do you know if this problem exists in current version of Fluxbuntu?

Sorry, I don't know. I don't use Fluxbuntu. I prefer to setup my own custom/minimal install and build Fluxbox from SVN code.

I just looked at the Fluxbuntu website and unfortunately their forum is offline at the moment.

[bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054") would probably know.

---

### Post by nolla on 2007-08-22
Well, i tried fluxbuntu and it doesnt seem to have the bug. Going to wait for the stable release, though...

---

