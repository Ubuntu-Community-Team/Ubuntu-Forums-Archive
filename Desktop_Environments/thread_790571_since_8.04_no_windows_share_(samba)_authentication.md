---
title: "since 8.04 no windows share (samba) authentication possible"
date: 2008-05-11
forum: Desktop Environments
---

### Post by airflow on 2008-05-11
Hi,

I'm having a very annoying problem here since upgrading to 8.04. I use this as a workstation, samba-shares are hosted in the same network on a server which runs debian.

I used to connect to those shares by using the bookmarks-functionality of nautilus, where i had shortcuts to e.g. smb://user@servername/share, authentication (password for user) was done by nautils/gnome, everything was working fine. Since the upgrade i can't authenticate any more. Nautilus removed the "user@"-part of the URLs, and I can only view the public viewable parts of the share, not the folders which are restricted.
If I try to add "user@" again or create the shortcut new (with "Connect to Server"), the username is immediately removed. I also can't give the url in the address-bar, it's removed there too.

Anyone knows what's causing / how to solve this?
Best Regards,
airflow

---

### Post by mattack on 2008-05-13
I'm having the exact same problem... I think it's a bug in nautilus though. I may switch to Debian if this doesn't get fixed soon.

---

### Post by Awalton on 2008-05-15
It's a GVFS-SMB bug, and it's a known issue, and there's a patch you can try (it hasn't been verified by the author of that backend as he's currently on leave, though). It may solve your issues.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072/comments/7](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072/comments/7)

Please let us know if the patch solves your issue.

---

### Post by mattack on 2008-05-15
> **Awalton said:**
> It's a GVFS-SMB bug, and it's a known issue, and there's a patch you can try (it hasn't been verified by the author of that backend as he's currently on leave, though). It may solve your issues.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072/comments/7](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072/comments/7)

Please let us know if the patch solves your issue.

I tired the patch, bot compiling it myself and the pre-compiled binary in the thread. It didn't work for me. I still can't connect to samba shares that I would have to authenticate to.

---

### Post by maxcelpc on 2008-05-16
I have what may be a related problem with a network attached file server running embedded linux. If I go to Places|Network of Connect to server|Windows share and select the server/share, I get an entry in the Places menu and a desktop icon, from which I can browse the share (although there is something strange with some of the permissions). If I come back to the icon after a few minutes I get an error message 'Couldn't display "smb://server/shared/" There is no application for this type of file'.
If I click on the entry in the Places menu I get an error message 'Could not open loaction "smb/server/shared/" Generic error'. If I persist with clicking the menu entry, the file browser does eventually open and I can access the share.
What I have not been able to do is to mount the share at boot time using the same fstab entry that worked with Gutsy.

---

### Post by eriqjaffe on 2008-05-16
It may not be the same thing, but I had problems connecting to samba shares after updating to 8.04.  I just reverted samba-common, smbfs and smbclient to 3.0.26a and it worked like a charm.

---

### Post by captaintrav on 2008-05-16
> **eriqjaffe said:**
> It may not be the same thing, but I had problems connecting to samba shares after updating to 8.04.  I just reverted samba-common, smbfs and smbclient to 3.0.26a and it worked like a charm.

I was having the same issue since upgrading from Gutsy to Hardy.  Your suggestion worked.  After downgrading to gutsy versions of all samba related packages, it works again.  It didn't occur to me until reading this thread because the command-line tools still worked fine, just connecting to Windows shares in nautilus was broken.  Also, I might add, I could browse samba shares on the local machine fine with nautilus, but I got a host of weird problems when trying to browse other shares.  I could see the machines in the workgroups, and the shares, but that's as far as I would get usually.  Sometimes I would be able to browse a share, but it would take forever.  I would also get dbus errors, timeout errors, and other errors.  With 3.0.26a versions all is well.  Hardy is trying my patience  **sigh**

---

### Post by maxcelpc on 2008-05-16
Suceeded in getting cifs to work. It doesn't support url's, so IP addresses are required. Also it won't accept spaces before username or password in credentials files.

---

### Post by Sayang on 2008-06-04
Solution for access to Windows passworded shares from Ubuntu 8.04

It was suggested elsewhere to ensure that in smb.conf, the entry:

"security = user" rather than "security = share" should be present.

This did not help for me, however, adding the entry:

"client lanman auth = yes"

then allowed the authentication of and access to my several Windows shares.

---

### Post by oneloveamaru on 2008-06-05
Guys, having the same exact problem here. How do I downgrade to 3.0.26? When I tried to install smbfs it gave me an error about samba-common being 3.0.28. If I try to remove samba-common it wants to remove kubuntu-desktop as well. :(  Thanks for the help guys.

[EDIT] Figured it out. Anyone that wants to know as well, follow these two links and get samba-common and smbfs then do a "dpkg -i --force-downgrade" on those debs. Found the solution here [http://ge.ubuntuforums.com/showthread.php?t=770893]("http://ge.ubuntuforums.com/showthread.php?t=770893")

---

### Post by satbunny on 2008-06-27
I have only just noticed this issue since I normally mount my samba shares in the fstab using cifs (once I'd had that explained to me) and don't browse on the fly. However my mate came over last weekend and couldn't browse the samba shares so I am very pleased that this thread is here.

I'll tell him the IP address next time.. and now I have installed Heron on this laptop I guess I'd better start editing the fstab!

It is a shame this happened, it look like 8.04 got caught between upstream and downstream at just the wrong time.

Wish they'd let everyone know of the fixes sooner but maybe Canonical didn't realise it either.

Roll on 8.10..

---

### Post by rgrashel on 2008-12-16
> **Sayang said:**
> Solution for access to Windows passworded shares from Ubuntu 8.04

It was suggested elsewhere to ensure that in smb.conf, the entry:

"security = user" rather than "security = share" should be present.

This did not help for me, however, adding the entry:

"client lanman auth = yes"

then allowed the authentication of and access to my several Windows shares.

I wanted to send a note to say that THANKS.  I am running Linux Mint 6 (Intrepid) and could not browse password-protected Windows shares.  After applying the above to my /etc/smb.conf file, everything works fine.

Many thanks!

---

