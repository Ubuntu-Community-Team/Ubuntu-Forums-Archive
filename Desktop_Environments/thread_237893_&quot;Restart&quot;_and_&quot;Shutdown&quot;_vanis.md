---
title: "&quot;Restart&quot; and &quot;Shutdown&quot; vanished!"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Orta on 2006-08-16
Hello all! I installed XGL/Compiz on my Ubuntu 606 laptop using the second method [described here](http://www.compiz.net/topic-389-1.html). Basically, this method explains how to install XGL/Compiz on a separate session, just in case of crashes, etc. but to me is more important because of battery savings. XGL works like a charm but, when I click the "quit icon" on the top right edge of the screen, I the buttons for "restart" and "shutdown" are missing! However, the buttons are there when I start a regular non-XGL/Compiz GNOME session. I guess this is because the xgl.desktop created during the process is missing something? Can you help me? Not having the buttons there is rather annoying... Many many thanks in advance!

PS: on that xgl.desktop, I removed the UTF-8 reference to avoid collisions with GNOME's keyboard settings. Probably it's not that causing my issue but I thought it'd be of interest to know.

---

### Post by Fass on 2006-08-16
This is a known issue with running XGL as a separate session, and there doesn't seem to be a solution, unfortunately, at the moment, other than either logging out and then shutting down in GDM or doing it manually with "sudo halt/reboot."

---

### Post by Orta on 2006-08-17
I understand... This issue will probably be fixed in time, no? Thanks for your patience.

---

### Post by Fass on 2006-08-17
> **Orta said:**
> I understand... This issue will probably be fixed in time, no?

We can hope. :)

---

