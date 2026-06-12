---
title: "Writing a simple script, need help!"
date: 2009-04-08
forum: General Help
---

### Post by dbsoundman on 2009-04-08
OK, all I'm trying to do is write a script that will open a terminal window, and run the command ```
ssh (user)@(domain)
```. What I have now is: ```
#! /bin/bash
gnome-terminal -e ssh user@domain
``` where "user" and "domain" are of course the correct credentials for this particular site, but I can't get the thing to run; it just seems to crash every time. I did this back in openSUSE long ago with no problem, using konsole instead of gnome-terminal. What's my syntax problem here? I did make the script executable too, so I know that's not it.

Thanks,
Dan

---

### Post by kerry_s on 2009-04-08
you should always check the man pages> man gnome-terminal

```
#!/bin/sh
gnome-terminal -**x** ssh user@domain
```

---

### Post by dbsoundman on 2009-04-08
Damn! I even read the man page, but I thought it said I could use -e as well. Thanks!

-Dan

---

### Post by KeyserSoze93 on 2009-04-09
> **kerry_s said:**
> you should always check the man pages> man gnome-terminal

```
#! /bin/sh
gnome-terminal -**x** ssh user@domain
```

I don't think ubuntu recognises a space in the hashbang (#!/bin/sh, as opposed to #! /bin/sh)

Other than that, it should work now.

---

### Post by dbsoundman on 2009-04-09
It works fine now, but I'll keep that space in mind if I have problems. I'll probably end up copying and editing these scripts over time as I need access to various different SSH servers for school and personal uses.

-Dan

---

### Post by kerry_s on 2009-04-09
> **KeyserSoze93 said:**
> I don't think ubuntu recognises a space in the hashbang (#!/bin/sh, as opposed to #! /bin/sh)

Other than that, it should work now.

ooops, must have fat fingered it. :lolflag:
it's fixed.

---

