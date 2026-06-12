---
title: "Orage clock options?"
date: 2010-12-26
forum: Desktop Environments
---

### Post by tpprynn on 2010-12-26
Is it possible to remove the seconds from the Orage clock?

I'm using Xubuntu 10.10, Xfce 4.6 if you need to know.

Thanks.

---

### Post by hhh on 2010-12-26
I don't use the Orage clock, but looking at this page...
[http://www.kolumbus.fi/~w408237/orage/screenshots.html](http://www.kolumbus.fi/~w408237/orage/screenshots.html)
it says that it uses strftime formatting (which is what the Gnome panel and Xfce panel clock applets use). I use %l:%M %p which gives me a readout like 6:19 PM . Replace %X with that, or another custom format...
[http://www.cplusplus.com/reference/clibrary/ctime/strftime/](http://www.cplusplus.com/reference/clibrary/ctime/strftime/)

---

### Post by tpprynn on 2010-12-26
Good work Batman. I've put 


%I:%M


and that does the job. Thanks!

---

### Post by hhh on 2010-12-26
No problem. Even more parameters...
[http://www.mkssoftware.com/docs/man3/strftime.3.asp](http://www.mkssoftware.com/docs/man3/strftime.3.asp)

---

