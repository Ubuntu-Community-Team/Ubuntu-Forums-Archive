---
title: "Checking and converting the Dos/Unix format of multiple files"
date: 2005-12-14
forum: General Help
---

### Post by Roobert on 2005-12-14
I have a tar package consisting of many (hundreds, easily) of both text and binary files. Specifically, my tar package is a [GRASS GIS ]("http://grass.itc.it/index.php")Location. Grass is a geographical information system used predominantly for spatial analysis, geological mapping, remote sensing/environmental applications, etc. I've been doing the work on a PC using Cygwin, and I've decided to try doing the work on the Ubuntu version of Grass. My problem is that I think that somehow an EOL conversion is happening implicitly somewhere either when the tar package is being written by tar in Cygwin, or during the ftp transfer, or some other way I'm not aware of.  The reason why I suspect this is because all of my raster files are broken in Ubuntu Grass (segmentation faults when I try to view them). 

Is there a way of checking the file mode-ness of a tar package? dos2unix won't work on these files, as all of my raster imagery is binary and will definitely get corrupted by using this utility. I've checked the settings in gftp and I'm certain that the file transfer mode is set to binary. Is there anything else I can do?

---

### Post by schilcha on 2005-12-15
Conversion from DOS to UNIX newlines is required for textfiles. Pictures do not require any conversion step. 

It seems, you transferred the tar-file with ftp. Did you make shure to turn binary mode in ftp.(I have to admit, I don't know if not turning on can actually break your files within the tar-package... But, I usually turn it on -- out of superstition.)

If you want to check the mode of your files, use the command "file *", which will give an informative description of the files' formats.

If you want dos2unix to act on text-files only, but you can't group them via wildcards (e.g. dos2unix *.txt), you might try:
```

for f in `file -F# * | grep -i text | cut -d# -f1`; do dos2unix $f; done

```
which will convert all text (readable) files.

Good Luck!

---

### Post by Roobert on 2005-12-15
[QUOTE=schilcha]It seems, you transferred the tar-file with ftp. Did you make shure to turn binary mode in ftp.[/QUOTE]

Yes. Several times.

[QUOTE=schilcha]If you want to check the mode of your files, use the command "file *", which will give an informative description of the files' formats.[/QUOTE]

Excellent. Thank you for this command, I didn't know it existed.

[QUOTE=schilcha]If you want dos2unix to act on text-files only, but you can't group them via wildcards (e.g. dos2unix *.txt), you might try:
```

for f in `file -F# * | grep -i text | cut -d# -f1`; do dos2unix $f; done

```
which will convert all text (readable) files.[/QUOTE]
Thank you! I'll give it a try.

---

