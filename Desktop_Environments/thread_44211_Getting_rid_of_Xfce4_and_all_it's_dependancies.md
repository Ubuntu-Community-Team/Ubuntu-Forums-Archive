---
title: "Getting rid of Xfce4 and all it's dependancies"
date: 2005-06-24
forum: Desktop Environments
---

### Post by dresnu on 2005-06-24
Ok, this should be easy. I'm using kubuntu. I wanted to try xfce4 and so I downloaded it from the repos. Apart from the xfce4 package I got another 40 packages or so(64MB in total). I would like to know if there is a way to remove xfce with all its dependacies in one shot(not package by package). Thank you ;-)

---

### Post by jasmuz on 2005-06-24
[QUOTE=dresnu]Ok, this should be easy. I'm using kubuntu. I wanted to try xfce4 and so I downloaded it from the repos. Apart from the xfce4 package I got another 40 packages or so(64MB in total). I would like to know if there is a way to remove xfce with all its dependacies in one shot(not package by package). Thank you ;-)[/QUOTE]
 sudo dpkg -P xfce

---

### Post by Xian on 2005-06-24
[QUOTE=dresnu]I would like to know if there is a way to remove xfce with all its dependacies in one shot(not package by package).[/QUOTE]
I think you meant to say "dependencies not required by other packages". Xfce has a large number of deps that your system requires to function properly. If you were to remove them all it would make for a very unpleasant situation. This command should remove most (if not all) of the Xfce files and deps no longer needed.

```
$ sudo apt-get remove libxfce4util-1
```

---

### Post by dresnu on 2005-06-25
Yes that's what I needed, thx

---

