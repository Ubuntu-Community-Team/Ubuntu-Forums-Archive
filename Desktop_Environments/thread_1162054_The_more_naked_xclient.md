---
title: "The more naked xclient"
date: 2009-05-17
forum: Desktop Environments
---

### Post by RogergR on 2009-05-17
Hello everybody, it`s my first thread on this forum. I`m trying to "create" **the more naked xclient** session for ubuntu, but not very successfully. I wont a session, that  runs only** VLC** and an option to log out. May be it is a simple task for someone, but not for me. A few days ago I noticed that watchig movie files with VLC in the **fluxbox** is more fluent, than watching movies in **gnome**. The lost frame rate is lower. For this, I want a VLC session. Does anybody already done something similar? Thank you for sharing your knowledge.

):P

---

### Post by Brandon Williams on 2009-05-17
If the only thing you want to run is VLC ... no window manager, no panel, etc. ... then create a file call $HOME/.xsession with this content:
```
#!/bin/sh
exec vlc
```
I don't have VNC installed, so I don't know if that's actually the name of the command, but I assume you will know what it should be.

After then script has been created, 'chmod u+x $HOME/.xsession'.

Now, log out, select the 'Run Xclient script' session type in GDM, and log back in. You should now have VLC running with none of the extra stuff that would be part of a fully functional desktop environment.

With this setup, you won't have volume control, access to a terminal, or anything else, so you may want to add some other initialization tasks to the above script. Ask more questions if you don't know how to do any of the specific setup tasks from the command line.

---

### Post by RogergR on 2009-05-18
Thank you,it works, but not exactly your way.

ln -s .xsession .xinitrc
gedit .xsession

#!/bin/sh
exec vlc

chmod 700 .xsession

I`ve found this site[ http://www.acm.uiuc.edu/workshops/cool_unix/xinitrc.html  ]("http://www.acm.uiuc.edu/workshops/cool_unix/xinitrc.html")
when googleing.                                                                                                                    :popcorn:

---

### Post by Brandon Williams on 2009-05-18
I'm looking for the "not exactly your way" part. Your post indicates that you did exactly what I suggested for the setup, with the one additional step of creating a symlink that will make it work if you run startx from a console (which you probably won't do, or at least not very often).

If there _is_ something you did that's different from what I suggested, I'd be interested to see what it is.

---

### Post by RogergR on 2009-05-18
Thank you again, but exactly is exactly and $HOME/.xsession for me is not .xinitrc .xsession. Look, I`m the fresh one with "programming", I`m also bad in english, so don`worry be happy:o

How can I change master volume in this new script?

---

