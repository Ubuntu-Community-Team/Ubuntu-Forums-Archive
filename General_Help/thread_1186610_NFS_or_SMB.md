---
title: "NFS or SMB"
date: 2009-06-13
forum: General Help
---

### Post by measekite on 2009-06-13
Which (NFS or SMB) would be best to use

---

### Post by Scotty Bones on 2009-06-13
It depends.

In a pure *nix environment, I would go with NFS.
If you have a mixed OS network, go with SMB.

---

### Post by measekite on 2009-06-13
> **Scotty Bones said:**
> It depends.

In a pure *nix environment, I would go with NFS.
If you have a mixed OS network, go with SMB.

I am in process of getting rid of Windows 2K.  One client already is running just Jaunty.  Next week my main machine will be Jaunty only.

During this time I still have to run SMB because of my Win Server.  I plan of eliminating that soon as well so it will be all Linux.

So I would like to know why NFS would be better and in what respect would it be better.

---

### Post by Frenziefrenz on 2009-06-13
If all other things were roughly equal (which they probably aren't), NFS isn't proprietary.

---

### Post by bab1 on 2009-06-14
> **Frenziefrenz said:**
> If all other things were roughly equal (which they probably aren't), NFS isn't proprietary.

Neither is Samba's implementation of SMB.  NFS was developed by Sun and was originally a proprietary protocol.  SMB (which started with DEC and later MS) is what Samba is based on.

I think the biggest difference is whether the users are going to browse for ad-hoc shares. Only Samba (SMB) allows you to browse the workgroup for dynamically created shares.

---

### Post by HermanAB on 2009-06-14
Note that MS has a free version of NFS in their Services for Unix download from MS Technet.

---

### Post by measekite on 2009-06-15
> **bab1 said:**
> Neither is Samba's implementation of SMB.  NFS was developed by Sun and was originally a proprietary protocol.  SMB (which started with DEC and later MS) is what Samba is based on.

I think the biggest difference is whether the users are going to browse for ad-hoc shares. Only Samba (SMB) allows you to browse the workgroup for dynamically created shares.

SO ARE YOU SAYING that in a pure Linux network that because Samba/SMB allows one to browse the workgroup dynamically (please explain what you mean by that "ad hoc"etc) SMB would be a better choice or are there other adv and disadv of one or the other?

---

### Post by Celauran on 2009-06-15
Microsoft's Services for UNIX, which purportedly allows Windows machines to mount NFS shares, has been nothing short of infuriating to try to use. Configuring an XP machine to mount an NFS drive repeatedly led to an infinitie crash-reboot loop that I could only break out of by removing SFU in safe mode. That said, if you have any Windows machines at all, go with Samba.

---

### Post by bab1 on 2009-06-15
> **measekite said:**
> SO ARE YOU SAYING that in a pure Linux network that because Samba/SMB allows one to browse the workgroup dynamically (please explain what you mean by that "ad hoc"etc) SMB would be a better choice or are there other adv and disadv of one or the other?

The popular definition of ad hoc is "*improvised or impromptu*" and that is the idea I meant.  It allows  you to create a share on the fly by right click >>etc., etc., and someone else to browse for it and subsequently view that share.  A peer to peer situation.

With NFS you (as an administrator) need to create the shared file system and mount it to the users file system e.g., /media/nfs or some such place.

Advantages and disadvantages are subjective in my mind.  It would be best to understand (in a general way) the individual protocols capabilities.

If I have a network where there is domain control, and users login to various hosts, I would use NFS to mount the users /home/directory.  On the other hand If I have users that need to share data in a P2P situation, I would use Samba.

---

