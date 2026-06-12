---
title: "upgrade errors"
date: 2005-06-12
forum: Desktop Environments
---

### Post by vaskark on 2005-06-12
I'm trying to update some packages and keep getting this error:

 > The following packages have unmet dependencies:
  mozilla-firefox-gnome-support: Depends: firefox-gnome-support but it is not installed 

I'm also running into this one a lot:

 > The following packages have unmet dependencies:
  realplayer: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

Any ideas?

---

### Post by Xian on 2005-06-12
Sounds like a issue in your sources.list. 
Do you have the marillat repos enabled?

They can cause some havoc with certain packages.

Edit: Yeah, now that I think of it I do recall hearing that '2.3.2.ds1' pkg error before with marillat. Open Synaptic and goto Status > Installed (Local or Obsolete), then look for any pkgs in that section that resemble this. I would try downgrading them to the default Ubuntu versions and see if that helps.

---

