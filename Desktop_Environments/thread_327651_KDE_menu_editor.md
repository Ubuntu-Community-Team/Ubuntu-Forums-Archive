---
title: "KDE menu editor"
date: 2006-12-29
forum: Desktop Environments
---

### Post by ingo on 2006-12-29
Hi,

I'm having problems adding apps to my kde menu. Whenever I edit it and save my changes are simply not accepted. Could be some rights issue? Anybody know where the config files for the editor are?

Cheers!

---

### Post by ingo on 2007-03-12
OK, the lads over at kde did wonders and finally helped me fix this problem. Here is how for all those fellow sufferers:

rename ~/.local/share/applications to ~/.../applications.bak

and 

~/.kde/share/config/kmenueditrc to ~/.../kmenueditrc.bak

then 

kbuildsycoca


and restart the X-server. Hey presto, everything works again :)

And in case you can't be arsed to add all the programmes manually, run kappfinder  :cool:

---

### Post by hikaricore on 2007-03-25
Thanks, you just saved my sanity.  :)

---

