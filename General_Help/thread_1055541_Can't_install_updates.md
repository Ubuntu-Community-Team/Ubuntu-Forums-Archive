---
title: "Can't install updates"
date: 2009-01-30
forum: General Help
---

### Post by Trixilver on 2009-01-30
It says there are 9 updates available but I cant install them. When I click to install my updates, I get this error dialogue:
[B]
Could not apply changes!
Fix broken packages first.[/B]

And nothing else happens.

---

### Post by Crafty Kisses on 2009-01-30
Try to run the following command:
```
sudo apt-get install -f
```

---

### Post by amauk on 2009-01-30
often happens if you quit the updater in the middle of things

open up a terminal, and type
```
sudo apt-get install -f
```

---

### Post by hl2040 on 2009-01-30
Sometimes I get weird package installation errors when my root partition is full. Check that / isn't full with 'df -k' and look for for the "/" in the "Mounted On" column. If it is full, you need to clear up some space.

---

### Post by Trixilver on 2009-01-30
I tried the -f thing and I got this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
```
I tried updating again but same story and I'm positive that my HDD isn't full.

---

