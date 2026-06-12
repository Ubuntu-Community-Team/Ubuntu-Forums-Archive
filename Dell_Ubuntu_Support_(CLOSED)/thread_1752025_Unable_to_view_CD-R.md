---
title: "Unable to view CD-R"
date: 2011-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-05-07
Hello,

My father received CD-R that has an MRI and would like to view it on computer. I popped the CD-R into my Ubuntu (which is on Dell Inspiron 1545n), and it doesn't play. 

When I double click the CD-R to open, there is an icon, start.exe, but when I click that it says


[/media/disk/Start.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/disk/Start.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/disk/Start.exe or
          /media/disk/Start.exe.zip, and cannot find /media/disk/Start.exe.ZIP, period.


How do I fix this?

---

### Post by Vishnu V on 2011-05-07
exe files are not  directly supported by Ubuntu or any other gnu/linux.
We need an emulator to run this type of files.Wine will help you to run exe files. You can install it from Ubuntu software center

---

### Post by RSASKA on 2011-05-08
> **Vishnu V said:**
> exe files are not  directly supported by Ubuntu or any other gnu/linux.
We need an emulator to run this type of files.Wine will help you to run exe files. You can install it from Ubuntu software center


Thank you!

I just installed Wine,will try running the CD-R later today.

---

