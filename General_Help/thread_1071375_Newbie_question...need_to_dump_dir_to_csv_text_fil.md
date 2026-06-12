---
title: "Newbie question...need to dump dir to csv text file"
date: 2009-02-16
forum: General Help
---

### Post by toddk111 on 2009-02-16
I'm sure there is a way to do this but I don't know the command.  

I have many external hard drives and I'd like to inventory the files and keep them in a spreadsheet.  So I was wondering what command I can use to get all of the file names, dates, sizes from a drive (including subdirectories) and dump it to a csv text file.  I would later import it into a spreadsheet.

Any help would be appreciated.
Thanks!

---

### Post by geirha on 2009-02-16
```
find /path/to/external/drive -type f -fprintf file.csv '"%p","%t",%s\n'
```

Read the manual page of find to see what other info you can use. [http://manpages.ubuntu.com/manpages/intrepid/en/man1/find.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/find.1.html) or ```
man find
```
In particular look at the description of -printf.

---

### Post by toddk111 on 2009-02-16
Thanks!

---

