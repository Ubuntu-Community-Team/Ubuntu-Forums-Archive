---
title: "copying folders"
date: 2010-09-09
forum: Desktop Environments
---

### Post by fred44nl on 2010-09-09
hi,
I have placed a new, much larger hard disk in my PC and installed Ubuntu 10.4 on it.
after making a connection to my Time Capsule, I want to copy a large numer of files, stored in various folders, to my new hard drive.
it appears that the copy-process cannot create folders.
I can make a folder myself, and than I can copy files into it from the TC.
what is it, that I'm overlooking ??
thnks

---

### Post by Brandon Williams on 2010-09-09
When you say "the copy-process", do you mean the program cp? If so, then you're looking for the -R flag (a.k.a. -r or --recursive), which tells cp to copy directories recursively. Without it, cp will just say "omitting directory foo".

---

### Post by fred44nl on 2010-09-09
I am using the filemanager Nautilus.
I just installed muCommander and that seems to work.
would be pleased if Nautilus could do the job also.

also with muCommander, there are folders which can't be read.
but with my Macbook and WinXP laptop, I can do just that.
stange, don't you think

---

