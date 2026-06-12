---
title: "Thumb Drive can't mount anymore in Hardy"
date: 2008-05-20
forum: Florida Team - US
---

### Post by chriscri on 2008-05-20
Well if this is you like me... don't despair. There is a bug on launchpad about this very issue. [Bug #211760 in Ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/211760").

My symptoms were exactly the same. So I chose to use the following workaround 
```
sudo modprobe -r ehci_hcd
```

Someone Else mentioned Modifying the gconf-editor setting for /system/storage/default_options/vfat say that there's looked like:
[shortname=mixed,uid=,utf8,umask=007,exec,usefree]

Mine didn't match exactly so I decided not to play with it. 
[shortname=mixed,uid=,utf8,umask=077,exec,flush]

Hope this helps. I remember seeing Falling Inferno today in IRC slightly frustrated hopefully she/he will see this post.

Chriscri

---

### Post by chriscri on 2008-05-20
OMG... I just noticed something. When I re-add that ehci_hcd, by Nostromo N-52 re-enables. So that may be why this might not affect everyone. 

I added it back by performing:

```
sudo modprobe ehci_hcd
```

> **chriscri said:**
> Well if this is you like me... don't despair. There is a bug on launchpad about this very issue. [Bug #211760 in Ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/211760").

My symptoms were exactly the same. So I chose to use the following workaround 
```
sudo modprobe -r ehci_hcd
```

Someone Else mentioned Modifying the gconf-editor setting for /system/storage/default_options/vfat say that there's looked like:
[shortname=mixed,uid=,utf8,umask=007,exec,usefree]

Mine didn't match exactly so I decided not to play with it. 
[shortname=mixed,uid=,utf8,umask=077,exec,flush]

Hope this helps. I remember seeing Falling Inferno today in IRC slightly frustrated hopefully she/he will see this post.

Chriscri

---

### Post by Nausser on 2008-09-09
The first command by itself worked like a charm!!  Thanks!!

---

