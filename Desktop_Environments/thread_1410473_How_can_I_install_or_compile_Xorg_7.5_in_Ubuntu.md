---
title: "How can I install or compile Xorg 7.5 in Ubuntu?"
date: 2010-02-18
forum: Desktop Environments
---

### Post by chenxiaolong on 2010-02-18
I'm trying to compile the new Xorg 7.5 and Xserver 1.7 under Ubuntu 9.10 Karmic x64. I've tried and used numerous guides, but since they were meant for Xorg 1.5, builds were failing. The reason I want Xorg 7.5 is for the MPX support. It would be really nice to have for my school group projects. I'm already running Xorg 7.4 from the xorg-edgers PPA. Are there binary packages for Xorg 7.5? If not, how can I compile Xorg (along with dependencies)? Also, would installing Xorg from the Lucid testing repository work? 

Thanks for any help and information.

---

### Post by Nagrom_17 on 2010-02-19
I would love to know how to do this. Ive been searching for hours on how to have 2 mouse pointers on one box, mostly for fun and the only answers I've found is that its in the new Xorg 7.5 but actually getting Xorg 7.5 is proving to be a pain.

---

### Post by Hero of Time on 2010-02-20
Lucid has 7.5, so either get Lucid, or use the daunting method of adding the lucid repo to your karmic install and install 7.5 from there.
Or find a way to build the packages, but it can take a while and lots of trial and error.

---

### Post by chenxiaolong on 2010-02-20
Is there a way to download a package + dependencies? That way I can add the Lucid repo, download Xorg, and install it, and revert back to the Karmic repo.

---

### Post by Hero of Time on 2010-02-20
You can always use apt-priority to put the Karmic repo before the Lucid one. If a specific dependency is required and Karmic doesn't have it, or the wrong version, it will either pick the Lucid one automatically, or inform you of broken packages that you can fix manually by selecting the proper version to install. See the manual for apt-preferences for more information about this. I found a debian forum post that had the same idea for stable and unstable packages origin.

Quick search got me this:
```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600
```
Which looks like what I had before, replace stable, testing and unstable to the likes of karmic, karmic-updates, etc, and lucid, lucid-updates, etc. Search for more info, as grabbing this without knowing what it does or how it works is a bad idea.

---

### Post by chenxiaolong on 2010-02-20
Thanks for the info :D. I'll try that.

---

