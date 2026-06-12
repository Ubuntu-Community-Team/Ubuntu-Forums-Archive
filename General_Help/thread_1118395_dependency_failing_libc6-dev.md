---
title: "dependency failing: libc6-dev"
date: 2009-04-06
forum: General Help
---

### Post by figured on 2009-04-06
I have a Nvidia Video card, I am trying to install the drivers: nvidia-177-kernel-source

but it keeps failing because of a dependency.

error message:

E: /var/cache/apt/archives/libc6-dev_2.8~20080505-0ubuntu9_amd64.deb: corrupted filesystem tarfile - corrupted package archive

I am new to Ubuntu how do I resolve this, I have exhausted all I know.
Thank you

---

### Post by ryanhaigh on 2009-04-07
The package file that has been downloaded is corrupt, all you need to do is remove it and apt should download the package file again when you try to install. Press alt-f2 to bring up the run dialog, then enter

gksudo nautilus /var/cache/apt/archives/

This will start the file browser in root/admin mode, you can then delete the file libc6-dev_2.8~20080505-0ubuntu9_amd64.deb. Once you are done close the file browser. You need to be careful when running anything as root.

Once that is done you can try installing the nvidia driver package in whatever way you were doing so before.

---

### Post by figured on 2009-04-07
Worked like a charm, thanks a bunch.  What a awesome first experience with the ubuntu forums.

---

