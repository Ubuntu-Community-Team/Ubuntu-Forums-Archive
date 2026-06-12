---
title: "testdisk not in repository"
date: 2009-04-26
forum: General Help
---

### Post by afrodeity on 2009-04-26
I urgently need a working copy of testdisk. It is supposed to be in the repositories and is listed here [http://packages.ubuntu.com/hardy/admin/testdisk](http://packages.ubuntu.com/hardy/admin/testdisk).

but when I try to apt-get it

```
afrodeity@afrodeity-desktop:~$ sudo apt-get install testdisk
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
afrodeity@afrodeity-desktop:~$ 

```

I folder with all my images has disappeared on a second hard drive and need to scan it to find out what happened. This is really troubling me. Please help:confused:

---

### Post by Malta paul on 2009-04-26
Try looking for Testdisk, in System>Administration>Synaptic Package Manager.
Then type Testdisk in 'search' - I've just found it their now.
Good luck:)

---

### Post by afrodeity on 2009-04-26
Nothing. I have universe and multiverse enabled, so don't get it. I must be living in a parallel dimension. Aaaargh!

---

### Post by afrodeity on 2009-04-26
Silly me. I aborted an upgrade because it would have taken about 13 hours. The upgrade manager purged my synaptic in preparation and didn't reinstate when I cancelled. All I had to do was

```

sudo apt-get update

```

Took about 5 minutes to download the index and now I have testdisk :)

---

