---
title: "GTK make problem"
date: 2008-12-11
forum: General Help
---

### Post by vindzhov on 2008-12-11
Hi! I wanted to install murrine theme engine, but I did not know, that GTK is requiered for that. So I tryed to install GTK+- 2.14.5. I first installed all the requiered packages (or at least I think so). After that I try ```
to vasil@vasil-laptop:~/Desktop/gtk+-2.14.5$ make
``` , But I get this error message: ```
/usr/bin/ld:.libs/libgdk_pixbuf-2.0.ver:2: ignoring invalid character `\001' in script
/usr/bin/ld:.libs/libgdk_pixbuf-2.0.ver:2: syntax error in VERSION script


```

I am newbie and please don't get angry if this is not the right forum part for posting this thread. And excuse me if I have made some mistakes in these linux terms. Thanks in advance

---

### Post by binbash on 2008-12-11
install murrine svn deb from here : 

[https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)

AND it is not gtk error you are missing a lib at murrine configure,it is libgtk2.0-dev
sudo apt-get install libgtk2.0-dev

---

### Post by snova on 2008-12-11
Murrine is in the repositories. Just install 'murrine-themes' from the package manager.

The way you're going is the way of extreme frustration...

---

