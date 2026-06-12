---
title: "ntfs mount"
date: 2009-04-09
forum: General Help
---

### Post by steeler on 2009-04-09
hi..i would like to mount an ntfs volume so that 1) it's case-insensitive while it supports local characters (greek or utf8, don't know)
2)it mantains windows read-only attribute
3)every user is able to change permissions for single files on that volume
thanks..

---

### Post by askreet on 2009-04-09
NTFS support is very basic in Linux.  It does not support permissions, for example.  It also does not support the filesystem attributes in place in Windows.

---

### Post by coffeecat on 2009-04-09
> **askreet said:**
> NTFS support is very basic in Linux.  It does not support permissions, for example.

**askreet**, you've got that back-to-front. It's the Windows NTFS filesystem that doesn't support Unix/Linux permissions, so that makes your first statement dubious. In fact I find the lack of support for Linux permissions to be a positive advantage, but that's a different matter.

**steeler**, the Jaunty installer set up my internal NTSF partition with the following /etc/fstab line:

```
device    mountpoint    ntfs    defaults,nls=utf8,umask=007,gid=46    0 1
```You could try that and see whether that suits your purpose. Obviously, change 'device' and 'mountpoint' to whatever you need. But, be warned, there's a minor bug using this line which has already been reported to launchpad. If you do a GUI copy from an ext3 partition to a NTFS partition mounted this way, the date/time stamp gets changed to current time. But not the other way round: NTFS -> ext3.

I've got round that with a simple:

```
device    mountpoint    ntfs    defaults    0 0
```Date/time stamps are preserved, but I don't know whether that would work for you. Experiment with variations and see what does.

---

### Post by askreet on 2009-04-09
> **coffeecat said:**
> **askreet**, you've got that back-to-front. It's the Windows NTFS filesystem that doesn't support Unix/Linux permissions, so that makes your first statement dubious. In fact I find the lack of support for Linux permissions to be a positive advantage, but that's a different matter.

Hah, now you're just splitting hairs. =)

---

### Post by steeler on 2009-04-09
basically, is it  possible to just make it case-insensitive?

---

