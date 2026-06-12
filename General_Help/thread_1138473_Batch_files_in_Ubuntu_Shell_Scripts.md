---
title: "Batch files in Ubuntu? Shell Scripts?"
date: 2009-04-26
forum: General Help
---

### Post by solidsnake204 on 2009-04-26
I need to run some commands in series when I logon for my internet to work.

On Windows I could do this with a batch file, but on Ubuntu I've heard about Shell Scripts, but I don't know where to start with them? Just put my commands in a text file?

What I need to do is run the *poff -a* command then *pon dsl-provider* command **twice** in this order.

I guess I use System > Preferences > Startup Applications to make the script run at logon.

Also, the poff and pon commands require admin privileges, would I use *sudo -S <mypassword>*?

---

### Post by bodhi.zazen on 2009-04-26
Easiest thing might be to put those commands into /etc/rc.local

```
gksu gedit /etc/rc.local
```

Add the commands , without sudo, above the exit 0 line,

rc.local is run during boot as root.

To answer the broader question, you use bash scripts in Linux :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

