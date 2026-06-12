---
title: "Change screen resolution-Vesa driver"
date: 2009-02-27
forum: General Help
---

### Post by dwiedenfeld on 2009-02-27
I recently replaced the "nvidia" driver with "Vesa" in my xorg.conf. Now I've got a display, but it's 800x600 and pretty stretched out. In "Preferences > Screen Resolution" 800x600 and 640x480 are the only choices. How do I get a higher resolution?

Also, is there a way to restart Xorg without having to reboot?

---

### Post by Yellow Pasque on 2009-02-27
Vesa only supports standard resolutions, nothing widescreen. If you're having issues with the nvidia driver, you may want to try using "nv" or "nouveau" as an alternative until you're able to fix them.

> Also, is there a way to restart Xorg without having to reboot?
Log out. Or Ctrl+Alt+Backspace (which will log you out).

---

### Post by dwiedenfeld on 2009-02-27
> try using "nv" or "nouveau"

To use one of those instead of Vesa, do I just edit xorg.conf to replace "Vesa" with "nv" or with "nouveau"?

---

### Post by Yellow Pasque on 2009-02-27
Yes, nv should be installed by default. Nouveau is included in the Ubuntu 9.04 Jaunty repos, but would take a little work to try in older versions: [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

---

