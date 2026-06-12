---
title: "Error's building the newest Kopete"
date: 2006-03-23
forum: Desktop Environments
---

### Post by tymanthius on 2006-03-23
Ok, so I love Gaim, but it doesn't have gaim-vv rolled back into it yet.  But Kopete .12beta 2 has video support.  Yay!  

I went to dwnload the source, and untar'd to my /usr/local/src dir.  But configure complains that I don't have KDE headers.  No biggie, run Synaptic, and ask for the kdebase-dev meta package.  

It says, nope, can't have it:

kdebase-dev:
 Depends: kdelibs4-dev but it is not going to be installed


Hmmm . . . so I go tell it to install kdelibs4-dev (makes sense, right?)  Nope!

kdelibs4-dev:
  Depends: kdelibs4c2 (=4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0breezy1 is to be installed
  Depends: kdelibs-bin (=4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0breezy1 is to be installed
 Depends: libarts1-dev but it is not going to be installed


Now I'm a bit confused.  I'm not a newbie to Linux, but this is my first Debian based *nix since about 1995. 

I have Ubuntu (not Kubuntu) 5.10 loaded, with everything up to date as of 2 minutes ago.

What gives?  I'm thinking I may have updated using a diff repository at some point for some of my playing, but I'm not sure.

---

### Post by tymanthius on 2006-03-24
shameless bump

---

### Post by Sef on 2006-03-24
Have you downloaded build-essential?  If not, you can't compile.

sudo apt-get install build-essential

---

### Post by tymanthius on 2006-03-24
Yes, build essential is in, so are the packages for checkinstall (which I LOVE).  If not, I wouldn't even get configure to run I don't think.

It's a problem w/ KDE specific stuff.  I'm not a big fan of KDE, tend to prefer gnomish apps, but Kopete is doing what I want, IF I can get it to build.

---

### Post by Sef on 2006-03-24
Kopete can run under Gnome, if the KDE packages are installed.

---

### Post by tymanthius on 2006-03-24
Yes, I know.  But I use XFCE, so gnome isn't the issue.  The issue is that I can't build the LATEST beta version of Kopete b/c of some unresolved dependencies.  I just need help resolving them.

---

