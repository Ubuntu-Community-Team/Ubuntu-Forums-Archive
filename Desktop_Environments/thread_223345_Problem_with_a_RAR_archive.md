---
title: "Problem with a RAR archive"
date: 2006-07-26
forum: Desktop Environments
---

### Post by pinkythepenguin on 2006-07-26
When exracting a .rar archive it displays the error messagee :

[/home/pinky/Desktop/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.mp4/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/pinky/Desktop/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.mp4/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip or
        /home/pinky/Desktop/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.mp4/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip.zip, and cannot find /home/pinky/Desktop/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.mp4/PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip.ZIP, period.

Any help would be appreciated 

(I know the films cheesey but I have still got to watch it!)

---

### Post by mogelhead on 2006-07-26
How do you extract it, from Nautilus file manager or from a terminal?

If terminal: what command are you using?

---

### Post by pinkythepenguin on 2006-07-26
I was using terminal with unzip (which I thought I used to do for .RAR ages ago

---

### Post by mogelhead on 2006-07-26
An you know it is a zip file? You keep mentioning rar. Rar and zip are two different archive formats.

The command 
```
file <filename>
```
will tell what kind of file it is. Replace <filename> with the correct one.

---

### Post by mogelhead on 2006-07-26
Also, there is a possibility that the file is corrupt (incomplete).

---

### Post by pinkythepenguin on 2006-07-26
file PSP\ -\ The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip
PSP - The.Fast.And.The.Furious.Tokyo.Drift.TS-maVen.zip: RAR archive data, v1d, os: Win32


thats the output of file - just noticed the os:win32?

Its a mp4 if that makes any difference ](*,)

---

### Post by mogelhead on 2006-07-26
The contents of the archive does not matter, neither the operating system on which the archive was created.

You need to extract it with the "unrar" command.

Rar (and unrar) is in the multiverse repository which you need to enable before installing.

[https://help.ubuntu.com/community/Repositories/](https://help.ubuntu.com/community/Repositories/)

---

### Post by pinkythepenguin on 2006-07-26
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
  

](*,)

---

### Post by mogelhead on 2006-07-27
Did you enable the multiverse repository?

---

### Post by Thund3rstruck on 2006-07-27
Rar and zip are different just as gunzip and bzip are different. Refer to [Wikipedia's archive format mapping]("http://en.wikipedia.org/wiki/List_of_archive_formats") for details. You must unrar the archive. Also this is a multi part (spanned) archive most likely from bitTorrent, usenet, or p2p so there is a very high probability of corruption. 

For installation details refer to [The Dapper Wiki - How to Install RAR]("http://ubuntuguide.org/wiki/Dapper#How_to_install_RAR_Archiver_.28rar.29")

---

