---
title: "Herd 3 64-bit report"
date: 2007-02-04
forum: Development CD/DVD Image Testing
---

### Post by Solver on 2007-02-04
After having had some issues with Edgy, I went ahead to install Herd3 (64-bit). It was a clean install, though preserving /home.

First, there was no usplash on boot, just a black screen with boot messages. Note that I was also affected by the no-usplash problem on Edgy. Other than that, the boot went fine. Two issues during installation:

1. That timezone selection screen, with the map. Clicking on the relevant section of the map to zoom in caused it to zoom really slowly - took some 10-15 seconds instead of being instantaneous. Possibly related to this, the "vesa" display driver was being used for whatever reason.

2. During manual partitioning, after every change I made (right click a partition to edit the mount point or tick/untick the Format checkbox), that "Analyzing drives" appeared, which caused the installer window to freeze up (without repainting) for up to several minutes.

Other than that, the system installed fine and everything. After booting Feisty from HD, I encountered a problem (possibly the same as others described) with setting up my network. I couldn't get the Net to work when setting my network up through the control center, and ifup would complain about a malformed /etc/network/interfaces - I fixed the network issue by editing the file manually. I have a static IP, and my relevant line said

```

iface eth1 inet

```

causing the network not to come up. The fix, for me, was to change it to

```

iface eth1 inet static

```

---

