---
title: "How do I fix Ctl-Alt-Backspace?"
date: 2009-04-23
forum: General Help
---

### Post by danbuter on 2009-04-23
Since lazy linux programmers have disabled CAB because it interferes with their eMacs, how do I reenable it?

---

### Post by m_2009 on 2009-04-23
You need to install the &#8220;dontzap&#8221; package
 
```
sudo apt-get install dontzap
```
 
Open Terminal or Konsole depending on if you use Ubuntu or Kubuntu and type:
 
```
sudo dontzap --enable
```
or
 
```
sudo dontzap --disable
```
 
Where &#8220;disable&#8221; means that Ctrl+Alt+Backspace will restart the xserver while &#8220;enable&#8221; won't.
 
You will need to restart before the setting takes effect too.

---

### Post by paradigm2 on 2009-04-23
> **danbuter said:**
> Since lazy linux programmers have disabled CAB because it interferes with their eMacs, how do I reenable it?

I forget the the way to enable it (check search), but if you do:

ALT Gr (a.k.a RT ALT) + SYSREQ + K

It pretty much does the same thing.

---

### Post by ftmichael on 2010-01-20
See also [http://sathyasays.com/2009/11/08/enable-xserver-shortcut-ctrlaltbackspace-in-ubuntu-9-10-karmic-koala/](http://sathyasays.com/2009/11/08/enable-xserver-shortcut-ctrlaltbackspace-in-ubuntu-9-10-karmic-koala/) for Karmic.

---

### Post by Potters Son on 2010-01-28
@ftmichael: +1

---

