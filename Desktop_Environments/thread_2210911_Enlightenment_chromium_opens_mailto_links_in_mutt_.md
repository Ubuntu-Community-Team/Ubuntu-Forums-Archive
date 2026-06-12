---
title: "Enlightenment chromium opens mailto links in mutt instead of Thunderbird"
date: 2014-03-13
forum: Desktop Environments
---

### Post by frisket on 2014-03-13
Since installing Enlightenment e17 under Ubuntu 13.04, all mailto links in web pages (chromium) now open mutt in a terminal, instead of Thunderbird.

How do I fix this? 

I have changed ~/.local/share/applications/mimeapps.list to say x-scheme-handler/mailto=thunderbird.desktop as recommended by several sites (and restarted chromium), but that does not change anything.

---

### Post by matt_symes on 2014-03-13
Hi

Which desktop are you currently using ?

For Gnome, try editing the file

```
/etc/gnome/defaults.list
```

or use the program

```
xdg-mime
```

Check out the man page but an example would be along the lines of 

```
xdg-mime default thunderbird.desktop x-scheme-handler/mailto
```

You will have to check the above mime type though.

This may also work on the enlightenment desktop. It's been a while since i used it.

Post back on whether this fixes the issue.

Kind regards

---

### Post by batden on 2014-03-13
In Enlightenment:
Settings>Settings Panel>Apps>Default Applications>Core
and choose Thunderbird Mail for E-mail

Screenshot:
[http://www.enlightenment.org/ss/e-5321c8ac61e0f2.30509870.jpg](http://www.enlightenment.org/ss/e-5321c8ac61e0f2.30509870.jpg)

---

