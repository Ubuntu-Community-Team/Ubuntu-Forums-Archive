---
title: "VLC Breezy Package broken?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by mortram on 2005-11-28
I didn't have any trouble installing VLC on Hoary - the widgets were all GTK2 and the sound worked fine.

The Breezy package (gnome-vlc) doesn't seem to use GTK or output to ESD or Alsa, even when those packages are installed and I add the command to the run dialog.

Has anyone else had these same problems?

---

### Post by Hallavej on 2005-11-28
From Synaptic:

GNOME frontend for VLC (dummy legacy package)
The gnome-vlc package has been discontinued. You should use the wxvlc
package instead.

This package is only useful to ensure clean upgrades from old Debian
releases and can be safely removed.

---

### Post by mortram on 2005-11-28
anyone have luck with the audio then?

Seems to be the only application I can find capable of playing DVDs in sync with the audio - 'cept now there's no audio output.

---

### Post by Kyral on 2005-11-28
You need to install the plugin for whatever system you use.

So for ALSA

```
sudo apt-get install vlc-plugin-alsa
```

and for ESD

```
sudo apt-get install vlc-plugin-esd
```

---

