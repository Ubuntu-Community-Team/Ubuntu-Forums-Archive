---
title: "mass recursivel file rename help"
date: 2009-01-24
forum: General Help
---

### Post by bhirning on 2009-01-24
i opened an iso and all the files have an ";1" appended to the end of the file name. Ex: readme.chm;1 comsc.ttf;1 etc...  (5000+ files) 

i found this code to rename file extension but i am unsure how to alter it to read every file to remove the last 2 characters in every directory recursively. im not good with regex.

find <directory> -name '.*' -prune -o -exec rename 's/\.jpg$/\.JPG/i' {} +

---

### Post by mb_webguy on 2009-01-24
If you're unfamiliar with regex syntax, I'd highly recommend using GPRename to do batch renaming of files.  It's a GUI batch renamer in the repositories, and is considerably easier than using commands in the terminal.

---

### Post by bhirning on 2009-01-24
ok i found the site for gprename. i will see how that goes. thankyou

---

### Post by kaibob on 2009-01-24
If you want a command-line solution:

```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

The -n option tells rename to do a dry run and report proposed changes; substitute -v for -n to actually rename the files.

If you're looking for a GUI solution, take a look at pyrenamer:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

It's in the repo's.

---

### Post by bhirning on 2009-01-24
> **kaibob said:**
> If you want a command-line solution:

```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

The -n option tells rename to do a dry run and report proposed changes; substitute -v for -n to actually rename the files.

If you're looking for a GUI solution, take a look at pyrenamer:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

It's in the repo's.

it works :) thank you very much.

---

