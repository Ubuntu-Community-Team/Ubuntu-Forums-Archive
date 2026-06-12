---
title: "virtual box help-vboxdvr"
date: 2008-12-23
forum: General Help
---

### Post by Howitzer777 on 2008-12-23
When i try to start up my virtual machine i get a message saying the kernel doesn't have vboxdvr or something like that.how do i get that ?

---

### Post by Titan8990 on 2008-12-23
I would guess that it came with it. Does this command do anything?


modprobe vboxdvr

---

### Post by p_quarles on 2008-12-23
> **Titan8990 said:**
> I would guess that it came with it. Does this command do anything?


modprobe vboxdvr

No, it doesn't. Should be:
```
sudo modprobe vboxdrv
```
Or better yet:
```
sudo /etc/init.d/vboxdrv start
```

---

### Post by Titan8990 on 2008-12-23
I meant the module came with the package, not that it is pre-loaded in to the kernel.

---

### Post by p_quarles on 2008-12-23
> **Titan8990 said:**
> I meant the module came with the package, not that it is pre-loaded in to the kernel.

And I meant that the command you gave does nothing, because it doesn't acquire root privileges, and it misspells the name of the module.

---

### Post by Titan8990 on 2008-12-23
> and it misspells the name of the module.


That is because I copied and pasted it from OP....


And yes, leaving off sudo was my mistake. After a weekend of Gentoo, I need to get back in the sudo habit for forum support (even though I personally use sudo -i).

---

