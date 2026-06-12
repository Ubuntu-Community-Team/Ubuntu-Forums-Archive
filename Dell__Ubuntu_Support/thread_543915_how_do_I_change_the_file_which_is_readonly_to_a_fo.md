---
title: "how do I change the file which is readonly to a format so that I can delete it"
date: 2007-09-05
forum: Dell  Ubuntu Support
---

### Post by chaitanyakrs on 2007-09-05
guys I recently switched form windows lo ubuntulinux...some files I couldnt jus delete even form root log...how to i do it?

---

### Post by eentonig on 2007-09-05
I don't know what you mean with 'root log'

But what happens when you try

> sudo rm /path/to/filename

But maybe wiser would be to ask.... what files do you want to delete?

---

### Post by chaitanyakrs on 2007-09-05
i am trying to delete read only files.......
i tried rm command but these files wouldn't be deletd so i logged in as a root and tried the same..den i realised that there must be some problem with mounting.....so how to correct that and delete these readonly files

---

### Post by Compyx on 2007-09-05
Make that file writable:
```

chmod +w file

```

On the other hand, if that file is on a file system which has been mounted read-only then you'll have to unmount that file system and remount it writable.
I suggest you try:
```

man mount

```
and read about the various options you can pass to the `mount` command.

---

### Post by PeggySue on 2007-09-06
I had real problems getting to grips with this when I started Linux and it gets worse when you talk about disk ownership!  There is a quick and easy fix if you haven't sorted it already but I suggest you search for Linux "file permissions" and "file ownership" and read up on the subject.  It is one of the cornerstones of Linux and worth understanding.  Remember there are users of documents, the users belong to groups and then there could be others who are not part of your group.  Also files can be read only, read/write and executable.  

The quick fix is to open a terminal (Applications/accessories/terminal) and type sudo nautilus.  This opens the windows like browser.  You can navigate to the file you are interested in from File System/home/..your user name.., right click to see the proerties, select permissions and change the file from read only if that is what you want or just delete it.

Take care!! SUDO means you can delete things that perhaps you shouldn't.  Double check that you really want to delete the file.  Exit nautilus as soon as possible.

---

### Post by neptho on 2007-09-06
Where are these files located?  If they're on the Windows partition, you'll need to install NTFS-3g for full (stable) read and write access.  By default, the old NTFS driver is read only.

---

