---
title: "browse files root.disk w/o booting or mounting"
date: 2008-12-29
forum: General Help
---

### Post by creek23 on 2008-12-29
I wanted to view the files inside "root.disk" without booting Ubuntu (or mounting in Windows, if it's even possible).

Question is: is there an existing software for that?

The idea is to easily copy/extract a file from **root.disk** from inside Windows using a packing/unpacking software.

I imagine **root.disk** as a huge **tar** file, so it should be doable right?

7zip can browse/extract files from inside an ISO. If only someone will make a hack of that to open ***.disk*** files. But I don't think 7zip source code was released in entirety, is it?

---

### Post by ajgreeny on 2008-12-29
I don't quite understand what you are trying to do.  Is the root.disk a linux install or if not what is it, perhaps a disk image or something like that?

You can certainly "mount" a linux partition in windows using explorefs2, a free download, which lets you view but not write to a linux file system, and there are now file system drivers which let you read and write to ext3 partitions from within windows, but you say this is not what you want.

I don't think it will be possible to browse any files on a disk without the disk/partition being mounted at the very least.  More info please about exactly what you are trying to do and why.

---

### Post by creek23 on 2008-12-29
> **ajgreeny said:**
> I don't quite understand what you are trying to do.  Is the root.disk a linux install or if not what is it, perhaps a disk image or something like that?I posted this thread under Wubi. So I presumed *root.disk* is known to others as the virtual-disk-like file that Wubi creates.

> **ajgreeny said:**
> I don't think it will be possible to browse any files on a disk without the disk/partition being mounted at the very least.  More info please about exactly what you are trying to do and why.It is not a partition, so I can't mount it with [ext2fsd]("http://ext2fsd.sf.net") (or the likes). *root.disk* is like a disk image file intended for Wubi to read-from and write to.

To my understanding, this **root.disk** file is like an [Apple's Disk Image]("http://en.wikipedia.org/wiki/.dmg"), DMG, which contains files. But 7zip can extract the contents of a DMG file.

Since **root.disk** contains files too, I was thinking if it's possible for 7zip (or any other zip software) to browse/open/extract files from it.

What I want to do is find an existing software that does this.

Of course, I could have simply booted Ubuntu and copied the files I wanted and boot back to Windows. But I just want to ask if there's such a tool. If none, consider this as an idea for 7zip developers or Wubi developers to add as additional feature.

---

### Post by ajgreeny on 2008-12-29
Whoops!  Sorry, I didn't notice it was a wubi question, so it's just me rushing in too fast again.  I always get to forum pages from the RSS feeds in a bookmark on firefox and thus I tend not to notice which forum section the question is in.

---

### Post by creek23 on 2008-12-30
I guess the only way really is to [mount it with Live CD]("http://ubuntuforums.org/showthread.php?t=1007816").

---

### Post by Jammanuser on 2008-12-30
> **creek23 said:**
> I guess the only way really is to [mount it with Live CD]("http://ubuntuforums.org/showthread.php?t=1007816").

Ahh...I see you found my how-to! :D At least I now know it has been of use to at least **one** person! :P

Yes, you can mount it with the LiveCD, using the steps that I describe in that thread, or you can mount it from Windows with a program like [cygwin]("http://www.cygwin.com/"), which has the necessary tools to perform the task of mounting the root.disk from Windows! :)

Hope this helps! :popcorn:

-Jam man

:guitar:

---

### Post by creek23 on 2008-12-31
> **Jammanuser said:**
> ...or you can mount it from Windows with a program like [cygwin]("http://www.cygwin.com/")...geez, I didn't thought of that.

But still, having it to browse under (let's say) 7zip, would be great don't you think? ;)

---

### Post by Jammanuser on 2008-12-31
> **creek23 said:**
> 
But still, having it to browse under (let's say) 7zip, would be great don't you think? ;)

It would be, but unfortunately its a root.disk, not a ZIP...;)

Cheers! :)

-Jam man

:guitar:

---

### Post by creek23 on 2009-01-01
> **Jammanuser said:**
> It would be, but unfortunately its a root.disk, not a ZIP...;)But DMG is browseable by 7zip. Maybe they could do it too with *root.disk*.

---

