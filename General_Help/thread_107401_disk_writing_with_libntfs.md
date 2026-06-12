---
title: "disk writing with libntfs"
date: 2005-12-22
forum: General Help
---

### Post by three_sixteen on 2005-12-22
I installed the libntfs5 package and libntfs-gnomevfs package, but I'm not sure how to take advantage of them now?

Do I need to remount the NTFS partition with different attributes than I have it mounted as now?

```
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0

```

---

### Post by BathroomNinja on 2005-12-23
What exactly are you trying to do?  What is the problem?  I'm quite confused by your post.

---

### Post by varunus on 2005-12-23
You cannot write NTFS with linux and those drivers.  Write support is highly experimental, and if you try it, **you will destroy your data.**

There is only one project that lets you write to NTFS in Linux; it is called the captive project, and has not really been developed for a little while...if you want, look it up and try it out.

But please do not try NTFS writing any other way.  Eventually, the libntfs driver will support writing to NTFS, but not yet.

Also, the packages you downloaded are unnecessary.  The Ubuntu kernel comes with NTFS read support already.  If you go to the libntfs website, you'll find that its the library for changing ntfs partition sizes and things like that.

---

### Post by three_sixteen on 2005-12-23
[QUOTE=varunus]You cannot write NTFS with linux and those drivers.  Write support is highly experimental, and if you try it, **you will destroy your data.**

There is only one project that lets you write to NTFS in Linux; it is called the captive project, and has not really been developed for a little while...if you want, look it up and try it out.

But please do not try NTFS writing any other way.  Eventually, the libntfs driver will support writing to NTFS, but not yet.

Also, the packages you downloaded are unnecessary.  The Ubuntu kernel comes with NTFS read support already.  If you go to the libntfs website, you'll find that its the library for changing ntfs partition sizes and things like that.[/QUOTE]

Ahh, I see.

Thanks for the heads up!

---

### Post by sebastjanp on 2006-06-11
> **varunus]You cannot write NTFS with linux and those drivers.  Write support is highly experimental, and if you try it, **you will destroy your data.**

There is only one project that lets you write to NTFS in Linux said:**
> 


How come that the new Knopix can write to ntfs?

they say:
[quote]
* transparent write access for NTFS partitions (libntfs+fuse)


---

