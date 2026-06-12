---
title: "Pidgin: ICQ not working"
date: 2010-12-02
forum: Desktop Environments
---

### Post by accodata on 2010-12-02
Hi ALl

I had ICQ running through pidgin, then 2 days ago it stopped working, the error message is:
"Received unexpected response from [https://api.oscar.aol.com/aim/startOSCARSession:](https://api.oscar.aol.com/aim/startOSCARSession:) Invalid requested host"

Any ideas with thanks

Accodata.
I run Ubuntu 10.4 LTS

---

### Post by PaterSVK on 2010-12-02
Hello, i have the same problem. I tried all possible configurations and nothing helped. This problem persists.

---

### Post by vivedekananda on 2010-12-02
I managed to get it work. Go to modify accoount->advanced;
change server to login.icq.com port 5190;
uncheck all three checkboxes (ssl, cleint login,use proxy server).
Enconding is ISO-8859-1.

Hope this will work for you as well.

---

### Post by jwp1223 on 2010-12-03
> **vivedekananda said:**
> I managed to get it work. Go to modify accoount->advanced;
change server to login.icq.com port 5190;
uncheck all three checkboxes (ssl, cleint login,use proxy server).
Enconding is ISO-8859-1.

Hope this will work for you as well.


Thanks man you rule!

---

### Post by honeybear on 2011-01-18
nothing works... any ideas if piding willl be fixed by pidgin team. Man, taht bug is really annoying again ...:( are developments of pidgin dead btw?

---

### Post by antekone on 2011-06-21
> **vivedekananda said:**
> I managed to get it work. Go to modify accoount->advanced;
change server to login.icq.com port 5190;
uncheck all three checkboxes (ssl, cleint login,use proxy server).
Enconding is ISO-8859-1.

Hope this will work for you as well.

Thanks for this info, it worked. I hope the connection with "slogin" will be fixed though, because proper transmission is encrypted transmission :P

---

### Post by honeybear on 2011-06-21
> **antekone said:**
> Thanks for this info, it worked. I hope the connection with "slogin" will be fixed though, because proper transmission is encrypted transmission :P

With so much famous is ICQ, I cannot believe yet that still even the most famous : pidgin cannot handle SSL connections..

that's sad actually, and it is over 1 year it is like that

---

