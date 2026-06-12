---
title: "Startup Shell Script Problems"
date: 2005-03-21
forum: Desktop Environments
---

### Post by orion_114 on 2005-03-21
I have written a shell script to mount 2 samba network shares to my home directory.

#!/bin/bash/
sudo smbmount //server/share1 ~/share1/ -o username=guest,fmask=664,dmask=755,uid=1000,gid=1 00,debug=0,workgroup=mshome
sudo smbmount //server/share2 ~/share2/ -o username=guest,fmask=664,dmask=755,uid=1000,gid=1 00,debug=0,workgroup=mshome

I have added the following entry to the startup programs in the session dialog.
xterm -hold -e ~/mount.sh

My only problem is now that I keep getting prompted for my password 3 times everytime I login.
Is there anyway I can run this script as full root and not sudo ?
And also is there a way to maybe automatically have the script enter my password ?
Any help would b appreciated ! :D

---

### Post by cwaldbieser on 2005-03-25
Not sure but I think you must be able to allow normal users to mount shares (maybe there is something in the man pages for /etc/fstab that is relevant)?  Short of that, you could always have your script get its input from a file instead of standard input, though some programs that want passwords don't always seem to respect that.  A program like "expect" would do the trick, but I'm not so sure if storing your password in a file is such a good idea.

---

