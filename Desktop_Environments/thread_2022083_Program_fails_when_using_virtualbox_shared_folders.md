---
title: "Program fails when using virtualbox shared folders"
date: 2012-07-10
forum: Desktop Environments
---

### Post by dargaud on 2012-07-10
Hello all,
this is a complex question because it deals with WinXP, VirtualBox, Ubuntu and a specific Windows executable.

So I have a program (SilkyPix, a RAW image processor) that runs in a VirtualBox session on my Ubuntu machine. It used to run fine, but the last (expensive) upgrade now has problems: it works fine on local RAW files, but it fails when the files are on a VirtualBox shared folder. It's like the program cannot create its destination files there.

It used to run fine, so the permissions should be OK, and I can create files there with Windows without problem. Other Windows programs have no problems... Well, now that I think about it, one other program, an IDE editor, also has problems.

```
$ ll -d / /Ter /Ter/Large1 /Ter/Large1/Pictures /Ter/Large1/Pictures/2012 /Ter/Large1/Pictures/2012/2012070*
drwxr-xr-x 28 root    root     4096 Jul  1 18:14 //
drwxr-xr-x 11 root    root     4096 Feb 13 19:41 /Ter/
drwxrwxr-x 21 dargaud dargaud  4096 Mar 17 19:52 /Ter/Large1/
drwxrwxr-x 25 dargaud dargaud  4096 Jan 15 15:56 /Ter/Large1/Pictures/
drwxrwxr-x 61 dargaud dargaud 36864 Jul  8 19:52 /Ter/Large1/Pictures/2012/
drwxrwxr-x  3 dargaud dargaud 57344 Jul 10 00:03 /Ter/Large1/Pictures/2012/20120707_MG40_AnneesFolles/
drwxrwxr-x  4 dargaud dargaud 36864 Jul  9 23:57 /Ter/Large1/Pictures/2012/20120707_MG40_Riviere/
drwxrwxr-x  3 dargaud dargaud 20480 Jul 10 12:07 /Ter/Large1/Pictures/2012/20120708_MG40_Matin/

$ grep vb /etc/passwd /etc/group
/etc/group:vboxusers:x:124:dargaud
```

---

### Post by SeijiSensei on 2012-07-10
Maybe it's looking for some NTFS primitives it can't find in the shared folder formatted with ext?

How about this?  Do you have any extra space on the drive, or perhaps an external device?  Try creating a separate partition and formatting that with NTFS.  Then make that the shared folder.  Any better?

How about using a network drive instead?  Share a directory off a Windows box and mount it in the VM using "map a network drive".

Must be really chilly down there in July!

---

### Post by dargaud on 2012-07-10
Yes, strange NTFS requests is what I'm thinking about also, but the question is, why does it work with standard Samba exports while it fails with VirtualBox exports ? My guess now is that it has nothing to to with Ubuntu and it's a VB bug.

I don't see how I can make and export an NTFS partition using Linux (nor do I want to !!!)

---

