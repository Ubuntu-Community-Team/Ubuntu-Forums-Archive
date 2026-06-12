---
title: "choosing desktop environment without desktop manager"
date: 2006-03-10
forum: Desktop Environments
---

### Post by stepore on 2006-03-10
hey group,

with gdm or kdm you can choose all the desktop environments you have installed. where are these settings stored? better yet, how does one control which desktop enviro to start when you do 'startx'. i'm playing with fluxbox, xfce (not xfce4) and i can't seem to find out how to start these without a k/g DM.

i've tried adding them to .xinitrc and .xsession (exec startfluxbox, exec startxfce) no go. fluxbox complains that X isn't running yet! so, how do you get X started with either of these or any other DE from command line.

cheers.

---

### Post by aysiu on 2006-03-10
My session lives in ~/.dmrc
Here it is right now: ```
[Desktop]
Session=gnome
```

Of course, I'm using KDM right now, so KDM is probably generating that .dmrc file.

If you have no DM, I don't know what you do.

Here's an excerpt from *startx*'s *man* page: >  To determine the client to run, startx first looks for  a  file  called
       .xinitrc  in  the user&#8217;s home directory.  If that is not found, it uses
       the file xinitrc in the  xinit  library  directory.   If  command  line
       client options are given, they override this behavior and revert to the
       xinit(1) behavior.  To determine the server to run, startx first  looks
       for  a file called .xserverrc in the user&#8217;s home directory.  If that is
       not found, it uses the file xserverrc in the xinit  library  directory.
       If  command  line server options are given, they override this behavior
       and revert to the xinit(1) behavior.  Users rarely need  to  provide  a
       .xserverrc  file.  See the xinit(1) manual page for more details on the
       arguments.

---

