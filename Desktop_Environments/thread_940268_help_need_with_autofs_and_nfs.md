---
title: "help need with autofs and nfs"
date: 2008-10-06
forum: Desktop Environments
---

### Post by drmoqu on 2008-10-06
Hi I am trying to setup autmounting of two nfs shares via automount. I have followed the instructions I found on various webpages but it does not appear to be working. When I go to my mountpoint, I do not see the contents of the mounted share.

Here are the two files I have modified:
my /etc/auto.master reads:

#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/nfs    /etc/auto.nfs

Then my /etc/auto.nfs reads:

/media/Snap410 -hard,intr 169.254.244.97:/replicate
/media/Snap4100 -hard,intr 169.254.244.98:/share1

And yes the servername and path are correct because the following line in my /etc/fstab:

169.254.244.97:/replicate /media/Snap410 nfs defaults 0 0
169.254.244.98:/replicate /media/Snap4100 nfs defaults 0 0

allows me to mount and unmount easily.


Now you are probably wondering why I want the autofs to work. The short answer is that I need the mounts for setting up a backup. I would like the backup to work unattended so it would be easier if the mountpoints automatically mounted when accessed.

After modifying/creating the /etc/auto.master and auto.nfs files above, I restarted autofs. Then I changed directory to /media/Snap410 and issued and ls command. The result shows an empty directory. I am working under the assumption that an ls command should constitute accessing the mountpoint even if the cd command doesn't (though I think it should as well).

Anyway, if you are familiar with autofs and can help me identify what I am doing wrong, your assistance would be appreciated.

FYI..I am using Ubuntu 8.04 desktop.

---

