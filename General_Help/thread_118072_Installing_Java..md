---
title: "Installing Java."
date: 2006-01-16
forum: General Help
---

### Post by MJSOnline on 2006-01-16
Hi all. 
How do I install Java using the "Manual Download" [http://java.com/en/download/manual.jsp]("http://java.com/en/download/manual.jsp") on the [www.java.com](www.java.com) site?

Which one do I download and install?

Thanks.
Matthew

---

### Post by kaamos on 2006-01-16
Hello!

You can follow this guide [http://ubuntuforums.org/showthread.php?t=79449&highlight=plf](http://ubuntuforums.org/showthread.php?t=79449&highlight=plf)
and then use synaptic to install sun-j2re1.5.

Hope this helps!

---

### Post by Perfect Storm on 2006-01-16
Easist way:

```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

then:

```

sudo apt-get update
sudo apt-get install sun-j2re1.5

```

---

### Post by MJSOnline on 2006-01-16
Cheers people!!.

Many thanks.
Matthew

---

