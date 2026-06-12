---
title: "Sun Wireless Toolkit 2.2"
date: 2006-09-10
forum: Desktop Environments
---

### Post by bardu on 2006-09-10
Hi all,

I tried to run ktoolbar on Ubuntu 6.06 but it hangs on startup. Here is the output from the command line:
> 
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
WTK OTA server started ...
I guess it is more a problem of the implementation of the toolkit rather an Ubuntu problem, but maybe someone had the same issue and could fix it.
Any usefull information are highly appreaciated.

Thanks in advance.
Stephan

---

### Post by nikosft on 2006-09-11
For a strange reason if you run the following it will work.
>LANG2=$LANG
>LANG=sv_SE.ISO8859-1
>path_to_wireless_toolkit/bin/ktoolbar
>LANG=$LANG2

If somebody knows the reasin for that I'll be more than happy to learn

---

### Post by nikosft on 2006-09-11
It seems that there is a problem if the $LANG variable is in UTF8. if we set it to a ISO whatever there is no problem running WTK nor installing it

---

### Post by bardu on 2006-09-12
nikosft, you saved the day. Thanks a lot.
Just for correctness: line 4 comes before line 3 and then is works.

Again, thank you very much.

Stephan

---

