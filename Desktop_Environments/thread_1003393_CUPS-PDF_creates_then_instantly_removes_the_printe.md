---
title: "CUPS-PDF creates then instantly removes the printed PDF"
date: 2008-12-06
forum: Desktop Environments
---

### Post by motin on 2008-12-06
I have installed cups-pdf and set up a virtual PDF printer according to the general instructions spread on blog posts and wikis. Now this has always worked fine in earlier versions of Ubuntu, but now in Intrepid, there is no PDF's to be found in ~/PDF after printing...

Switching on debug level logging in /etc/cups/cups-pdf.conf reveals the following upon printing:
```
Sat Dec  6 09:30:31 2008  [DEBUG] switching to new gid (lpadmin)
Sat Dec  6 09:30:31 2008  [DEBUG] initialization finished (v2.4.8)
Sat Dec  6 09:30:31 2008  [DEBUG] user identified (motin)
Sat Dec  6 09:30:31 2008  [DEBUG] output directory name generated (/home/motin/PDF)
Sat Dec  6 09:30:31 2008  [DEBUG] user information prepared
Sat Dec  6 09:30:31 2008  [DEBUG] spoolfile name created (/var/spool/cups-pdf/SPOOL/cups2pdf-16566)
Sat Dec  6 09:30:31 2008  [DEBUG] source stream ready
Sat Dec  6 09:30:31 2008  [DEBUG] destination stream ready (/var/spool/cups-pdf/SPOOL/cups2pdf-16566)
Sat Dec  6 09:30:31 2008  [DEBUG] owner set for spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-16566)
Sat Dec  6 09:30:32 2008  [DEBUG] found beginning of postscript code (%!PS-Adobe-3.0)
Sat Dec  6 09:30:32 2008  [DEBUG] now extracting postscript code
Sat Dec  6 09:30:32 2008  [DEBUG] found title in ps code (([ubuntu] Changing AnonDirName for CUPS-PDF - Ubuntu Forums))
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:32 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found embedded (e)ps code (%!PS-TrueTypeFont- 1)
Sat Dec  6 09:30:33 2008  [DEBUG] found end of embedded (e)ps code (%%EOF)
Sat Dec  6 09:30:33 2008  [DEBUG] all data written to spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-16566)
Sat Dec  6 09:30:33 2008  [DEBUG] trying to use PS title (([ubuntu] Changing AnonDirName for CUPS-PDF - Ubuntu Forums))
Sat Dec  6 09:30:33 2008  [DEBUG] removing trailing newlines from title (([ubuntu] Changing AnonDirName for CUPS-PDF - Ubuntu Forums))
Sat Dec  6 09:30:33 2008  [DEBUG] removing enclosing parentheses () from full title (([ubuntu] Changing AnonDirName for CUPS-PDF - Ubuntu Forums))
Sat Dec  6 09:30:33 2008  [DEBUG] removing special characters from title ([ubuntu] Changing AnonDirName for CUPS-PDF - Ubuntu Forums)
Sat Dec  6 09:30:33 2008  [DEBUG] title successfully retrieved (_ubuntu__Changing_AnonDirName_for_CUPS-PDF_-_Ubuntu_Forums)
Sat Dec  6 09:30:33 2008  [DEBUG] input data read from stdin
Sat Dec  6 09:30:33 2008  [DEBUG] output filename created (/home/motin/PDF/_ubuntu__Changing_AnonDirName_for_CUPS-PDF_-_Ubuntu_Forums.pdf)
Sat Dec  6 09:30:33 2008  [DEBUG] ghostscript commandline built (/usr/bin/gs -q -dCompatibilityLevel=1.4 -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="/home/motin/PDF/_ubuntu__Changing_AnonDirName_for_CUPS-PDF_-_Ubuntu_Forums.pdf" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f /var/spool/cups-pdf/SPOOL/cups2pdf-16566)
**Sat Dec  6 09:30:33 2008  [DEBUG] output file unlinked (/home/motin/PDF/_ubuntu__Changing_AnonDirName_for_CUPS-PDF_-_Ubuntu_Forums.pdf)**
Sat Dec  6 09:30:33 2008  [DEBUG] TMPDIR set for GhostScript (/var/tmp)
Sat Dec  6 09:30:33 2008  [DEBUG] entering child process
Sat Dec  6 09:30:33 2008  [DEBUG] GID set for current user
Sat Dec  6 09:30:33 2008  [DEBUG] UID set for current user (motin)
Sat Dec  6 09:30:33 2008  [DEBUG] ghostscript has finished (256)
Sat Dec  6 09:30:33 2008  [DEBUG] waiting for child to exit
Sat Dec  6 09:30:33 2008  [DEBUG] spoolfile unlinked (/var/spool/cups-pdf/SPOOL/cups2pdf-16566)
Sat Dec  6 09:30:33 2008  [DEBUG] all memory has been freed
```

Why deleting the generating PDF?

I have tried adjusting the apparmor profile for cups-pdf as mentioned in [http://ubuntuforums.org/showthread.php?t=786981](http://ubuntuforums.org/showthread.php?t=786981)...

```
#  @{HOME}/PDF/* rw,
  @{HOME}/PDF/** rw,
  /home/motin/PDF/** rw,
```

...but this seems not to be the problem in this case. Now it's restored to it's original state btw. 

I also don't want to purge all my cups configuration (as mentioned in [http://ubuntuforums.org/showthread.php?t=546444](http://ubuntuforums.org/showthread.php?t=546444)) as I'd prefer to keep my printers installed. The only modification to the configuration files I've is to run Cups as a user (as recommended in CUPS-PDF installation instructions). 

I'd love to be able to use my pdf printer - any ideas?

---

### Post by motin on 2008-12-22
Nobody?

I guess ghostscript is the problem here, it seems to exit with code 256 instead of 0 - explaining why there is no output file in the end, but where is ghostscript's debug output?

Am I the only one who installed cups-pdf and ran into this problem?

---

### Post by motin on 2008-12-22
Solved it!

It appears I had faulty permissions on /var/tmp, such that only root could write to it! And as ghostscript for some reason uses /var/tmp instead of /tmp, this made it silently fail. 

It is very buggy behavior that this is not reported accordingly in the logs, but at least it works great now!

---

