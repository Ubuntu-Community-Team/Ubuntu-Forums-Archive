---
title: "Installing Kubuntu on a Ubuntu Machine"
date: 2006-08-10
forum: Desktop Environments
---

### Post by cobbweb on 2006-08-10
Hi 
  I would like ot install KUbuntu on my machine but still have the option to change the session to Ubuntu. Is there anyway to do this? I would like to try both out. Is there a command for this? Thanks, 
 
Cobbweb

---

### Post by ardchoille on 2006-08-10
```

sudo apt-get install kubuntu-desktop

```

That will get you the kde desktop. You can switch from gnome to kde by logging out, choosing "Options" at the gdm screen and choosing the option to log into.

---

### Post by Ramses de Norre on 2006-08-10
```
sudo aptitude install kubuntu-dekstop
```

You can then choose which one to use each session on the login screen.

EDIT: too late =)

---

### Post by ardchoille on 2006-08-10
> **Ramses de Norre said:**
> ```
sudo aptitude install kubuntu-dekstop
```

You can then choose which one to use each session on the login screen.

EDIT: too late =)

Actually, using aptitude, the way you suggested, is a better option when installing kubuntu-desktop. That way, it is much easier to uninstall all of those packages should the user decide they don't like kde.

---

### Post by petersjm on 2006-08-10
I never knew it was as easy as a 100Mb download! Kewl! But, um... if you install kubuntu-desktop and all its dependencies, login using KDE, log out, log back in using Gnome, will the desktop be identical (I mean, launchers on the panel etc) to when you last logged in with Gnome?

---

### Post by Ramses de Norre on 2006-08-10
Absolutely, there will only be a bunch more applications in your gnome menu ;)

---

### Post by ardchoille on 2006-08-10
> **petersjm said:**
> I never knew it was as easy as a 100Mb download! Kewl! But, um... if you install kubuntu-desktop and all its dependencies, login using KDE, log out, log back in using Gnome, will the desktop be identical (I mean, launchers on the panel etc) to when you last logged in with Gnome?

Your menus will have extra items (kde items) but the rest of gnome should be the same as when you left gnome last. At least, that's the way it was for me.

---

### Post by vbeav99 on 2006-08-10
On a somewhat related note, is it possible to have xgl and compiz installed on one version of gnome and then have one that's without it? (don't know how to state it better)
I installed xgl and compiz about a month ago and remember some things not being perfect so I disabled it somehow (I don't think I removed it completely, sorry if it's unclear pretty new with this Linux thing).

Basically, I want to be able to choose to log into Gnome with regular windows manager or gnome with xgl and compiz.

Thanks

---

### Post by petersjm on 2006-08-10
> **ardchoille said:**
> Your menus will have extra items (kde items) but the rest of gnome should be the same as when you left gnome last. At least, that's the way it was for me.

Thanks, ardchoille and Ramses.

---

### Post by Ramses de Norre on 2006-08-10
> **vbeav99 said:**
> On a somewhat related note, is it possible to have xgl and compiz installed on one version of gnome and then have one that's without it? (don't know how to state it better)
I installed xgl and compiz about a month ago and remember some things not being perfect so I disabled it somehow (I don't think I removed it completely, sorry if it's unclear pretty new with this Linux thing).

Basically, I want to be able to choose to log into Gnome with regular windows manager or gnome with xgl and compiz.

Thanks
I don't use xgl/compiz myself (because I don't use gnome or kde) but my neighbour has it and he's able to click a button and select xgl/compiz or metacity. The whole thing can change of window manager with all apps open, this seems a good solution to your problem but I don't know how to accomplish it.

---

