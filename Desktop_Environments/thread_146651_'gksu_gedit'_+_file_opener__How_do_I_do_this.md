---
title: "'gksu gedit' + file opener?  How do I do this?"
date: 2006-03-18
forum: Desktop Environments
---

### Post by naked on 2006-03-18
I want to execute a command that runs gedit with root privies, but prompts me for a file?

My son was cramming on the keyboard and out of no where an very simple open location box appear.  I had no windows open either.

Anyone know how to do this?

L

---

### Post by taurus on 2006-03-18
Try
```

sudo gedit

```

---

### Post by drewbie on 2006-03-18
you probably mean using Alt-F2 to bring up the run box, and then using

gksudo gedit /path/to/file

or just 'gksudo gedit' and then opening the file from the program

---

