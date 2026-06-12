---
title: "Burn MPG to DVD"
date: 2007-10-02
forum: Desktop Environments
---

### Post by Djbb on 2007-10-02
I have a .mpg movie file on my desktop that I want burned to a DVD so I can watch it on my DVD player. I read another thread on this topic but I'm having trouble with the steps. Heres the log from my terminal.

tony@mom-laptop:~$ cd /home/mom/Desktop
tony@mom-laptop:~/Desktop$ dvdauthor -o dvd -t mma.mpg
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing mma.mpg...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
ERR:  SCR moves backwards, remultiplex input.
tony@mom-laptop:~/Desktop$ dvdauthor -o -T
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
ERR:  no titles defined
tony@mom-laptop:~/Desktop$ mkisofs -dvd-video -o dvd.iso dvd/
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for 'dvd/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

---

### Post by avik on 2007-10-02
I'm not sure about the command line program, but I use a front-end such as [dvdstyler]("http://www.getdeb.net/app.php?name=DVDStyler").  I found it simpler than trying to figure out the all the options.

Other than that, I would say some options are missing from the first command.  That or maybe something's wrong with the mpg file.

---

