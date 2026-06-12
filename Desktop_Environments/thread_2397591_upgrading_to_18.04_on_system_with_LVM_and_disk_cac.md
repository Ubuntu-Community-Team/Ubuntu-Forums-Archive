---
title: "upgrading to 18.04 on system with LVM and disk cache"
date: 2018-07-31
forum: Desktop Environments
---

### Post by Peter_Brandon on 2018-07-31
I need to upgrade to 18.04 on a system with LVM (for the home and root directories).  I've seen in 'known problems' and on the web that there are problems doing a full installation of 18.04 on a LVM system.  What I don't know is whether I would be wrecking my system if I simply upgrade from 17.10 to 18.04.  Anyone have any experience / thoughts on that?

I also have a small SSD that I created a disk cache for.  I imagine I at least need to turn off the disk cache before the upgrade, but do I also need to completely erase it?

Peter

---

### Post by Dennis N on 2018-07-31
My Ubuntu 17.10 was an LVM install, and I upgraded to 18.04 using the Software Updater. I experienced no problems with this upgrade.

---

### Post by Peter_Brandon on 2018-08-04
Dennis:  Thanks so much, that's very reassuring!  Once I figure out how to turn off the disk cache, I'll give this a try.

Peter

---

### Post by Peter_Brandon on 2018-08-06
Just fyi to all:  I turned off the SSD cache using:  lvremove linuxVG/lv_cache .  After that, I installed 18.04 without incident.  All good!

The following instructions will allow me to reinstitute the SSD cache:

##Create the cache data logical volume on SSD PV. 
lvcreate -L 14.8G -n lv_cache linuxVG /dev/sdb1
##Create the cache metadata logical volume on SSD PV.
lvcreate -L 16M -n lv_cache_meta linuxVG /dev/sdb1
##Create the cache pool logical volume by combining the cache data and the cache metadata logical volumes into a logical volume of type cache-pool
lvconvert --type cache-pool --cachemode writethrough --poolmetadata linuxVG/lv_cache_meta linuxVG/lv_cache
##When you execute this command, the cache data logical volume is renamed with _cdata appended to the original name of the cache data logical volume, and the cache metadata logical volume is renamed with _cmeta appended to the original name of the cache data logical volume; both of these volumes become hidden.
lvs -a -o +devices
##Create the cache logical volume by combining the cache pool logical volume with the origin logical volume. The user-accessible cache logical volume takes the name of the origin logical volume. The origin logical volume becomes a hidden logical volume with _corig appended to the original name. You can execute this command when the origin logical volume is in use.
lvconvert --type cache --cachepool linuxVG/lv_cache linuxVG/homeLV

---

