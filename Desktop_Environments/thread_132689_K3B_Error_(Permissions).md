---
title: "K3B Error (Permissions)"
date: 2006-02-18
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-02-18
I just installed k3b using "APT" and then I went to create a Debian "Etch" ISO and get the following error and am not sure how to resolve it.

[IMG]http://img85.imageshack.us/img85/5161/k3berror7qa.png[/IMG]

---

### Post by knalle on 2006-02-18
try to run it as root

---

### Post by nalmeth on 2006-02-18
k3b keeps telling me that I don't have root permission for cdrao, when in fact I do. Go into settings, and look for permissions for a better idea of what might be going on

> try to run it as root
even if this works, you shouldn't need to run as root everytime you want to burn a disk...

---

### Post by knalle on 2006-02-18
perhaps k3b is set to only allow root to operate? i havent tried it

---

### Post by CarlosinFL on 2006-02-18
I agree - There should be a way to adjust this however how can I su to root? I thought I could only sudo in Ubuntu?

---

### Post by knalle on 2006-02-18
sodu su -

---

### Post by CarlosinFL on 2006-02-18
I did

```
$sudo k3b
password:
```

That worked but would like to resolve this so bash users can also burn.

---

### Post by nalmeth on 2006-02-18
open k3b as user, not root
go SETTINGS --> k3b SETUP
you will be prompted for password
at bottom of window you will see permission settings for cdrdao and cdrecord

---

### Post by 4ebees on 2006-04-29
Hi Nalmeth,

I had a related problem. Came here to see if I could fix it... found your post... fixed it!!

Thanks very much. Your advice was greatly appreciated.

---

### Post by twigboy on 2006-04-30
gksudo fixed this problem for me.  
apt-get gksudo
Its similar to when you run synaptic and that password box comes up.

---

### Post by davebgimp on 2006-05-26
While I can burn while running as root using "kdesu k3b', I'd rather assign permissions to my normal user account. How would I go about doing this for a CD/DVD writer? Running K3b Setup doesn't do the trick, it seems. I know I'm probably missing something, but it's grey territory for me. ](*,)

---

