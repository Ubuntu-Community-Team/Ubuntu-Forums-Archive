---
title: "XMMS locks up when trying to play mp3"
date: 2005-08-18
forum: Desktop Environments
---

### Post by tkeisling on 2005-08-18
I just followed the starter guide on how to install xmms, after I got done everytime I try to play a file it just freezes and doesnt do anything sits at 0:00:00

I checked my .xsession file and found this:

** (gnome-cups-icon:9698): WARNING **: failed request with status 1030


Anyone know how to fix this?

Thanks.

---

### Post by Solomon on 2005-08-18
I just encountered this problem and fixed it. Go to your preferences inside of XMMS and check to verify your output is set correctly. There should be three I think. Least there are for me. Try each one.

---

### Post by izmaelis on 2005-08-18
The error (this time warning) message has nothing to do with XMMS crashing while starting to play audio file. This is output plugin misconfiguration for sure.
How to setup your sound system look [here](http://ubuntuguide.org/#configuresoundproperly).

---

### Post by tkeisling on 2005-08-20
Woot it worked thanks a lot guys :)

---

