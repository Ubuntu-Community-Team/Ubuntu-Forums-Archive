---
title: "Emerald gone"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by jan247 on 2008-02-07
hi guys. updated Quattro's compiz debs today. problem is, emerald's no longer working. it used to work before the update. when i type emerald --replace, no window borders are displayed although no errors are showing either. i've tried the following steps as well:

- reinstalling emerald. both normal reinstall, and complete remove, then install
- switching from Quattro's compiz to ubuntu's default (then switched back after this didn't work)

i was wondering if there are any log files i can check? there seems to be no indication of any errors.. other than it not really working at all. thanks.

---

### Post by flamepanther on 2008-02-07
I'm having the exact same problem.  I'm using the AMD64 version of Gutsy.

---

### Post by Cygoku on 2008-02-07
Same here my friend ! :( Please, someone help !

Cygoku

---

### Post by Cygoku on 2008-02-07
I have this for you, when I type emerald --replace in a Terminal, I get this error message : 

(emerald:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

Cygoku

---

### Post by flamepanther on 2008-02-08
> **Cygoku said:**
> I have this for you, when I type emerald --replace in a Terminal, I get this error message : 

(emerald:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

CygokuInteresting.  I don't get that message if I try to execute Emerald from the terminal, but I *am* using the Aurora GTK engine.  It sounds like jan247 isn't getting any errors in the terminal either, so it doesn't seem like that should have anything to do with it.  I wonder if the current git of Compiz needs a newer version of Emerald for some reason.  The version that's available seems pretty old by comparison.

EDIT: Was there previously a version of Emerald available from Quattro's repo?  I can't recall, and since I've uninstalled the version I had, all that's available is the one from the official repositories.  It doesn't look like there's a version on Quattro's now (at last not for 64-bit), just the Emerald themes package.

---

### Post by jan247 on 2008-02-08
I'm not using aurora either. And yep, as far as i know, only emerald-themes is available from Quattro.

---

### Post by flamepanther on 2008-02-08
I guess this is a minor inconvenience more than anything, but I really am going to miss using the Adonis theme until there's a resolution.

---

### Post by jan247 on 2008-02-09
flamepanther, was this just a theme issue for you? I tried switching themes but no luck.

---

### Post by flamepanther on 2008-02-09
No, it's not a theme issue.

---

### Post by Cygoku on 2008-02-10
I am using a later version of emerald theme manager and also a later version of libemeraldengine0 version 0.6.9.9 both from 20071119 svn.  

Too bad it did not solve the problem here.  

Cygoku

---

### Post by flamepanther on 2008-02-12
There's also been another update to Compiz, but that doesn't seem to have fixed it either.

---

### Post by emerson999 on 2008-03-22
I just found out about Quattro's packages today, and found the same thing happened to me. Emerald started from the command line just stalls out with no feedback, and I'm left with borderless windows. Is this issue ongoing since the start of this thread, or any fix found?

---

### Post by jan247 on 2008-03-23
I'm afraid there hasn't been any fixes for me. I'm just waiting for the next version of Ubuntu 'til I reformat and start from scratch.

---

