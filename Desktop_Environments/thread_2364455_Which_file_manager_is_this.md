---
title: "Which file manager is this?"
date: 2017-06-23
forum: Desktop Environments
---

### Post by Daniel_Rosehill on 2017-06-23
Hi,

What is the name of the file manager that is called from other applications (say, Google Chrome)?

I installed Ubuntu 16.04 then removed Nautilus and set have set PcMan File Manager as the default file manager using exo-preferred-applications. (Long story short, Lubuntu wouldn't install on my machine, so I'm trying to adapt Ubuntu to incorporate its programs).

What I'm seeing when I select open from within Chrome appears to be neither Nauiltus (which has been removed) nor PcManFM. It is something else - but I don't know what!

Any ideas what this is, or how to get it to call the default FM,  please let me know.


 [IMG]http://i.imgur.com/ssQPYVb.png[/IMG]

---

### Post by Dennis N on 2017-06-23
The Open and Save file dialogs appearance are determined by the toolkit the application uses (gtk2, gtk3, qt, etc). The dialogs aren't provided by the file manager.

---

