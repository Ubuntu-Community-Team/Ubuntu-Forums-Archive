---
title: "Nautilus: Bug with 7Zip"
date: 2006-09-23
forum: Desktop Environments
---

### Post by waffen on 2006-09-23
I installed 7zip fomr Synaptic and I open nautilus, right clik over a Directory (with others dirs and files inside) and select create archiver, chose .7z and the program only create a empty file with only 32 bytes in all cases.

Thats error not appear when I try to ziped only one file.

:confused:

---

### Post by moopoo on 2006-11-23
Hi,

I'd like to confirm this "file roller and p7zip" bug. The same happens on my Edgy machine.

Compressing multiple files works.
Compressing one or multiple empty folders works.
Compressing a folder with one or more files in it does **not** work.

I tried uninstalling p7zip, just having p7zip-full installed. It didn't help.

This is the output of the error message:

```
7-Zip (A) 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14
p7zip Version 4.42 (locale=de_DE.UTF-8,Utf16=on,HugeFiles=on,1 CPU)
Scanning


folder\file02:  WARNING: No more files                
folder\file01:  WARNING: No more files                
folder\file03:  WARNING: No more files                


Creating archive /home/*user*/Desktop/folder.7z



WARNINGS for files:

folder\file02 : No more files                
folder\file01 : No more files                
folder\file03 : No more files                
----------------
WARNING: Cannot find 3 files
```

The error occurs in both cases: a) Compressing the folder via context menu b) Running the Archive-Manager from the Gnome Panel. Creating an empty 7zip archive and dragging the folder into it.

yours,
moopoo

---

### Post by moopoo on 2006-11-26
I found out, that the bug is discussed here:

[https://launchpad.net/distros/ubuntu/+ticket/2302]("https://launchpad.net/distros/ubuntu/+ticket/2302")

Someone proposes to use the Feisty .debs, but I think that this is quite risky. It "cracked down" at least one system.

yours,
moopoo

---

