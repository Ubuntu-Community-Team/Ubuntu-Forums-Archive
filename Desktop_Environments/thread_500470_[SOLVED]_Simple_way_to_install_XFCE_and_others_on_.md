---
title: "[SOLVED] Simple way to install XFCE and others on Kubuntu?"
date: 2007-07-13
forum: Desktop Environments
---

### Post by kansas_plainsman on 2007-07-13
I'm running kubuntu, being a KDE fan - but sometimes I'd like to run XFCE or one of the other desktop environments.  Is there a straight-forward way to enable my system to load these other desktop environments?

---

### Post by merlinus on 2007-07-13
```

sudo aptitude update && sudo aptitude install xubuntu-desktop

```-merlin

---

### Post by pxwpxw on 2007-07-13
Or you can just install the xfce4 package, and should be able to select an xfce session at login.

---

### Post by Nythain on 2007-07-14
if you havent figured it out yet, most of the more common and popular desktop environments and window managers have packages in the ubuntu repos and are as easy to install as
sudo aptitude install <de or wm package name here>
the really popular ones (gnome, kde, xfce) have entire desktop metapackages wich will nto only install the de but a list of apps that have proven to run well with them
sudo aptitude install ubuntu-desktop (or kubuntu-desktop or xubuntu-desktop)

a search in synaptic or aptitude for the DE or WM you want to install will show weather or not its available via apt

---

### Post by reset3x on 2007-07-14
This site tells how to install some desktop environments and also how to completely uninstall them... : [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by kansas_plainsman on 2007-07-14
"sudo aptitude update && sudo aptitude install xubuntu-desktop" worked well, (I'm running xfce now with apparently no problems) but I DID get an error downloading a file or package near the end, which terminated the download session.  (I *think* it related to some xfce management software).

I am impressed by how simple ubuntu made the change - being a slackware user in the past, I'm used to getting down and dirty with configuration files and the like.  Ubuntu seems about one step away from "ready for prime time".

Great distribution, this ubuntu.

Thanks for the help and suggestions, folks.

---

