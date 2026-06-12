---
title: "qcomic-* directories and missing files"
date: 2014-01-12
forum: Desktop Environments
---

### Post by dargaud2 on 2014-01-12
Hello,
I'm investigating missing files and it seems linked to qcomicbook.

Some important files have recently disappeared from my /home structure (I'm talking hundreds of files).
Instead plenty of directories qcomic-123456789 have appeared (8 to 10 random digits), all dated to the first time I installed and used qcomicbook:

```
$ find -name qcomic-\* | wc -l
87

$ ll -d $(find -name qcomic-\*)
drwxr-xr-x 3 dargaud dargaud  4096 janv.  5 21:58 ./Corono/OTHER/qcomic-1793889537/
drwxr-xr-x 2 dargaud dargaud 12288 janv.  5 21:58 ./Dargaud/MISC/qcomic-1364805944/
drwxr-xr-x 6 dargaud dargaud  4096 janv.  5 21:58 ./Dargaud/MISC/qcomic-2097758587/
drwxr-xr-x 5 dargaud dargaud  4096 janv.  5 21:58 ./Dargaud/MISC/qcomic-906977449/
drwxr-xr-x 3 dargaud dargaud  4096 janv.  5 21:58 ./Dargaud/qcomic-354961753/
...
drwxr-xr-x 3 dargaud dargaud  4096 janv.  5 21:59 ./Dargaud/WebPageStuff/Websites/Various/qcomic-670492322/

```

Most of those contain the same file names:

```
$ ls ./Dargaud/Text/Antarctic/qcomic-121457687/
Configurations2  content.xml  META-INF  meta.xml  mimetype  settings.xml  styles.xml  Thumbnails

```

But some contain random files from other directories (either copies or moved):

```
$ ls ./Text/MOUNTAIN/qcomic-67738215
Guil154.tif  GUIL155.TIF  GUIL156.TIF  GUIL157.TIF  Guil84.tif  GUIL85.TIF  GUIL86.TIF  GUIL87.TIF  GUIL88.TIF

```
The above files are from a zip files that is GONE. It's still in my backup so I'm sure of it.

Now some of those are directories I haven't touched in years. Not even 'cd' inside.
And now all those qcomic dir appear at the time I did use qcomicbook to read a few .cbz on an nfs share. They are all dated Jan 5, same two times one hour apart.


It's a new PC with a fresh install of Kubuntu and smartctl reports no error.

```
$ ll Dargaud/MISC/qcomic*
Dargaud/MISC/qcomic-1364805944:
total 9332
-rw-rw-rw- 1 dargaud dargaud  59211 avril  3  2002 abricots.html
-rw-rw-rw- 1 dargaud dargaud   3586 avril  3  2002 ail.html
...
-rw-rw-rw- 1 dargaud dargaud   1428 avril  3  2002 viande.html
-rw-rw-rw- 1 dargaud dargaud    899 avril  3  2002 vinaigre.html

Dargaud/MISC/qcomic-2097758587:
total 68
drwxr-xr-x  6 dargaud dargaud  4096 janv.  5 21:58 ./
drwxrwx---  9 dargaud dargaud  4096 janv.  5 21:58 ../
drwxr-xr-x 11 dargaud dargaud  4096 janv.  5 21:58 Configurations2/
-rw-r--r--  1 dargaud dargaud  7309 sept. 17  2011 content.xml
-rw-r--r--  1 dargaud dargaud   532 sept. 17  2011 manifest.rdf
drwxr-xr-x  2 dargaud dargaud  4096 janv.  5 21:58 META-INF/
-rw-r--r--  1 dargaud dargaud  1041 sept. 17  2011 meta.xml
-rw-r--r--  1 dargaud dargaud    39 sept. 17  2011 mimetype
drwxr-xr-x  2 dargaud dargaud  4096 janv.  5 21:58 Pictures/
-rw-r--r--  1 dargaud dargaud  8606 sept. 17  2011 settings.xml
-rw-r--r--  1 dargaud dargaud 11425 sept. 17  2011 styles.xml
drwxr-xr-x  2 dargaud dargaud  4096 janv.  5 21:58 Thumbnails/

Dargaud/MISC/qcomic-906977449:
total 56
drwxr-xr-x  5 dargaud dargaud  4096 janv.  5 21:58 ./
drwxrwx---  9 dargaud dargaud  4096 janv.  5 21:58 ../
drwxr-xr-x 10 dargaud dargaud  4096 janv.  5 21:58 Configurations2/
-rw-r--r--  1 dargaud dargaud 12259 juil. 26  2009 content.xml
drwxr-xr-x  2 dargaud dargaud  4096 janv.  5 21:58 META-INF/
-rw-r--r--  1 dargaud dargaud   933 juil. 26  2009 meta.xml
-rw-r--r--  1 dargaud dargaud    46 juil. 26  2009 mimetype
-rw-r--r--  1 dargaud dargaud  7755 juil. 26  2009 settings.xml
-rw-r--r--  1 dargaud dargaud  6318 juil. 26  2009 styles.xml
drwxr-xr-x  2 dargaud dargaud  4096 janv.  5 21:58 Thumbnails/

```

ALL my openoffice odt files are GONE. Instead I find traces of them in the form of xml garbage in the qcomicbook directories. For example:

```
$ grep contester Dargaud/Text/Misc/qcomic-330375409/content.xml
Je souhaite contester la pr
$ odt2txt BACKUP/Dargaud/Text/Misc/MISSING_FROM_HOME.odt | grep contester
Je souhaite contester la pr

```

Questions:
- does qcomicbook indeed create those qcomic-123456789 directories ?
- does it explore /home to find zip files and open them ? 
- if so, how come they show up in so many old directories where I certainly have not opened it ?



My last backup is over a month old and there are so many differences that it's a ****ing nightmare. I want to know if qcomicbook is responsible for this and what happened.

---

