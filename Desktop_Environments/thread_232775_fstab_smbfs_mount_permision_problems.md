---
title: "fstab smbfs mount permision problems"
date: 2006-08-09
forum: Desktop Environments
---

### Post by sitedesign on 2006-08-09
I have the following in my /etc/fstab file
//192.168.0.30/main /home/pking/server/main smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

When I create a text file on the share then open it in gedit, I get a fault on trying to save. Cannot create a temporary backup file.

When I mount a share using nautilus (smb mapping on desktop) then edit the same file in gedit I do not have the problem.

I presume the problem is with my permisions set in the fstab file. Can anyone shed some light on this one please.

PS the file server is a linux box running samba, so I could use NFS or SSH etc if that is easier.

Regards Peter King

---

### Post by ryanVickers on 2007-05-23
I would recommend ssh over nfs highly!  Yes, I would definitely agree it's a permission problem.  Have you looked at the current permissions for the folder(s) in question and their files?  If anything seems like it should be different, (for example, if you want anyone who connects, even you, to be able to read/write, make sure the "others" section gives full privilages, not just the default, read-only) than I would change it.  You might need to use "sudo nautilus" to get full control over some of the files.

Now my difficulties:
I'm having a similar problem - I got a ssh network working perfectly really easily (at least on the LAN, don't know about remote yet), but it gives anyone who knows my password free range to do what ever they want (write/read every file) anywhere in the computer.  They need the password, but I would still like to know how to set permissions for folders (full, read-only, or no access)

Any ideas, anyone?

---

### Post by SirSpammenot on 2007-05-24
Funny how things change....

Instead of smbfs use cifs.  CIFS is the new name (SMB is depricated) that the protocol is going to use and the newer builds of samba seem to play better when you use the new name.  I was having the exact same issue and when I changed smbfs to cifs, reboot, ouila!

TRY: //192.168.0.30/main /home/pking/server/main ***[COLOR="Red"]cifs[/COLOR]*** credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

My icon on the desktop even went from the orange 'link' icon to a silver 'disk' icon after a reboot.  Just like a real drive!

Cheers!

---

