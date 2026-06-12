---
title: "Programs reopen when I restart ubuntu"
date: 2007-02-05
forum: Desktop Environments
---

### Post by mod187 on 2007-02-05
Every time I turn on my computer, certain windows will open automatically. The windows include:

Terminal
System Monitor
Sessions
Nautilus

I can only close them by pressing alt-F4. Is there a way to correct this so these do not re-open when I restart?

I am running Edgy-gnome

Thanks,
Matt

---

### Post by bapoumba on 2007-02-05
Hi,
close all unwanted applications on startup, then enter **gnome-session-save **in a terminal.

---

### Post by dannyboy79 on 2007-02-05
> **mod187 said:**
> Every time I turn on my computer, certain windows will open automatically. The windows include:

Terminal
System Monitor
Sessions
Nautilus

I can only close them by pressing alt-F4. Is there a way to correct this so these do not re-open when I restart?

I am running Edgy-gnome

Thanks,
Matt

this is because if you have ever tried to change the "session" pull down prior to actually loggin in it's because the default selection is always your last session I believe. so either change that to be default session or do what the previous person stated so that your session is saved with nothig opened prior to loggin out.

---

### Post by mod187 on 2007-02-05
Problem solved! Thanks for the rapid reply

Matt

---

### Post by dannyboy79 on 2007-02-06
> **mod187 said:**
> Problem solved! Thanks for the rapid reply

Matt

mod187, can you please get in the habit of posting the solution so that others can benefit as well. this way people don't have to read back thru tons of threads and do trial and error until they get it fixed. I know this time there is only 3 posts in this thread but it's just a good habit to get into. thank you.

---

### Post by mod187 on 2007-02-06
> Hi,
close all unwanted applications on startup, then enter gnome-session-save in a terminal.


This worked, didn't try the second solution since the first solved the problem.

Thanks again anyway

Matt

---

