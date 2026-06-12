---
title: "How to add IP local address on the top panel of Ubuntu 12.04 Unity"
date: 2014-02-14
forum: Desktop Environments
---

### Post by bibbothegreat on 2014-02-14
Hello :)
I work as IT assistant for libraries network. I need to add the local IP address on the top bar or panel of Ubuntu Unity 12.04 (the one displays on the right date, account username and settings). It's important that appears easily there because the librarians without IT practice gonna call me for help they can easily read me the IP local to connect via SSH etc.
I tried with Conky but it has a bug, it seems. If I click on show desktop and after I click on the desktop the Conky network message disappears. Giplet doesn't work in Unity. 
Would you help us please?
Thank you :)

---

### Post by deadflowr on 2014-02-14
There are more than one setting to run conky with.
look for the line that says
own_window_type
and try out different options.(several are desktop, normal, override, panel)
You might even see about selecting more or less hints
something like
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
More [here]("http://conky.sourceforge.net/documentation.html")
See if adjusting these settings help.

As far adding the local ip to the panel, unless there is an app indicator for it already, you would have to write it yourself.

---

### Post by buzzingrobot on 2014-02-14
Why not write a simple script that generates all the info you might need, create .desktop file for it, and add an icon to launch it to the Launcher?

---

