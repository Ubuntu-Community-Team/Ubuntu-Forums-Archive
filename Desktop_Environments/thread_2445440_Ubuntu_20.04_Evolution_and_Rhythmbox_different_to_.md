---
title: "Ubuntu 20.04 Evolution and Rhythmbox different to OpenSuse Tumbleweed with Gnome 3.36"
date: 2020-06-14
forum: Desktop Environments
---

### Post by alyana on 2020-06-14
Hi everyone,

when comparing these two distros, I found out that Evolution and Rhythmbox have differences, although both are running under the latest Gnome desktop 3.36:


[LIST]
[*]In Ubuntu 20.04, the menu entry for backing up the Evolution settings is gone. It's only possible to restore previously saved settings. (Same applies for Evolution in Ubuntu Mate 20.04 btw, so it must be an Ubuntu thing). Using Evolution in OpenSuse Tumbleweed the menu is still there.
[*]Rhythmbox in Ubuntu 20.04 does not have a status bar anymore at all, not even the floating one like Nautilus has that is being mentioned on the Gnome website, what it should have. This status bar is present when using Rhythmbox in OpenSuse Tumbleweed.
[/LIST]

Does anybody know why the Ubuntu versions of these applications are lacking these features? Is that a bug or by purpose?

---

### Post by Yellow Pasque on 2020-06-14
Is either program installed as a snap?:
```
snap list
```

---

### Post by alyana on 2020-06-15
@Yellow Pasque
No snaps at all on the system yet. Both applications are from the focal repository. When, for example, clicking on the link in the "about" section of Rhythmbox, it leads me to the Gnome developers site, and there the features of this version are listed, and that status bar is explicitly mentioned. That's how I found out about it missing. Same for the "save settings" feature in Evolution. So I wondered why, because to me it seems that Ubuntu stripped these applications of  these features (maybe even more, I haven't compared further yet).

Just a bit strange to me, because I thought, these applications should be the same in all distros when using the same version of the application.

---

### Post by anarchy-x on 2020-06-29
Are they the same exact version numbers across distros?

Are any of the applications flatpaks?

---

