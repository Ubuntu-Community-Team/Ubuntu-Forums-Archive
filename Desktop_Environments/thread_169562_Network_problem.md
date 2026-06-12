---
title: "Network problem"
date: 2006-05-02
forum: Desktop Environments
---

### Post by rab on 2006-05-02
THe network settings configurator wont let me get in as root anymore. I went in to set a static IP and i logged out, forggetin to set te default gateway. Now it ownt let me back in, it keeps on saying to click the button. I do and enter in my password and it wont let me change anything.

---

### Post by dschulz on 2006-05-04
try to do it by editing by hand the file /etc/network/interfaces.

first, stop the interfaces by running 

sudo /etc/init.d/network stop

then edit the above mentioned file,

in the interface definition add a line like this

  gateway 192.222.222.222

and restart again

sudo /etc/init.d/network start

---

