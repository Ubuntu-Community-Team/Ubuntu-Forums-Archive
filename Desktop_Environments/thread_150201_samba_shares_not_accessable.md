---
title: "samba shares not accessable"
date: 2006-03-25
forum: Desktop Environments
---

### Post by CloudBuilder on 2006-03-25
Hello,

I have a samba server running on a box (Suse 9.2).
On my workstation I have Ubuntu.

I tried all kind of things to get the samba shares connected to the workstation but nothing works. From my winboxes I can connect without any problem (me,w98,xp doesn't matter ...)

Mount -t smbfs does not work. I can make a share, but when I want to see the contents of the share by browser or krusader it seems to hold and I can only force the leave from the browser.

Smbclient works.

On my desktop I have some SMB maps to the shares and I can copy to and from them, but I can't see them in any program, so If I want to copy something from Gimp to the samba share that is not possible.

Can anybody help me out?

CloudBuilder

---

### Post by jakez on 2006-03-25
maybe this helps...it worked for me:
[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)
greetz

---

### Post by CloudBuilder on 2006-04-03
No this is no help. The strange thing is, that I can make nice volume maps (with an smb mark and network icon) on the desktop(after giving username and password), I can copy files in them but there is no way to access them with a script, and that is what I want. Simply move some files in them by a cron job.

Any suggestions?

CloudBuilder

---

