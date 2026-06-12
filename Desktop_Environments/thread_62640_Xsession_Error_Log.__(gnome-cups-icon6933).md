---
title: "Xsession Error Log.  (gnome-cups-icon:6933)"
date: 2005-09-05
forum: Desktop Environments
---

### Post by dysprosium on 2005-09-05
** (gnome-cups-icon:6933): WARNING **: failed request with status 1030

Is this a serious problem?  What can I do to remedy this?

---

### Post by strawberry on 2005-09-05
[QUOTE=dysprosium]** (gnome-cups-icon:6933): WARNING **: failed request with status 1030

Is this a serious problem?  What can I do to remedy this?[/QUOTE]
I think it is not. I found this somewhere in the forum and helped:
>      gnome-cups-icon is quering every 5 seconds the cups daemon.            

     gnome-cups-icon is started by default by gnome-session. To disable     

     it delete the lines regarding gnome-cups-icon from                     

     /usr/share/gnome/default.session.
I hope it works for you too...

---

