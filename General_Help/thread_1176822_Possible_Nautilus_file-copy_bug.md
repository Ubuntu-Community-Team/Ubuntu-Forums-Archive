---
title: "Possible Nautilus file-copy bug?"
date: 2009-06-02
forum: General Help
---

### Post by BrendanM on 2009-06-02
Short version:
Nautilus checks for available space before it checks for duplicate files that will be overwritten or not copied, resulting in inaccurate "insufficient space" errors.

----------------------------------------------------------------------
Longer version:
I have an issue with the way Nautilus calculates space requirements for copying files. I have a large photo directory on my hard drive that I regularly back up to an external drive. The easiest way to do this is to select everything in the directory, and then copy it to the external, and hit "merge" when prompted about overwriting.

The whole size of the directory is maybe 6 or 7 gigabytes, but when updating the backup using the "merge" option results in actually copying no more than a few hundred megabytes at a time. However, unless I have sufficient space on the external drive to copy the ENTIRE directory, I get an "insufficient space" error, and the copy does not proceed.

The problem, as far as I can tell, is that Nautilus checks for available space before it checks which files/directories are duplicates that don't actually need to be copied. I don't know anything about the internals of Nautilus, but could somebody tell me if it would be easy to change the order in which these checks are carried out? Should this be reported as a bug in launchpad?

Also, does anyone have an easy workaround?

---

### Post by Linteg on 2009-06-02
I think you should file a bug report presuming there isn't one already.

---

### Post by BrendanM on 2009-06-02
Update: this bug has already been reported here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/246130](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/246130)
and here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/264585](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/264585)

They basically say that the Ubuntu project won't deal with this, and it needs to be reported higher up to GNOME developers. I'm quite skeptical of the claim that "The extra logic you describe would be of no use in most of the cases and add complexity to the code for no real win," but in any case I'll check and see if it's been reported on the GNOME project's bug tracker.

---

### Post by nandemonai on 2009-06-02
As a side note you may want to use cp, perhaps in a script. 

Something like so:

```
cp -uvr /source/images/* /destination/images/
```

This would get around the insufficient space issue in the mean time.

---

### Post by BrendanM on 2009-06-03
Thanks for the tip.

Further update, I submitted this as a bug upstream at the GNOME project's bug site: [http://bugzilla.gnome.org/show_bug.cgi?id=584685](http://bugzilla.gnome.org/show_bug.cgi?id=584685)

---

