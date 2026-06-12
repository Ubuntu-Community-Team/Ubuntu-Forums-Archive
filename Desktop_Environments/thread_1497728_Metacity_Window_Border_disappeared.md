---
title: "Metacity Window Border disappeared?"
date: 2010-05-30
forum: Desktop Environments
---

### Post by PsychoDevon on 2010-05-30
I recently installed KDE on my Ubuntu setup to try kubuntu by installing the kubuntu-desktop package.

I decided I didn't enjoy KDE as much as GNOME, so I went back into GNOME and uninstalled the kubuntu-desktop package via Synaptic.
That didn't remove ANY of the stuff that it brought in, so I searched for the keywords "kubuntu" and "kde" and uninstalled all packages but one (libdecoration0) to get rid of all the KDE-mess.

Now, after logging back in...THERE IS NO WINDOW BORDER. AT ALL.

I know this happened due to uninstalling a package, but what package would that be? Please help.

---

### Post by dv3500ea on 2010-05-31
Try reinstalling kubuntu-desktop, then uninstalling kubuntu-desktop, then running ```
sudo apt-get autoremove
``` in a terminal

---

