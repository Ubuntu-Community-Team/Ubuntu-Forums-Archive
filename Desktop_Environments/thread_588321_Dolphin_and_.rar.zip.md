---
title: "Dolphin and .rar/.zip"
date: 2007-10-23
forum: Desktop Environments
---

### Post by atlefren on 2007-10-23
I've upgraded to kubuntu 7.10 and kinda like Dolphin (although it has its weak and strong sides). However, i'm wondering if it is possible to change  the default compress-format used in the "compress here" and "compress" buttons on the information bar. 

I understand that .tar.bz is the linux native compression format, but my windows-using friends and lecturers kinda expects zip/rar when i send a mail etc. 

So does anyone have any hints on how to change dolphin so that it creates zip or rar files when i use the compress-option. I have installed rar/zip-support in ark and can create those files from there, but when dolphin gives these kinds of shortcuts it would be great to be able to do it from there.

---

### Post by hazelkid on 2007-11-01
I had the same problem. Here is a workaround. You have to manually edit (as superuser) the file:

```
/usr/share/apps/d3lphin/servicemenus/compress.desktop
```

This is the initial file on my machine:

```
[Desktop Entry]
ServiceTypes=all/allfiles
Actions=CompressTarGz;CompressTarBz2
X-KDE-Priority=TopLevel
X-KDE-Submenu=Compress

[Desktop Action CompressTarGz]
Name=Gzipped Tar Archive
Icon=ark
Exec=ark --add-to %U Archive.tar.gz

[Desktop Action CompressTarBz2]
Name=Bzip2-ed Tar Archive
Icon=ark
Exec=ark --add-to %U Archive.tar.bz2

```

And this is the modified one with Dolphin ZIP and RAR support:

```
[Desktop Entry]
ServiceTypes=all/allfiles
Actions=CompressTarGz;CompressTarBz2;CompressZIP;CompressRAR
X-KDE-Priority=TopLevel
X-KDE-Submenu=Compress

[Desktop Action CompressTarGz]
Name=Gzipped Tar Archive
Icon=ark
Exec=ark --add-to %U Archive.tar.gz

[Desktop Action CompressTarBz2]
Name=Bzip2-ed Tar Archive
Icon=ark
Exec=ark --add-to %U Archive.tar.bz2

[Desktop Action CompressZIP]
Name=ZIP Archive
Icon=ark
Exec=ark --add-to %U Archive.zip

[Desktop Action CompressRAR]
Name=RAR Archive
Icon=ark
Exec=ark --add-to %U Archive.rar
```

All you have to do is add new sections : [Desktop Action <YourAction>] as the ones above and then add the actions to the Actions list.

Happy hacking :)

edit: You could also change the ark call parameters to create the archive in the current folder and not your home folder :)

---

### Post by atlefren on 2007-11-01
Thanks! This worked like a charm

---

### Post by Rogon on 2007-11-15
Thanks a lot! Works perfectly

---

### Post by the_darkside_986 on 2008-03-16
That didn't work at all. Luckily, Konqueror still works and is able to do that. I never really cared too much for Dolphin. It looks too much like Vista's version of Windows Explorer.

---

