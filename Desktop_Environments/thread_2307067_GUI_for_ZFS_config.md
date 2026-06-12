---
title: "GUI for ZFS config"
date: 2015-12-21
forum: Desktop Environments
---

### Post by THEKINGDOM on 2015-12-21
Who would I need to beg to develop a simple GUI for the purposes of ZFS and RAID formatting and manipulation within Ubuntu and Webmin? 

Right now the only way is with CLI. I do know the CLI methods but simple operations that I'd like to be able to see visually, like the RAID array or the allocated drives with ZFS, pools, datasets etc would all be nicely placed in a GUI that would double as an input to modify them. 
There are GUI's that exist on Ubuntu for non-ZFS volumes, but since Ubuntu is moving towards ZFS as a standard it only makes sense that a GUI would be created for such tasks. It's nice to see things like your currently configured cron jobs, like scrubs and disk usage etc.

Currently, I'm trying to migrate from FreeNAS to Ubuntu. I even opted to go for Ubuntu desktop since it's still fairly lightweight and it seems that some things that were dead simple on FreeNAS are a tonne of CLI commands to install and **equally** as many commands just to interact or continue running them within Ubuntu. I would have thought running Ubuntu desktop would have provided some graphical administrative advantages, but completely not so. At least not when trying to deal with things like: ZFS, Utorrent/BitTorrent, PlexMediaServer, Owncloud etc..

---

### Post by grahammechanical on 2015-12-21
It seems to me that ZFS & BTFS are meant for server systems and not desktop systems. If either of those 2 file systems were to become default for both Ubuntu desktop & server editions then there would most certainly be a need for a GUI utility.

ZFS may become a standard for Ubuntu server systems but that does not mean that it will also be the standard for Ubuntu desktop systems. And I can see 2 obstacles.

> ZFS is licensed under the [CDDL]("http://en.wikipedia.org/wiki/CDDL"), a popular and widely used [OSI-approved open source license]("http://opensource.org/licenses/category"), that is [recognised by the FSF]("https://www.gnu.org/licenses/license-list.html#CDDL")  as a free software license, but is incompatible with the GNU GPL.  Because of that ZFS cannot be added to the Linux kernel directly. It  can, however, be distributed as a DKMS package separate from the main  kernel package.

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

And then there is the plan to build Ubuntu desktop on Snappy Ubuntu Core. That will have an OS that can be rolled back if an update to the OS fails and is also read only. In my mind those developers with the greatest reason for developing an ZFS GUI management utility (the desktop team) are very busy elsewhere.

---

### Post by lukeiamyourfather on 2016-01-04
ZFS is so easy to administer there's not really a point in creating a GUI. It has only two commands (zfs and zpool) and is typically used for servers where there's no GUI anyway. If you want a GUI I'd suggest sticking with FreeNAS because ZFS on Linux is unlikely to have a GUI anytime soon if ever. If you'd like some assistance with commands I'd be happy to help.

---

### Post by bobk48 on 2016-01-14
I agree with Robert here, a GUI for ZFS would be a tremendous advance in terms of expediency, utility, and ease of use. An excellent example of this is the PCBSD zmanager, does everything that zpool and zfs commands do, but with pictures! And I respectfully disagree with Darth, ZFS is for every class of computer, laptop with one drive, server with NAS, cluster, Docker containers, desktop, tablet, on and on. Linus couldn't do ZFS, he did git instead.

---

### Post by lukeiamyourfather on 2016-01-14
> **bobk48 said:**
> And I respectfully disagree with Darth, ZFS is for every class of computer, laptop with one drive, server with NAS, cluster, Docker containers, desktop, tablet, on and on.

I wouldn't touch ZFS with a ten foot clown pole on a laptop or average desktop computer. They don't have ECC memory. The way it's designed ZFS assumes everything in the ARC is sane data and when it's not there's no recourse, stuff gets corrupted and much worse so than other file systems which don't have something like the ARC. No ECC memory means no ZFS.

---

### Post by bobk48 on 2016-01-14
I totally agree with lukeiamyourfather about ecc memory on a server where you love your data( or the money that your customers give you for maintaining data integrity), but for an ordinary user like myself desktop and laptop use, non-ecc works for me. My ZFS use routinely involves mirroring the system disk on all the major UNIX releases (Solaris 11.3, OpenIndie, FreeBSD, PCBSD) mirroring USB 3  thumbdrives, custom compilations of the major UNIX kernels to set ZFS copies=2 on single-drive laptops without ecc memory. All those use cases outweigh data loss due to non-ecc bad ram, FOR ME. lukeiamyourfather is totally correct- no ecc, no zfs, why mess around?

---

