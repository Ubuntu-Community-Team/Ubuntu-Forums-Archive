---
title: "Accessing Windows Shares from Kubuntu"
date: 2005-09-04
forum: Desktop Environments
---

### Post by raveman7 on 2005-09-04
so i have my laptop set with Kubuntu, i have samba client setup on the laptop now i just need to connect to my windows pc to connect to the shared drives and the printer. 

my windows server is running 2003 server setup as a domain controller to share files and the printers. i am not having any luck connecting to the windows shares to access them. ive done searches on this forum and have looked at the ubuntu starter guide but nothing really standing out on how to do this. 

any help would be appreciated.. im sure this has been asked before so forgive my n00b status..

---

### Post by drx on 2005-09-04
[QUOTE=raveman7]so i have my laptop set with Kubuntu, i have samba client setup on the laptop now i just need to connect to my windows pc to connect to the shared drives and the printer. 

my windows server is running 2003 server setup as a domain controller to share files and the printers. i am not having any luck connecting to the windows shares to access them. ive done searches on this forum and have looked at the ubuntu starter guide but nothing really standing out on how to do this. 

any help would be appreciated.. im sure this has been asked before so forgive my n00b status..[/QUOTE]
 I am not familiar with Server 2003, but what i usually do is to type into Konqueror's address bar:

smb://windowsUser@nameOfWindowsMachine

and all the things for this user from an XP machine show up.

---

### Post by raveman7 on 2005-09-04
ok that worked i can see the shares, but how would i go about mounting them to my laptop?

---

### Post by linzer on 2005-09-04
[QUOTE=raveman7]ok that worked i can see the shares, but how would i go about mounting them to my laptop?[/QUOTE]

Check out the [unofficial Ubuntu guide](http://ubuntuguide.org/#networking)  networking section.  This deals with mounting samba shares at boot time both in a read only and read/write mode.

Depending on your domain controller's security policy, you might have to mount as type CIFS as opposed to SMBFS.

HTH
--
Linzer

---

