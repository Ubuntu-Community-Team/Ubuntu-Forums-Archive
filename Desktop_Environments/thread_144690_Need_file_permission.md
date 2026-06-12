---
title: "Need file permission"
date: 2006-03-14
forum: Desktop Environments
---

### Post by rosingjh on 2006-03-14
Hello, recently switched to ubuntu and am having a problem installing gatos. I need to extract it into the /usr folder in my file system.  However, I do not have permission to do this.  It is odd because there is only one account on the computer and that is me.  Is there something I am missing, or is there a way to do this in the terminal that allows me to over ride the permissions?  Please  help me...

---

### Post by aysiu on 2006-03-14
This should help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

It may be easier, though, to just enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then install Gatos through apt-get ```
sudo apt-get update
sudo apt-get install gatos
```

For more on installing:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mavr on 2006-03-14
By default u are not root when using the gui. 
U can stil sudo su on the console and do it from there.
There are different ways to get root on gui as well, depending on what u have. Gnome or KDE?

---

### Post by jasay on 2006-03-14
Ubuntu does not activate the root account by default.  Instead just place "sudo" in front of any command you want run as root and enter your user password when it asks.  Here's more info. [https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

---

