---
title: "Problem unzipping a file"
date: 2009-01-30
forum: General Help
---

### Post by JordyD on 2009-01-30
I downloaded Haiku [from haiku-os.org]("http://haiku-os.org/"), and when I tried to unzip it, I got this:```
Archive:  haiku.image.r29080.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of haiku.image.r29080.zip or
        haiku.image.r29080.zip.zip, and cannot find haiku.image.r29080.zip.ZIP, period.

```

Any idea what this means or how to fix it?

Thanks,
Jordy

---

### Post by ajgreeny on 2009-01-30
It means that you have just part of the total requirement for Haiku, which I assume means that there are other zip files available to make up the whole, which you will need and then will need to use them in the correct order, if it is similar to the way it happens in windows.  The last zip (I think) contains all the information for the program and you do not apparently have that on your zip file.

---

### Post by Mud.Knee.Havoc on 2009-01-30
I just downloaded the exact same .zip.  It works fine.  Try downloading it again - yours must be corrupted.

Or if you don't want to redownload it, compare yours to mine.  Run this in a terminal (in the directory where the file is located):

```
md5sum haiku.image.r29080.zip
```

and you should see this

```
94e4b4542deccef2978db9341a912640  haiku.image.r29080.zip
```

If that long and ugly string of numbers and letters doesn't match yours, your .zip is bad and you'll need to get it again.

---

### Post by JordyD on 2009-01-30
> **Mud.Knee.Havoc said:**
> I just downloaded the exact same .zip.  It works fine.  Try downloading it again - yours must be corrupted.

Or if you don't want to redownload it, compare yours to mine.  Run this in a terminal (in the directory where the file is located):

```
md5sum haiku.image.r29080.zip
```

and you should see this

```
94e4b4542deccef2978db9341a912640  haiku.image.r29080.zip
```

If that long and ugly string of numbers and letters doesn't match yours, your .zip is bad and you'll need to get it again.

Well, mine is definitely corrupted then.

Thanks, I guess I'll have to download it again.

---

