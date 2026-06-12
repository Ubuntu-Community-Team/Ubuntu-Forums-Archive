---
title: "rar file tests OK, won't extract"
date: 2009-05-30
forum: General Help
---

### Post by max_brasil on 2009-05-30
I downloaded a multivolume rar file.
unrar t   lists all files as OK but

unrar e (or x) just says "skipping <filename>" and doesn't extract anything.

Any ideas?
Thanks

---

### Post by tommah04 on 2009-05-31
did you try using sudo?

---

### Post by max_brasil on 2009-05-31
Sorry, sudo didn't work...

william@wood-designs:~/music/Sheffield/Elton John$ sudo unrar e *
Password:

RAR 3.30    Copyright (c) 1993-2004 Eugene Roshal    22 Jan 2004
Shareware version         Type RAR -? for help

Enter password (will not be echoed) for Eljo_Goyebriro.part1.rar:


Extracting from Eljo_Goyebriro.part1.rar

Skipping    Elton John - Goodbye Yellow Brick Road [SC 180g DoLP][24-96]/Elton J ohn - Goodbye Yellow Brick Road.cue
Skipping    Elton John - Goodbye Yellow Brick Road [SC 180g DoLP][24-96]/A1 - Fu neral for a Friend_Love Lies Bleeding.flac
User break
william@wood-designs:~/music/Sheffield/Elton John$

---

### Post by Sycron on 2009-05-31
Are you sure that the rar password is correct?

---

### Post by ActiveFrost on 2009-05-31
File name is too long - that's why it's "skipping" these files !

---

### Post by bacardiandwatermelon on 2009-05-31
Does archive manager extract the files?

---

### Post by max_brasil on 2009-05-31
First of all, a big thank youto all who have responded so far.
The rar password is correct. I tried it with a wrong pwd and it immediately stops and doesn't even "try" extracting.

File names too long...  Some program compacted them, there certainly must be a way to extract them.
-> This just in: unrar rn *.rar renamed the files to fixed*.rar but only in the first volume. Is there a switch to get unrar to rename the files in all the volumes?

When I try to open the rar file with archive manager, it doesn't give me the chance to give the password. How do I pass the password to archive manager?

Thanks again.

---

### Post by max_brasil on 2009-06-02
Just to close this thread, I ended up using WinRAR on a Windoze machine. It worked, what can I say?
Anybody have an idea why?

---

### Post by pigphish on 2009-09-05
The windows gui WinRar creates these part files instead of the more conventional rXX. 

Extract from the last part file and file-roller ( default Ubuntu archive manager ) should be smart enough to start from the beginning and extract all the files.

---

