---
title: "Kubuntu mounting c drive/sda2"
date: 2007-09-11
forum: Desktop Environments
---

### Post by avantgardaclue on 2007-09-11
I'm sure that this must have been gone over a million times before.

Twice my ubuntu gnome has terminally crashed. Apparently ubuntu is the best desktop so i'm giving it a 3rd go but this time i'll try KDE.

Looks very smart, a whole lot different to gnome. When i was using gnome there was a utility to automount my windows drive c: or sda2 and also write to that drive.

Hmmmm, so how does this work in KDE please?

help gratefully recieved..   thanks... Simon

---

### Post by merlinus on 2007-09-11
Don't know about automounting in kde, but to write to ntfs partitions you will still probably need to install the drivers.

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

---

