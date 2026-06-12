---
title: "Trying to make changes on main menu"
date: 2010-03-10
forum: Desktop Environments
---

### Post by carandraug on 2010-03-10
Hi

I'm trying to make some changes on Ubuntu's main menu but failing miserably. I want to change the command that runs when I click on the skype button. At the moment, there's only

```
skype
```

but I want to change it for

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

However, when I do it, I get an error. The error is in portuguese but I think in English it would be something like "Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory). I though the error could be related with having to use quotes. I tried

```

"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"
'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

```

But still get the error. I have no problem when I run it from a terminal

---

### Post by kerry_s on 2010-03-10
put the command in a bash file & point to that.

press> **alt+f2**
type> **gedit ~/bin/skype**
put:

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

make it executable:
type> **chmod +x ~/bin/skype**

---

### Post by asmoore82 on 2010-03-11
the above should work

-OR-

you can start off with the `env` command in the launcher,
so the full launcher command will be:
```
env LD_PRELOAD="/usr/lib/libv4l/v4l1compat.so" skype
```
^the quotation isn't strictly necessary here, but it makes me feel warm and fuzzy :razz:

---

### Post by carandraug on 2010-03-12
Thanks to both of you. I'll try them once I get home and then mark this as solved.

EDIT: I ended up using **asmoore82**'s advice and it worked fine. I think using env instead of a bash script seems more correct and less messy.

---

