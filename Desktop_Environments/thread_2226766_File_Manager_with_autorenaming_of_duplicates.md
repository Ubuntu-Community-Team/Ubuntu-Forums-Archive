---
title: "File Manager with autorenaming of duplicates"
date: 2014-05-28
forum: Desktop Environments
---

### Post by didshukaj on 2014-05-28
My question is about file renaming

I rename a lot of pics simply putting tags into names, so that few tags combine into a name. In Windows 7, in case if I rename some file using filename that already exist (say, "file_name"), Explorer automatically renames new file into "file_name (1)", then "file_name (2)" etc. Is there some native linux file manager (nautilus gives options skip or replace, nemo adds to it rename options, but you have to enter name manually)(or pictures manager) capable of this, preferably with preview capabilities, or is it possible to run explorer on wine. Because currently I have to run win7 on Virtual Box just for the sake of renaming pictures (It's hundreds of pics and adding, so figuring out some time to just complete it will not work)

Thank You in Advance

---

### Post by TheFu on 2014-05-29
I don't know of a GUI way, but there is an extremely powerful **rename** tool from perl that uses regex.  I have a script that renames my photos (usually a few 1,000 after every trip).

```
#!/bin/bash
rename 's/^IMG_.//g' IMG*
rename -f 's/JPG/jpg/g' *JPG
rename 's/^014//g' 014*

#  MVI_0426.MOV  --> 0426.mov
rename 's/^MVI_//g' *MOV
rename 's/MOV$/mov/g' *MOV

# Fix Panorama photos
rename 's/.jpg/-pano.jpg/g' ST*
rename 's/ST._0//g' ST*

```
Of course, these are for the output from my PnS camera - yours probably names files differently.  I like to put tags inside the Exif fields along with other data like GPS, City, State, Country, and a nice description so these things can be searched later.  Sadly, I find the tools to accomplish this lacking, so I'm building my own.
[http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) may be helpful too.

---

