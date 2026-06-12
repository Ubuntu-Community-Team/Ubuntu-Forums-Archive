---
title: "Jaunty fstab smb network access"
date: 2009-06-24
forum: General Help
---

### Post by measekite on 2009-06-24
**Before Jaunty:**

I was using Feisty 7.04 and had the appropriate entries at the bottom of my fstab file and my network drives have been auto mounting for read and write without any problems at all.
[B]
After Jaunty Install:[/B]

I can manually mount my network shared drives  by clicking menu>places>Network and filling out the 3 pieces of information in the dialog box.  I have to do this twice, once for each share.  I do not know for sure yet but I read it would be faster to auto mount via fstab and for sure more convenient.
[B]
Problem:  [/B]
I created a new /root/.smbcredentials file and provided the same info:
username=winusername
password=winpassword

I set the permissions to 700

Just like in Feisty I edited the fstab file in /etc and added the following two lines:

```
//111.111.11.11/share1  /media/netshare1 smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0 0 
//111.111.11.11/share2  /media/netshare2 smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0 0 
``````
When I do a mount -a or a reboot I get the following error:
mount: wrong fs type, bad option, bad superblock on //111.111.11.11/share1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //111.111.11.11/share2,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```**Question:**

I have read and searched the entire internet and while others have had similar but not exact problems like those above all of the information still leads to the way I have done it.  I also have put in username and password in place of the credentials file and got the same errors.

[COLOR=Red]Is this a known bug without a workaround or does anybody know of a solution.  The shares are on a Win2K Server.

How do you solve this?[/COLOR]:confused:

---

