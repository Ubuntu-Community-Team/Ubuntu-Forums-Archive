---
title: "Shell script help for mkdir and mv-ing lots of files"
date: 2009-06-03
forum: General Help
---

### Post by sun2z_emily on 2009-06-03
Hello,
I downloaded AssaultCube_v0.93.2-Update-Source.zip from sourceforge, it consist the source for an older version of AssaultCube binary.
The thing is when I extracted the file, i found out that the directory structure and file names are messed up. Here is a part of it

```
2007-06-04 21:35:24 .....         2419         2228  xcode\Main.gif
2007-06-04 21:12:58 .....          125          105  xcode\main.m
2006-11-06 20:26:30 .....          318          230  xcode\SDLMain.h
2007-06-04 21:10:30 .....        11902         3924  xcode\SDLMain.m
2007-06-04 21:35:24 .....         2926         2805  xcode\Server.gif
2007-06-04 21:54:54 .....        56586         6903  xcode\actioncube.xcodeproj\project.pbxproj
2007-06-04 21:11:20 .....          632          240  xcode\English.lproj\InfoPlist.strings
2006-11-06 20:27:12 .....          382          195  xcode\English.lproj\MainMenu.nib\classes.nib
2006-11-06 20:27:12 .....          614          324  xcode\English.lproj\MainMenu.nib\info.nib
2006-11-06 20:27:12 .....        11149         7457  xcode\English.lproj\MainMenu.nib\keyedobjects.nib
2006-11-06 20:27:12 .....         5112         2713  xcode\English.lproj\MainMenu.nib\objects.nib
------------------- ----- ------------ ------------  ------------------------
                               3069978       722553  185 files, 0 folders

```

Somehow the folder names are written as part of the file names, and the directory structure is gone. One way to fix it is mkdir the missing folders based on the file names and mv-ing everything manually. Thing is it will take some time. Now is it possible to use bash script for this? I'm not proficient in shell coding (or coding of any kind).
Or at the very least how can i remove parts of the filename that was the folder name (xcode\English.lproj\MainMenu.nib\objects.nib become English.lproj\MainMenu.nib\objects.nib or objects.nib). mkdir all of the folder manually is doable, then I can rename them automatically.

Thank you

---

### Post by alberto ferreira on 2009-06-03
first save the file with the name of the files and directory structure:
```
val = `grep '\\' $file | awk -F"\\" '{print $1}'`
``` -this gives you the first occurence behind a "\" so you can do a mkdir with $val

---

