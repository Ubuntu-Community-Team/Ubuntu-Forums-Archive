---
title: "UDF permissions"
date: 2005-12-08
forum: General Help
---

### Post by jhnphm on 2005-12-08
Every time I mount a UDF CDRW or a DVDRAM, I have to sudo as root and manually set the permissions to allow myself to write or read from the disc - it appears to ignore permissions on the device file, the mountpoint, and the umask passed in as a parameter (although it can further *restrict* permissions on that last one).  If it is formatted as Reiser, ext2, etc it seems to work fine, but there is limited compatibility  with other platform for those. How can I fix this so it gives 777 permissions to the disc?

EDIT: Nevermind, figured it out for manually mounting (set permissions on mountpoint after mounting as root)-  still can't seem to figure it out for mounts via pmount (automatic mount via GNOME). Is there any way to run a script before and after pmount executes?

EDIT: It appears pmount sets a permission of 007 by default- workaround seems to be to make myself own the disc rather than simply handing out read/write permissions. Being able to run a script would be useful...

EDIT: It appears it forgets the permissions of the root directory of the disk, and resets it to root w/ permissions 007 when the disc is ejected. How can this be fixed?

EDIT: It seems pmount overwrites the original permissions when gnome automounts the disc, while it doesn't when manually running pmount.

EDIT: Ended up patching pmount to set a mask of 000 for UDF.

---

