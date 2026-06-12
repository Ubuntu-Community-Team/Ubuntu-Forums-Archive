---
title: "deluge executable directory"
date: 2008-12-17
forum: General Help
---

### Post by Balinsky on 2008-12-17
ok so im trying to point firefox to the deluge bittorrent client and after 20+ minutes of searching both my filesystem and the internets i cannot find it

---

### Post by Elv13 on 2008-12-17
Probably /usr/bin

but if it is not there, a find /* | grep deluge will find it

---

### Post by jimmy the saint on 2008-12-17
you need to activate the deluged daemon with the appropriate option for the web gui in order to connect to it.  there is a faq entry at their site with more details.

---

### Post by teddks on 2008-12-17
If you're using the Ubuntu deluge, it won't have any deluged (I'm fairly sure).

To locate any program, just use whereis or which.

```
ted@Stormbringer:~$ whereis deluge
deluge: /usr/bin/deluge /usr/share/deluge /usr/share/man/man1/deluge.1.gz
ted@Stormbringer:~$ which deluge
/usr/bin/deluge

```

whereis also shows where the documentation is, as you see.

---

### Post by jimmy the saint on 2008-12-17
Ooops.  teddks is right!!  ignore what I said!  I am thinking v1+

---

### Post by Balinsky on 2008-12-18
thanks for all the help what i need was in /usr/bin

---

