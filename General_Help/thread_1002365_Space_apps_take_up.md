---
title: "Space apps take up"
date: 2008-12-04
forum: General Help
---

### Post by LegoAddict on 2008-12-04
So I have suddenly found myself deprived of disc space by about 10 GB.

Is there any way I can find out how much disc space each app I have installed takes up?  I've used Intrepid's cruft remover and cleaned all my caches and stuff in UbuntuTweak.

I'm running Ubuntu Intrepid.

---

### Post by Skripka on 2008-12-04
> **LegoAddict said:**
> So I have suddenly found myself deprived of disc space by about 10 GB.

Is there any way I can find out how much disc space each app I have installed takes up?  I've used Intrepid's cruft remover and cleaned all my caches and stuff in UbuntuTweak.

I'm running Ubuntu Intrepid.

Go in Add/Remove and look up FileLight...tis a neat graphical utility for just this purpose.

---

### Post by sdennie on 2008-12-04
The short answer is, "Probably not".  The long answer is that Ubuntu doesn't put applications into their own folders but instead spreads them out across the existing file system structure so everything is in a well known place.  Having said that, you can use something like:

```

apt-cache show name_of_package | grep Size

```

And it will show you the size of an individual package but, not of it's dependencies (which will often dwarf the size of the package).  Another option if you are looking to reclaim disk space is to go to Applications->Accessories->Disk Usage Analyzer and see if you can figure out where space is being taken up.

---

