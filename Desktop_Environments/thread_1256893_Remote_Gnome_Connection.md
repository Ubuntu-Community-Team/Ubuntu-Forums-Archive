---
title: "Remote Gnome Connection?"
date: 2009-09-03
forum: Desktop Environments
---

### Post by RandyRitter on 2009-09-03
I'm new to Ubuntu, but I have experience working with Windows servers.  I've recently installed Ubuntu server on one of the machines.  I can logon from the console and I have loaded gnome and it is running fine.

What I would like to do is establish a connection from another computer, either ubuntu or windows, and be presented with the same kind of environment as if I were logged on to the consol.  Same kind of idea as a windows remote desktop.  Just like being there.

I can telmet to the machine and log in however I do not know how to set up gnome to work remotely.  Are there instructions showing me how to do this?

I searched and found references to remote desktop but they appear to be sharing a descktop between to logged in users.  That's not really what I want.

Thanks very much!

---

### Post by i.r.id10t on 2009-09-03
You'll need a X server on your local machine - either a second Linux box or a win32 one like cygwin-x or similar.  Then ssh in and allow exporting your display (Putty can do this in Windows).  Then launch whatever app you want.

Unfortunately GDM is broken in 9.04 and does not allow network connections...

---

