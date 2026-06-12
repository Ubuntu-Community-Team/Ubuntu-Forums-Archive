---
title: "checking spelling of latex file using aspell"
date: 2009-09-06
forum: Education &amp; Science
---

### Post by ashgard on 2009-09-06
Hey,

Im checking the spelling of my latex-files with

$ aspell -t check file.tex

This works perfectly, but does anyone know if it is also possible to use this command on multiple files at once? I'm unable to put it in a single line as:

$ aspell -t check file1.tex file2.tex

I've also tried to put it in a makefile (this is actually what I want, to run the spelling checker from a makefile)

...
spell:
    aspell -t check file1.tex
    aspell -t check file2.tex
....

But now only file1.tex is checked for spelling.

Anyone any suggestions?

Regards,
Ashgard

---

### Post by nateperson on 2009-09-07
A bash script should do the trick.

```
#!/bin/bash
aspell -t check file1.tex
aspell -t check file2.tex
aspell -t check file3.tex
```

Then you just add the script to the makefile.
[http://hbfs.wordpress.com/2008/10/14/spiking-makefiles-with-bash/]("http://hbfs.wordpress.com/2008/10/14/spiking-makefiles-with-bash/")

---

### Post by ashgard on 2009-09-07
That works perfectly! Thanks a lot :)

---

### Post by Simian Man on 2009-09-07
> **ashgard said:**
> 
I've also tried to put it in a makefile (this is actually what I want, to run the spelling checker from a makefile)

...
spell:
    aspell -t check file1.tex
    aspell -t check file2.tex
....

But now only file1.tex is checked for spelling.d

The reason this didn't work is that make stops running a target when one command reports failure (by returning a code other than 0).  In this case, aspell must return a non-zero value to indicate that stuff was spelled wrong.

---

### Post by Freelance Physicist on 2009-09-21
Wouldn't a better way be to make a bash script that accepts arguments?  This way you wouldn't have to edit the script every time you wanted to spell check a different file.

Something like this:

```
#!/bin/bash

for file in "$@"   # "$@" contains all the command line arguments passed to the program
do
  aspell -t $file
done
```

If you name the file, say, mspell.sh, you can call it like this:

```
$ ./mspell.sh file1.tex file2.tex ... etc
```

or

```
$ ./mspell.sh *.tex
```

to get every tex file at once.

---

### Post by leorolla on 2009-11-24
How can set aspell to ignore words containing special characters (other than !?.,) and numbers, like {E}instein or qre123wqert ?


Thank you!

---

### Post by leorolla on 2009-11-24
BTW,

 You may want this in the script:

 aspell --add-tex-command="eqref p" --add-tex-command="psfrag pP" --add-tex-command="special p" --encoding=iso-8859-1 -t check $file

---

### Post by cheshirekow on 2011-07-14
> **Simian Man said:**
> The reason this didn't work is that make stops running a target when one command reports failure (by returning a code other than 0).  In this case, aspell must return a non-zero value to indicate that stuff was spelled wrong.

You can override this by prefixing the command with a minus sign (-). This tells make not to quit if the result returns failure (also useful for the clean: target if you want to rm something that may not be there).

```

spell:
    -aspell -t check file1.tex
    -aspell -t check file2.tex

```

(note, if you copy and paste this, change the spaces into tabs).

---

