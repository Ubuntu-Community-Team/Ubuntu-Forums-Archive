---
title: "Access Root Files"
date: 2007-03-17
forum: Desktop Environments
---

### Post by dontgetshocked on 2007-03-17
How can I access my root files, i.e. the files below the root folder such as etc/  and so on?

---

### Post by dbbolton on 2007-03-17
run Nautilus as root. i.e.:
```
$ sudo nautilus /etc 
```

if you need to see the *hidden *files in a folder, type Ctrl + H

---

### Post by ardchoille42 on 2007-03-17
You should use

```

gksudo nautilus

```

Always use gksudo with gui apps because it sets up the environment more appropriately. sudo is for cli apps. For an explanation of this, see [this page]("http://www.psychocats.net/ubuntu/graphicalsudo").

Avoid ever using

```

sudo <gui app>

```

---

### Post by dbbolton on 2007-03-18
i've never noticed a difference.

---

### Post by taurus on 2007-03-18
> **dbbolton said:**
> i've never noticed a difference.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dontgetshocked on 2007-03-18
So how would I access ALL the files using this method? That is ALL the files starting with root!

---

### Post by taurus on 2007-03-18
What files do you want to access?  If you can be a little more specific, perhaps somebody here would tell you exactly how to do it.

---

### Post by dontgetshocked on 2007-03-18
I would like to be able to view ALL of the folders inclusing the root folder

---

### Post by dontgetshocked on 2007-03-18
So if I use gksudo nautilus /etc  I then see a lot of folders and I wanted to see ALL of the folders below and including the root folder, so what command do I sue to do this? Hope this clear enough. I believe  there are folders above the /etc folder

---

### Post by christhemonkey on 2007-03-18
```
gksudo nautilus / 
```
That lets you browse the root of the hard drive.

---

