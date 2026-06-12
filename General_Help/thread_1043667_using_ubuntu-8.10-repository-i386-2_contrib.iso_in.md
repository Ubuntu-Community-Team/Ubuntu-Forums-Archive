---
title: "using ubuntu-8.10-repository-i386-2_contrib.iso in synaptic"
date: 2009-01-18
forum: General Help
---

### Post by demikid on 2009-01-18
hi guys. i downloaded these 6  ubuntu 8.10 dvd isos and now
i cant manage to mount them and use them in synaptic.
i seem to do everything right:mount them, add the line in sources.list i.e

[B]#mount /mnt/stuff/ubuntu-8.10-repository-i386-2_contrib.iso -t iso9660 /media/iso1 -o loop 
[/B]
in sources.list:


[B]deb file:///media/iso1/ intrepid main restricted universe multiverse 
[/B]

but i keep getting this error when i run apt-get update:

[B]Err file: intrepid/main Packages
  Sub-process gzip returned an error code (1)
66% [Packages gzip 0]
gzip: stdin: not in gzip format
Err file: intrepid/restricted Packages
  Sub-process gzip returned an error code (1)
W: Failed to fetch file:/media/iso1/dists/intrepid/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
W: Failed to fetch file:/media/iso1/dists/intrepid/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)[/B]

i have even tried changing 

**deb file:///media/iso1/ intrepid main restricted universe multiverse**

to

**deb file:/media/iso1/ intrepid main restricted universe multiverse**

but nothing helps.somebody help!

---

