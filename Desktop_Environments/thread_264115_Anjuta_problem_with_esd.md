---
title: "Anjuta problem with esd"
date: 2006-09-24
forum: Desktop Environments
---

### Post by horvatj on 2006-09-24
Hello!

After reinstalling anjuta (it worked fine since last year) I have this problem:

> johann@indiecam2:~$ anjuta 
/bin/sh: /usr/bin/esd: No such file or directory 
** Message: Initializing AP class 
** Message: Initializing AP Instance 
** Message: Initializing launcher class 

(anjuta:2922): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed 

(anjuta:2922): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed 
/bin/sh: /usr/bin/esd: No such file or directory 


My developing system does not have a soundcard. But this wasn't any problem befor reinstalling it.

I tried to install the esound package. This doesn't work as well.

What's wrong?

Thanks Johann

---

