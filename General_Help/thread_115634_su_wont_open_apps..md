---
title: "su wont open apps."
date: 2006-01-10
forum: General Help
---

### Post by corstar on 2006-01-10
I have a strange problem regarding superuser. 
With every su command regarding kate or kwrite and even synaptic, I get the following error.
corstar@blackbox:~$ su
Password:
root@blackbox:/home/corstar# synaptic
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

(synaptic:9145): Gtk-WARNING **: cannot open display:

I'm not sure what the ":0.0" is. It looks like a display issue, but everything is cool with that. 
I do have a work around though, I have to sudo a lot of commands, actualy, could it possibly be a permisions issue??

---

### Post by corstar on 2006-01-10
this is the output when I tried to open kate.

root@blackbox:/home/corstar# kate
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9182' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9172' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.

---

### Post by aysiu on 2006-01-10
Maybe [this](http://www.experts-exchange.com/Operating_Systems/Linux/Q_20762091.html) might help?

---

### Post by corstar on 2006-01-11
thanks, it gives an idea of the problem.

I didn't know the x server stopped those kind of simple opperations

---

