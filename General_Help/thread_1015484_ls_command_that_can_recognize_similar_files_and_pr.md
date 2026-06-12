---
title: "ls command that can recognize similar files and print the pattern instead of it all"
date: 2008-12-18
forum: General Help
---

### Post by Solidcell on 2008-12-18
I was wondering if there's a command or an option for ls that will recognize command filenames and use a pattern to save space and not print so much.

For instance, if I have 50 rar files of the form abc-gow.rXX where XX ranges from 0 to 49, then is there a command that will print:

abc-gow.r[0-49] (or something similar)

instead of:
abc-gow.r0
abc-gow.r1
abc-gow.r2
abc-gow.r3
...

I ask because I don't like to have to pipe ls's output to less and have to scroll.

Any suggestions would be much appreciated.

Edit: I know I can make a script to do it if necessary, but I'd rather use a standard command if there is one.  If it has to be a script, does anyone have one already?

---

### Post by dcstar on 2008-12-19
> **Solidcell said:**
> I was wondering if there's a command or an option for ls that will recognize command filenames and use a pattern to save space and not print so much.

For instance, if I have 50 rar files of the form abc-gow.rXX where XX ranges from 0 to 49, then is there a command that will print:

abc-gow.r[0-49] (or something similar)
......?

```
man find
```

---

### Post by geirha on 2008-12-19
ls does not accept any kind of patterns; what you are asking for is how the shell can expand those filenames based on a pattern. Any of these should list those r00-r49-files with ls.

```

# Loose match
ls abc-gow.r??
# Match r<digit><digit>
ls abc-gow.r[0-9][0-9]
# Match only r00-r49
ls abc-gow.r[0-4][0-9] 

```

Read about filename expansion in bash's man-page. [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

---

### Post by Solidcell on 2008-12-19
haha, two very different replies, but neither answers it.

I don't want to *supply* the pattern, i want ls to *output* the pattern.

I want it to group similar filenames when they occur.

For instance, 50 rars being myfile.r0-myfile.r49 should be output by this hypothetical ls as: myfile.r[0-49], and not as 50 items taking up way too much room on my terminal.

I'm not wanting to use grep or any grep-like tool, because this should be a general ls-like command, there should be no input from the user...

---

### Post by Solidcell on 2008-12-20
aww, I guess it requires a custom script.  seems like it would have been a good option for ls.  bummer.  If I get around to writing it, I'll post it here (it'll be in ruby though).

---

