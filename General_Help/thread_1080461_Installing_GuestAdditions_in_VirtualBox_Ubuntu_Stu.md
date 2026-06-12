---
title: "Installing GuestAdditions in VirtualBox Ubuntu Studio"
date: 2009-02-25
forum: General Help
---

### Post by jhouse59 on 2009-02-25
I'm trying Ubuntu Studio 8.04 on VirtualBox. How do I open up the CD-ROM in a terminal so I can install the VBoxGuestAdditions? Also, I use Mint 5.0. It has a program called APTonCD to back updates that are downloaded. I know Mint uses Ubuntu as its base. Does Ubuntu use this or does it use something else? I couldn't find in the Add/Remove program.

---

### Post by ju2wheels on 2009-02-25
```

cd /media/cdrom0/
sudo ./Vboxadditions_name

```

Dont recall the actual name of the installer, just type the first letter and press TAB twice...

AptOnCD is in the repository. Just make sure you have the correct repositories enabled on System->Administration->Software Sources and use Synaptic instead (System->Administration->Synaptic).

```

sudo apt-get install aptoncd

```

---

