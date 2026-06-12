---
title: "Cannot restore grub after XP installation"
date: 2009-02-25
forum: General Help
---

### Post by Souljah on 2009-02-25
Hi,

I was doing my regular format/reinstall with XP, though I hardly use it. I'm using ubuntu v8.04 and when I use the LiveCD to try to restore grub it tells me that ```
find: /boot/grub: No such file or directory
```. So I think that the grub boot file has someone been deleted. I'm not sure what to do to get it back. I can browse both the drives of ubuntu and linux through the 'places' menu. What can I do? Thanks.

P.S. When I browse to the directory, stage1 is there in the boot folder. Why can't the terminal find it I don't know.

---

### Post by sim-value on 2009-02-25
Try from Terminal 
sudo grub
then
```
find /boot/grub/stage1
```

---

### Post by Souljah on 2009-02-25
> **sim-value said:**
> Try from Terminal 
sudo grub
then
```
find /boot/grub/stage1
```

Umm.. that's what I was actually trying and it was giving me an error output. Whether you sudo it or not. :(

---

### Post by sim-value on 2009-02-25
and when you try root(hdX) and setup(hdx) directly ?

---

### Post by Souljah on 2009-02-25
> **sim-value said:**
> and when you try root(hdX) and setup(hdx) directly ?

```
grub> find /boot/grub/stage1

Error 15: File not found

grub> setup (hd0)

Error 12: Invalid device requested

grub> 

```

---

### Post by Souljah on 2009-02-25
It is now fixed. I simply did a restart and retried the commands and it worked. I don't know why a restart would fix it but oh well. Lol. I wonder how do I change this topic to solved.

---

