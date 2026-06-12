---
title: "How do I delete ALL documentation? (need to save space)"
date: 2008-12-08
forum: General Help
---

### Post by Panarchy on 2008-12-08
Hi

How do I delete all documentation?

I'm in Synaptic Package Manager, I select everything in documentation that's checked green, 'mark for complete removal'.

When I click apply, it says that it also wants to remove synaptic, ubuntu-desktop and various other 'packages' that are required by me, obviously. For without them I wouldn't have a GUI.

So is there a way to remove all documentation without getting rid of neccessities? Such as ubuntu-desktop and synaptic?

Please reply

Thanks in advance,

Panarchy

---

### Post by oilchangeguy on 2008-12-08
> **Panarchy said:**
> Hi

How do I delete all documentation?

I'm in Synaptic Package Manager, I select everything in documentation that's checked green, 'mark for complete removal'.

When I click apply, it says that it also wants to remove synaptic, ubuntu-desktop and various other 'packages' that are required by me, obviously. For without them I wouldn't have a GUI.

So is there a way to remove all documentation without getting rid of neccessities? Such as ubuntu-desktop and synaptic?

Please reply

Thanks in advance,

Panarchy

the approx. 20,000 packages that are listed in synaptic, are not actually already there. when you select install synaptic downloads the package from the repos, via the internet. so if you remove the links, you are not saving that much space.

---

### Post by psusi on 2008-12-08
Don't remove rarian-compat.

---

### Post by Panarchy on 2008-12-08
^Tried that, and deselecting manpages, to no avail. Still wanted to remove ubuntu-desktop!

:confused:

> **oilchangeguy said:**
> the approx. 20,000 packages that are listed in synaptic, are not actually already there. when you select install synaptic downloads the package from the repos, via the internet. so if you remove the links, you are not saving that much space.

How much space would I save? I'm trying to remove everything except the GUI and a few other programs (gedit, terminal, calculator, administrative stuff and system tools stuff)...

So how can I save space?

Please reply telling me how.

Thanks in advance,

Panarchy

PS: Will remove OpenOffice and GIMP... but how much would that save me?

---

### Post by albinootje on 2008-12-08
If you really want to remove all documentation, rm -rf /usr/share/doc/*
is an option, but not a nice solution.

The package ubuntu-desktop is a meta-package. It is only important to have when you want to do a dist-upgrade.

Removing openoffice.org will at least gain you 250 Mb of space.
(Just did a : du -sh /usr/lib/openoffice/)

---

### Post by binbash on 2008-12-08
are you using localepurge to gain space?

---

### Post by Panarchy on 2008-12-08
^:confused: Don't think so! Using synaptic...

> **albinootje said:**
> If you really want to remove all documentation, rm -rf /usr/share/doc/*
is an option, but not a nice solution.

The package ubuntu-desktop is a meta-package. It is only important to have when you want to do a dist-upgrade.

Removing openoffice.org will at least gain you 250 Mb of space.
(Just did a : du -sh /usr/lib/openoffice/)

Hmm... sounds good. So I don't need the ubuntu desktop meta package?

How about these others (will edit them in in a sec)

---

### Post by Panarchy on 2008-12-08
Okay, everything is working fine when I selected everything but rarian and manpages, now I've selected them and am restarting.

Will tell how it goes

---

### Post by Panarchy on 2008-12-08
Well it seems I could boot up again, though synaptic and a few other things are missing... well doing a 

sudo apt-get install synaptic

Now, so everything should be a-OK!

Thanks for the help

Panarchy

---

### Post by fenian on 2008-12-08
the program localepurge will remove all documentation that isn't in your language,you may be able to use it to remove all documentation though I like to have man pages available so have never tried.Their are other tools for freeing up disk space (autoremove,deborphan) there is a good rundown in the last section of [this post]("http://ubuntuforums.org/showthread.php?t=898573&highlight=autoremove").

---

