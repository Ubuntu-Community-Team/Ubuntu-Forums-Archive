---
title: "windows network mounts"
date: 2007-11-06
forum: Desktop Environments
---

### Post by endswithaW on 2007-11-06
hello forums,

i currently use "places > connect to server" to mount my windows network share to my ubuntu 7.10 desktop.  i know how to use samba to mount a network drive to a filesystem (such as /media/networkdrive).  what i can't figure out is how "connect to server" mounts filesystems or network drives.

typically when i type "mount" i would see an NFS or SMB filesystem.  with "connect to server" i don't see anything.  

i am trying to see my networked share on the filesystem somewhere so i can access it from the command line or use the application "unison".  

any ideas?  i'm a linux administrator for a large company, but this is the first time i've used ubuntu.  i'm not quite familiar with the nuances of desktop linux.

thanks friends.

---

### Post by maybeway36 on 2007-11-06
I don't think it actually mounts it.  For that ,you want to use cifs or smbfs in the /etc/fstab fie.

---

### Post by endswithaW on 2007-11-06
i see mount information in 

/home/trgm/.nautilus/metafiles

but it doesn't appear to be in a format that smb or other familiar protocols would speak.

---

