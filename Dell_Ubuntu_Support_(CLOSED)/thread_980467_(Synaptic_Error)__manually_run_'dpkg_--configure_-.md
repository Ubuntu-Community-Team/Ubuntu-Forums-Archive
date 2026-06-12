---
title: "(Synaptic Error)  manually run 'dpkg --configure -a'"
date: 2008-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teledocument on 2008-11-12
Ubuntu 8.10:confused:

Everytime I try the Synaptic I get the following error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. Terminal states I must have super user privliges??

---

### Post by Shwefty on 2008-11-12
Then, run sudo first:

```
sudo dpkg --configure -a
```

It'll prompt you for your password.

---

### Post by teledocument on 2008-11-12
I have a Dell, XPS M1330, The CD,DVD player is not registering. It worked with Ubuntu 8.4 and now with the 8.10 it doesnt. I can not play or record CD/DVDs

---

### Post by ciscosurfer on 2008-11-12
Did you follow Shwefty's advice?

---

### Post by Thaismai on 2008-11-13
I'm having the same problem, see here:

[http://ubuntuforums.org/showthread.php?p=6167187#post6167187](http://ubuntuforums.org/showthread.php?p=6167187#post6167187) 

let me know how you go resolving it!

James.

---

### Post by Shwefty on 2008-11-13
The dpkg --configure -a is a broad command which the [New to Ubuntu? Start here -]("http://ubuntuforums.org/showthread.php?t=801404") forum discussion (stickied), says is for fixing broken packages.  It is very likely that these to problems are unrelated.

Still, I think teledocument might should still run 
```
sudo dpkg --configure -a
``` where as it might not work for you.

---

### Post by Josh512 on 2009-01-12
when i go to sudo and type in the "dpkg configure a" thing, it says "package is in a very bad, inconsistent state, you should reinstall it before attempting configuration". how do i go about reinstalling it and what package do i have to reinstall?

---

### Post by ugm6hr on 2009-01-12
Post the exact output from:
```
sudo dpkg --configure -a
```

It should tell you what package it is trying to configure.

If it doesn't, can you remember the last update / install you did?

To reinstall:
```
sudo apt-get install --reinstall package_name
```

---

