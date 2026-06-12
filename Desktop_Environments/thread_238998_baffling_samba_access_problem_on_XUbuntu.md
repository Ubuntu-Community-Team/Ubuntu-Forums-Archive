---
title: "baffling samba access problem on XUbuntu"
date: 2006-08-18
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-18
I used Ubuntu (Gnome desktop) for about 2 months before I decided to switch to XUbuntu (XFCE desktop) for reasons of speed/performance.

However, in the process lost a few goodies that existed in the Gnome desktop, like the ability to access Windows shares (on a networked Samba server).

I tried to use mount -t smbfs //server/share /mnt/serverdir/sharedir to manually mount that share, but it doesn't work. I get the the following error message:

> mount: wrong fs type, bad option, bad superblock on //nefi/dani,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


So I checked a little further and discovered that while I have smbclient installed, I don't have smbmount installed...

Which baffles me: How did the Gnome desktop mount the samba shares without smbmount? :? 

And what do I do now to solve the problem? Does smbmount come in a package different than Samba? :-s 

Thanks,
Alex

---

### Post by fdoving on 2006-08-18
You want the 'smbfs' package.


- Frode

---

### Post by xp_newbie on 2006-08-18
> **fdoving said:**
> You want the 'smbfs' package.

Thanks!

Do you also happen to know how on earth does the Gnome desktop manages to mount those Samba shares without needing the smbfs package installed? I am very curious to know how this is accomplished.

I checked via Synaptic and discovered that the only related package currently installed in my system is smbclient. Neither smbfs, nor samba, nor linneighborhood are installed.

I am puzzled.

---

### Post by stormblue on 2006-08-18
I believe it's a feature of nautilis, although, someone should confirm this.

I'm also looking for this easy samba functionality for xubuntu.  Any suggestions?

---

### Post by xp_newbie on 2006-08-18
> **stormblue said:**
> I believe it's a feature of nautilis, although, someone should confirm this.

Yes, I believe so too, but I am curious to know how this is being accomplished *without* the **smbfs** package. It seems that nautilus is using **smbclient** to wrap it with a GUI - similar to many GUI wrappers around **ftp**.

> **stormblue said:**
> I'm also looking for this easy samba functionality for xubuntu.  Any suggestions?

I believe **linneighborhood **will give you this functionality. The problem with this approach, however, is that the mounted shares are not accessible via command line and scripts (just like in the Gnome desktop). The most consistent solution IMHO is to use mount -t smbfs (either in a script or in /etc/fstab - depending on what you actually want). Once you do that, it is accessible via any file manager (e.g. Thunar).

---

### Post by stormblue on 2006-08-18
Thanks!

I got it working now.

The only weird thing is that before I didn't need to know the login name to login in under Ubuntu, but under xubuntu I had to login.

---

