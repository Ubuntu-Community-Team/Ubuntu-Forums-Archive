---
title: "RealPlayer not working with Firefox"
date: 2005-10-16
forum: Desktop Environments
---

### Post by bored2k on 2005-10-16
I downloaded and installed RealPlayer using the .bin on real.com and placed it on /opt/RealPlayer (as the regular user). As a stand alone application it loads perfectly, but when I try an RM stream on Firefox I get this (even with mozilla helpers installed):

[CENTER][img]http://img106.imageshack.us/img106/8438/screenshothttpwwwtvradiocom7ng.png[/img]

[[IMG]http://img106.imageshack.us/img106/4136/screenshot8tt.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshot8tt.png)[/CENTER]

Anyone knows how to fix this :confused: ? I need my dose of RFI every once in a while .

---

### Post by hajk on 2005-10-17
Firefox should ask about application with which to open multimedia content, probably suggesting something like Totem or Rhythmbox. At that stage you can hit "Other" and browse to /usr/bin/realplay (or enter it manually), and you should be all set. Mind you, I installed realplayer from Marillat's repository -- in your case the location of realplay might be different, perhaps /usr/local/bin/realplay.

If all fails, I would say remove the RealPlayer that you have already installed, and go the Marillat route. It worked for me.

---

