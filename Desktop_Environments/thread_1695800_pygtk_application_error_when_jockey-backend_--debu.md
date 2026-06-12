---
title: "pygtk application error when jockey-backend --debug starts"
date: 2011-02-26
forum: Desktop Environments
---

### Post by Jonnox on 2011-02-26
I am using Ubuntu 10.04 and I have a script:
```
/etc/X11/Xsession.d/92my-guiapp
```

Which runs a python (pygtk) script. It loads fine and I exit it using the following function:
```
def delete_event(self, widget, event, data=None):
    gtk.main_quit()
    return True

```

When GDM finishes loading the user into the environment, there is no error. I run
```
ps -ef | grep python
```
and only the grep command show up. Then, after about a minute or so, 
```
/usr/bin/python /usr/share/jockey/jockey-backend --debug -l /var/log/jockey.log
```
shows up as a process and the application error console in gnome show up saying that my python application has unexpectedly quit (I thought I had gracefully quit it in the application).

Is this a python problem, or an X11 issue?

Any ideas are welcomed!

---

### Post by Jonnox on 2011-02-26
FYI: I added quit() after the gtk quit function and it seemed to accept that so I guess I can assume it was a python error.
:o

---

