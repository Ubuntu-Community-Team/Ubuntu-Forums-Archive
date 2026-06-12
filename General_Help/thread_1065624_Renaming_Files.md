---
title: "Renaming Files"
date: 2009-02-10
forum: General Help
---

### Post by Morgazmo on 2009-02-10
Hey guys..

       I've got a bunch of files to rename.. I've looked thru some forums and I've tried a bunch of programs.. Seems like the batch rename I want to do is a little trickier. I have a whole bunch of files which are for example "001 - DATA - MOREDATA.ext". I want to swap the MOREDATA and DATA parts of the filename. Can anyone think of a script to do this? I'm at a loss... Any help appreciated. Cheers.

---

### Post by adamlau on 2009-02-10
Thunar Bulk Rename :) .

---

### Post by mb_webguy on 2009-02-10
GPRename and KRename are both good batch renamers.  Though you're going to have to look into regular expressions either way, if you're wanting to swap sections of the filenames like that.

---

### Post by geirha on 2009-02-10
The rename command is nice.
```
$ ls -1 *.ext
001 - DATA - MOREDATA.ext
002 - FOO - BAR.ext
$ rename -v 's/(\S+) - (\S+) - (\S+).ext/$1 - $3 - $2.ext/' *.ext
001 - DATA - MOREDATA.ext renamed as 001 - MOREDATA - DATA.ext
002 - FOO - BAR.ext renamed as 002 - BAR - FOO.ext
$ ls -1 *.ext
001 - MOREDATA - DATA.ext
002 - BAR - FOO.ext

```

---

### Post by mb_webguy on 2009-02-10
> **geirha said:**
> The rename command is nice.
```
$ ls -1 *.ext
001 - DATA - MOREDATA.ext
002 - FOO - BAR.ext
$ rename -v 's/(\S+) - (\S+) - (\S+).ext/$1 - $3 - $2.ext/' *.ext
001 - DATA - MOREDATA.ext renamed as 001 - MOREDATA - DATA.ext
002 - FOO - BAR.ext renamed as 002 - BAR - FOO.ext
$ ls -1 *.ext
001 - MOREDATA - DATA.ext
002 - BAR - FOO.ext

```

And that's exactly what I was talking about when I mentioned regular expressions.  Linux users and regex are the original love-hate relationship. ;)

---

### Post by ataraxic on 2009-04-30
Yet another useful batch renaming.
Rename all **.jpg* files in **.c* in cwd:
**for i in `dir`; do j=`echo $i | sed 's/\.jpg$/\.c/g'`; mv "$i" "$j"; done;**

---

