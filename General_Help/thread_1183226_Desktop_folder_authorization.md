---
title: "Desktop folder authorization"
date: 2009-06-09
forum: General Help
---

### Post by ultimatebuster on 2009-06-09
Everytime I try to extract something or copy something to desktop (90% of the time), it tells me I do not have enough authorization. I can only do these stuff with sudo under command-line.

How can I change this because I use my desktop as a temp folder for extracting, copy/paste etc very often and I don't want to use sudo everytime i try to extract something

---

### Post by michy99 on 2009-06-09
Open a terminal, enter this command, and post the result here.```
ls -ld Desktop
```

---

### Post by ultimatebuster on 2009-06-10
I got this
```
drwxr-xr-x 2 ultimatebuster ultimatebuster 4096 2009-06-09 21:14 &#26700;&#38754;
```

BTW, my interface is in Chinese therefore it ends with &#26700;&#38754; instead of Desktop

---

### Post by ad_267 on 2009-06-10
Your desktop directory permissions look fine, you should be able to copy files to there and create files. Can you give an example of what you're trying to do and the error you get.

---

### Post by escjohn on 2009-06-10
Try this in the terminal.
gksudo nautilus

---

### Post by michy99 on 2009-06-10
> **escjohn said:**
> Try this in the terminal.
gksudo nautilus

The point is, you shouldn't need root permissions to copy a file to your Desktop.

---

### Post by ultimatebuster on 2009-06-11
This usually happens when I try to extract something, or downloading a file from a email client like exchange (FirstClass). Occasionally when I download something from Firefox

---

