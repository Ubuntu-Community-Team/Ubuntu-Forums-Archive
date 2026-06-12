---
title: "simple question dial up"
date: 2005-11-20
forum: Desktop Environments
---

### Post by trisscross on 2005-11-20
Hi, I am new to Linux. I installed Ubuntu 5.10 earlier today and have swapped over to an external modem when the internal WinModem failed to work. Everything works fine, but is there facility, preferably without complicated fiddling, to get the modem to automatically dial and disconnect when applications require a network connection and when that application is closed?

~ Tristram

---

### Post by autocrosser on 2005-11-20
Synaptic>GnomePPP  Not automatic, but it is very easy to use--I put it on one of my panels & have it show as a notification icon--

---

### Post by trisscross on 2005-11-21
now my next problem it only connect's 4 minutes and then disconnect's please help:confused: 

~tris

---

### Post by autocrosser on 2005-11-22
Well--I'd try changing some of the settings--speed being the first on the list, also--recheck your .wvdial.conf file for correctness (make sure you enable hidden files in your nautilus preferences)--You can also right-click on the PPP icon & look at the log--will give you insight about why the cut-off----

---

### Post by michael_salcher on 2005-11-22
when using gnome-ppp check the log when dialing up. does it actually ever log on properly? if not, try using "stupid mode" option in the gnome-ppp preferences

---

### Post by trisscross on 2005-11-23
i have just installed gnome ppp i will post how i get on tomorrow thanks

---

### Post by trisscross on 2005-11-24
hi there i think i know what the problem is i just don't know how to fix it 
if i connect on my laptop win xp if i type in my isp password  it gets updated by my isp??
this is a list of errors from the log
warning could not modify /ect/ppp/pap-secrets: permission denide
chap maybe flaky
warning could not modify /ect/ppp/chap-secrets: permission denide
chap maybe flaky
ppp daemon has died lack of lcp echo (code 15)
please help
thanks tris

---

### Post by michael_salcher on 2005-12-18
I'm sure that's totally unsafe (but it would work), give all files which don't have read-write permissions, read-write permissions:

```
sudo chmod a+rw filename
```

---

