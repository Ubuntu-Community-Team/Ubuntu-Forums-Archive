---
title: "UTF-8 and ASCII files."
date: 2006-07-28
forum: Desktop Environments
---

### Post by musther on 2006-07-28
I have a number of UTF-8 files.  Traditionally I index text files (for a use I'm not going to get into here) using a small command line app, for which I have a nautilus script.  Unfortunately the little command line app I use only supports good old ASCII files, and makes a bit of a hash of my UTF-8 files.  SO what I'm looking for is a command line method of converting my UTF-8 files to ASCII.  I've tried the following:

```
tr -dc "[:print:]" < file
```
Which didn't seem to do anything, the resulting file was 'exactly' the same size as the original.

```
cat file |tr -dc "[:print:]" > newfile
```
Which made an odd mess of my file, stripping everything, newlines and '-' characters included.

Any suggestions?

---

### Post by stdragon on 2006-07-28
Hey,

If you have Tcl installed (probably do) then you can use this simple script to convert the file:

```

#!/usr/bin/tclsh

fconfigure stdout -encoding iso8859-1
fcopy stdin stdout

```

Usage: ./utf8convert < utf8file > outputfile

If you really want plain ascii then change "iso8859-1" to "ascii". Be warned that "bad" characters such as é will be replaced by question marks in the output.

---

