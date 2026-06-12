---
title: "Renaming downloaded files with wget?"
date: 2009-03-18
forum: General Help
---

### Post by brownbat on 2009-03-18
There are a bunch of files online "http://fake.url/334.pdf", "http://fake.url/5536.pdf" and "http://fake.url/2.pdf", say. I want to save them to my machine as "/foo/natasha.pdf", "/foo/wombat.pdf" and "/foo/tau.pdf" (where the directory "foo" does not yet exist).

Priority is the renaming, directory placement is simple enough after the fact.

Turning to wget's man, I find:

> -O file
--output-document=file
    The documents will not be written to the appropriate files, but all will be concatenated together and written to file. ...

I do not want to concatenate several files, but to simply rename them as I go, keeping them in separate files.

Is this sort of "Save As..." unsupported by wget, in which case I should use some sort of script that combines wget with other tools?

Or can I put a new -O *file* after every file to get these results I want?

Is there another approach I'm missing?

Thanks in advance for any suggestions you have!

---

### Post by t0p on 2009-03-18
I too long for renaming.  But I haven't been able to find a suitable option in the manual.  So I'm stuck with renaming after downloading.

Of course, the man page is not the final authority.  As it tell us:

> This is not the complete manual for GNU Wget.  For more complete information, including more detailed explanations of some of the options, and a number of commands available for use with .wgetrc files and the -e option, see the GNU Info entry for wget.

Maybe you'll find your solution there...

---

### Post by flyingsolow on 2009-03-18
You could use the -O option for single file wget's. Multiple files might require fancy bash'ing?

---

### Post by KeyserSoze93 on 2009-03-18
Perhaps this fancy bash'ing will work?

```

echo "http://fake.url/334.pdf natasha.pdf
http://fake.url/5536.pdf wombat.pdf
http://fake.url/2.pdf tau.pdf" |
awk '{print "wget "$1" -O "$2}' |
bash

```

I don't know how much of it makes sense, but just put it all in a script file (in your home dir), with a name like dlfiles.sh, and then run:

```
bash ~/dlfiles.sh
```

For each in the echo statement, put in the URL, followed by the desired filename.

---

### Post by brownbat on 2009-03-18
Just what I needed, thanks!

---

