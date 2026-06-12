---
title: "Where to put an *.key file?"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Heart on 2005-08-17
Hi,

I'm using kubuntu (hoary) and added this line in my sources.list to get always 
the newest tellico version:

```
deb http://www.periapsis.org/tellico/download/deb hoary main
```

But when I updated my sources list in aptitude I get an error like "..... key is not known. "

I wrote to the maintainer from this repository/package and he sent me a/his *.key file **but where I have to put this key or what do I have to do with it?**  :? 

Thanks

---

### Post by rmrf on 2005-08-17
sudo apt-key add <*.key file>

hope this helps :cool:

---

### Post by Heart on 2005-08-17
[QUOTE=rmrf]sudo apt-key add <*.key file>

hope this helps :cool:[/QUOTE]
 Yes, thanks ;)

---

### Post by ericvmazzone on 2005-09-26
[QUOTE=Heart]Hi,

I'm using kubuntu (hoary) and added this line in my sources.list to get always 
the newest tellico version:

```
deb http://www.periapsis.org/tellico/download/deb hoary main
```

But when I updated my sources list in aptitude I get an error like "..... key is not known. "

I wrote to the maintainer from this repository/package and he sent me a/his *.key file **but where I have to put this key or what do I have to do with it?**  :? 

Thanks[/QUOTE]


Who did you have to contact to get the key?
Thanks.

---

### Post by Heart on 2005-09-27
I wrote an email to the package maintainer and he has sent me the key....

---

