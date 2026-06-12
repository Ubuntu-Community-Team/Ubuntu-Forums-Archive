---
title: "ls command and colors"
date: 2006-08-25
forum: Desktop Environments
---

### Post by utab on 2006-08-25
Dear all, 

Is there a way to list directories executables and files in a chosen color by the user? for instance executables in red, directories in yellow and normal files in green sth like this.

Regards,

---

### Post by John.Michael.Kane on 2006-08-25
This maybe of help [**ls command-color**]("http://pchowtos.co.uk/index.php?page=tutorials&action=view&id=71")

Then there's this.
[**ls-command-Color-defined**]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2004/12/where-is-color-of-ls-command-defined.php")

---

### Post by Phrawm48 on 2007-03-07
This is an old thread, but since I just figured this out, I'll add the suggestion that one look at the *dircolor* man page:

```
man dircolors
```

The *dircolors *program configures the *LS_COLORS* variable used by the *ls* command to colorize various types of entities displayed by *ls*.

You can also use dircolors to view current settings:

```
dircolors -p
```

---

