---
title: "Can email client profile run off network drive?"
date: 2009-05-20
forum: General Help
---

### Post by Heeter on 2009-05-20
Hi all,

Just wondering, can thunderbird/evolution email client profile folder run off a network samba/nfs shared drive (Ubuntu File Server 8.10)?

I would like to put the profile onto a network drive so that it is backed up in real time in case the desktop workstation stops working.

I once tried changing the path of the thunderbird in the profile.ini file and moved the profile folder on an XPPro box once and it didn't work. I have never tried it with my Ubuntu Server/workstation setup.

Thanks

Heeter

---

### Post by dcstar on 2009-05-21
> **Heeter said:**
> Hi all,

Just wondering, can thunderbird/evolution email client profile folder run off a network samba/nfs shared drive (Ubuntu File Server 8.10)?

I would like to put the profile onto a network drive so that it is backed up in real time in case the desktop workstation stops working.

I once tried changing the path of the thunderbird in the profile.ini file and moved the profile folder on an XPPro box once and it didn't work. I have never tried it with my Ubuntu Server/workstation setup.


A lot of things require full Linux filesystem permission support, which external resources do not always provide.

You can try to do it by creating a soft link to the external folder, and replacing the existing .evolution folder with that link.

---

### Post by egalvan on 2009-05-21
I regularly run FireFox with profiles on *nix file systems,
and NTFS file systems.

Firefox is run from *nix and Windows platforms.

Thunderbird has a similar profile system.

Absolutely no problems.

I got the idea (and information) from the June 2006 issue of* Linux Journal*

You do need to verify the paths.
It was the only problem I had....

---

