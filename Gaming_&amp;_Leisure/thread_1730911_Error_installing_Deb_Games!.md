---
title: "Error installing Deb Games!"
date: 2011-04-16
forum: Gaming &amp; Leisure
---

### Post by Advice Pro on 2011-04-16
I went to *System > Admininistration > Software Sources > Options tab > Add*, APT line: ```
deb http://archive.getdeb.net/ubuntu lucid-getdeb games
```

and got the follwing error message when closing and reloading:

```
W: GPG error: http://archive.getdeb.net lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
```

---

### Post by Perfect Storm on 2011-04-16
You forgot to the second line.

Terminal:

```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

 [http://www.getdeb.net/updates/ubuntu/9.10/](http://www.getdeb.net/updates/ubuntu/9.10/)

---

### Post by Advice Pro on 2011-04-16
What I want to do is get QJoypad pre-compiled for Ubuntu from the [GetDeb Games PPA](http://www.ubuntuupdates.org/packages/show/198210).  This is an alternative to [the requirements & install for QJoyPad 4.1.0!](http://ubuntuforums.org/showthread.php?t=1724435).

---

