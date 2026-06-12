---
title: "How to search entire hard drive (HDD) or file system?"
date: 2009-04-29
forum: General Help
---

### Post by Buttons840 on 2009-04-29
I use the program Blender.  Blender works fine, and as far as I know a file known as B.blend is required for Blender to work.  Obviously then, this B.blend file is somewhere on my hard drive, but I can't find it.

I have tried several things.

```

sudo updatedb
```
```

sudo locate *.blend
```
```

sudo find -name *.blend -print
```

*All 3* commands complete is under 2 seconds.  Is it really possible that my entire HDD index was updated in under 2 seconds?

The latter 2 command do return lists of .blend [blender] files, all I witch are carefully organized by myself.  B.blend is not listed in the files.

Is there a way to search the hard drive directly without using the index/database?
Is there a way to update the index/database to include every file in the HDD?
What is the easiest way to search the *entire* file system?

---

### Post by mb_webguy on 2009-04-29
Find will run from the current directory if none is provided.  Try "find **/** -name *.blend -print".

---

### Post by mkoehler on 2009-04-29
updatedb is used to update the database used in conjunction with the 'locate' command.  On the other hand, the 'find' command does a full search of the input location.  In your case, you did not provide a location, so the command should have searched the local directory.  The command I typically use is 

```
sudo find / -iname "*.blend"
```

Give that a shot - it should scan your entire HDD.  The full documentation for the command can be found by typing in "man find".  Cheers!

---

### Post by andrew.46 on 2009-04-30
Hi Buttons,

> **Buttons840 said:**
> Is there a way to search the hard drive directly without using the index/database?


I see others have answered your initial query but I think you may be interested in the first guide I have written in a projected *series* of guides:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

I would be interested to know if you found this type of guide useful or not?

All the best,

Andrew

---

