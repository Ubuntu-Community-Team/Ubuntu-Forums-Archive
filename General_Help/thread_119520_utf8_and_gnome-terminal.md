---
title: "utf8 and gnome-terminal"
date: 2006-01-19
forum: General Help
---

### Post by Román on 2006-01-19
How do I configure utf8 as the default character encoding in my gnome-terminal?

My locale is set to utf8

```

rgoro@in_horto_meo:~ $ locale
LANG=en_US
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=en_US.utf8
rgoro@in_horto_meo:~ $

``` 
But my gnome-terminal still thinks that the current locale is ISO-8859-1. How do I change that? I couldn't find gnome-terminal's configuration files.  What am I missing?

---

### Post by Dougal on 2006-01-20
Try looking in /etc/console-tools/

---

### Post by cutOff on 2006-01-20
Hi,
```
sudo dpkg-reconfigure locales
```

---

