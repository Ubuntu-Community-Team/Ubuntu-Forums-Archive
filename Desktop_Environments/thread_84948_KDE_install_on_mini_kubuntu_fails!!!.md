---
title: "KDE install on mini kubuntu: fails!!!"
date: 2005-11-01
forum: Desktop Environments
---

### Post by luxidio on 2005-11-01
Hi all,

I'm trying to install a mini kubuntu on my pc to fit with my 1Gb disk

as follow:

- installed: kubuntu 5.04 server expert 
- updated all pkg with aptitude
- installed xserver with: apt-get install xserver-xorg
- configured X with: sudo dpkg-reconfigure xserver-xorg

kde starts (it seems following the boot log)

the kde login screen appear

but any attempt to log in gives (as "user" or also as root):

" Xsession: unable to start X session --- no "home/user/.xsession" file, no "home/user/.Xsession" file, no session managers, and no terminal emulators founds; aborting"

any idea how to solve this? or how to select the pkg installed by the full kubuntu installation?

thank you in advance

---

### Post by daller on 2005-11-24
[QUOTE=luxidio]Hi all,

I'm trying to install a mini kubuntu on my pc to fit with my 1Gb disk

as follow:

- installed: kubuntu 5.04 server expert 
- updated all pkg with aptitude
- installed xserver with: apt-get install xserver-xorg
- configured X with: sudo dpkg-reconfigure xserver-xorg

kde starts (it seems following the boot log)

the kde login screen appear

but any attempt to log in gives (as "user" or also as root):

" Xsession: unable to start X session --- no "home/user/.xsession" file, no "home/user/.Xsession" file, no session managers, and no terminal emulators founds; aborting"

any idea how to solve this? or how to select the pkg installed by the full kubuntu installation?

thank you in advance[/QUOTE]

Did you install kubuntu-desktop???

---

