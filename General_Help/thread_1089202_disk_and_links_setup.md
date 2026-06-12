---
title: "disk and links setup"
date: 2009-03-06
forum: General Help
---

### Post by jet.he.is on 2009-03-06
hi,

i'm pretty new to ubuntu and totally new to ubuntu forums, so forgive me and redirect me if this has already been asked.

i'm currently dual-booting with ubuntu 8.10 and have links to my windows my documents and desktop folders on my desktop for quick access. when i start my computer, though, these links are broken, because my hard drive isn't "mounted" i guess until i click on the link to it.

is there a way to put this mounting, or whatever the process is called, into a script that can run at startup?

thanks for helping out a newbie

---

### Post by taurus on 2009-03-06
Install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by jet.he.is on 2009-03-06
thanks a bunch. worked perfectly.

---

