---
title: "Doom 3 modding/map making"
date: 2010-09-07
forum: Gaming &amp; Leisure
---

### Post by feardotcom on 2010-09-07
I'm confused. I went to the gtk radient site and it said files are int he trunk folder, so i went there and it looks like i have to download every single file seperatly, isn't there a tar file or zip file or something to download the source to compile?

Anyone know of any other d3 or q4 map making tool for linux? 

What is the idtech4 sdk exactly? Im looking to start modding for d3/q4, and im not making the switch to windows again. Does it not include a map making utility?

---

### Post by glaze on 2010-09-07
I haven't tried GTK Radiant, but you don't have to download the files separately. You can get them all using this command:
```
svn checkout [https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5/](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5/) ./GtkRadiant
```

Here's compile instructions:
[https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5/COMPILING]("https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5/COMPILING")

I don't know how well it compiles/runs on modern systems, it's quite old.

---

### Post by J.K.Makowka on 2010-09-07
Try Darkradiant:
[http://darkradiant.sourceforge.net/](http://darkradiant.sourceforge.net/)

Otherwise there is also Netradiant, but I don't think it supports Doom3.

---

