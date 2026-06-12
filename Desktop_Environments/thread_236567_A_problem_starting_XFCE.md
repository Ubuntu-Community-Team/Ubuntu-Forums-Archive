---
title: "A problem starting XFCE"
date: 2006-08-14
forum: Desktop Environments
---

### Post by LadyDoor on 2006-08-14
I switched over to Xubuntu...my plan is still to primarily use Ratpoison as before, only now I would like to have XFCE as a backup instead of GNOME. However, I can't seem to start XFCE from either a CLI or from the GDM. From the CLI, I get the following error and then the XServer quits:

```
FreeFontPath: FPE "/usr/share/X11/fonts/misc/" refcount is 2, should be 1; fixing.
```

When trying to start from the GDM, I get the error that X is already running and so XFCE can't start. In both cases, the command issued was "startxfce4" (i.e., that's what I typed in the CLI, and that was the command given in the xfce4.desktop script in the /usr/share/Xsessions directory).

Any suggestions?
--Door

---

### Post by orb9220 on 2006-08-15
Do you mean you log out first then click on sessions and change it there from gnome to xfce then log in normally?

Because that is the way to change window mangers. It is not run from the term or as you call it the cli.

Did you install the xfce window manger? If you have done it correctlly then you should log out of gnome to the log on screen. You should see the word sessions click on that select xfce then logon with user name and password,

Hope this helped.

---

### Post by LadyDoor on 2006-08-15
Ok.

As I said, I don't use gnome--I use ratpoison. And I don't prefer to log in from GDM--I only even tried that as a fallback. My computer boots to a terminal and I type "startx" to start the X server to the window manager of my choice; from there I tried both putting "startxfce4" into my .xinitrc and just typing it instead of startx (which is also supposed to work for this particular windowmanager). That's what I was referring to as the CLI (command-line interface). And startxfce4 is the command that is supposed to start xfce. Finally, to install XFCE I installed the xubuntu-desktop metapackage and then went ahead and removed a lot of the heavy ubuntu-desktop packages that did not require removal of the xubuntu-desktop. I don't really plan to use XFCE a lot, but it would be nice to have it working as a backup.

So that's what's going on on this end. Thanks for your response!
--Door

---

### Post by LadyDoor on 2006-08-17
Sorry, but...*bump*

---

