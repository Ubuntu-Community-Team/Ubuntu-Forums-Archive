---
title: "GRUB menu messed up after updates?"
date: 2009-03-16
forum: General Help
---

### Post by mahela007 on 2009-03-16
HI.. My GRUB menu has two extra entries after i performed. the update. I'm comfortable with editing the GRUB entries. However I don.t know which ones to delete. 
which one is newer?
kernel 2.6.17-11 or kernel 2.6.17-7?
 I'm guesing the first one  is newer and i should delete the entry for the second one?

---

### Post by drs305 on 2009-03-16
the higher number is the more recent. You can find which kernel you are running with:
```

uname -r

```

You can use StartUp-Manager to set the default kernel and what you see. It can also limit the number of entries you see when the next kernel is added. There is a link in my signature line to a guide  if you are interested (even if comfortable with editing menu.lst ;-)  )

---

### Post by mahela007 on 2009-03-17
I used the "GRUB EDITOR" application in kubuntu.
Do the dual entries mean that I now have both versions of the linux kernel installed?

---

### Post by ruel- on 2009-03-17
happens to every ubuntu user, I havent tried entering on an outdated kernel, I just removed it from the list... maybe it was just appended by grub when the update is finished..(sorry for my crappy english)

---

### Post by mahela007 on 2009-03-17
Well I tried entering on the older version and it works.. So that means that I have both versions installed right? I'm confused. What use is an update if all it does it install another completely new version rather than make changes in the older version? I mean, at the very least is just eats up hard disk space right?

---

### Post by ruel- on 2009-03-17
What I exactly mean is.. "maybe" the kernel updated... and GRUB detected the new kernel version.. and instead of changing the previous line, it just appended another one..

EDIT: and, no I dont think you can have 2 kernel versions installed..

---

### Post by mahela007 on 2009-03-17
> **drs305 said:**
> the higher number is the more recent. You can find which kernel you are running with:
```

uname -r

```You can use StartUp-Manager to set the default kernel and what you see. It can also limit the number of entries you see when the next kernel is added. There is a link in my signature line to a guide  if you are interested (even if comfortable with editing menu.lst ;-)  )

I checked out your guide. (It's very useful). So does this mean I can delete the older kernel if a want to?

---

### Post by zvacet on 2009-03-17
@ **mahela007**

> So does this mean I can delete the older kernel if a want to?

Yes,you can delete older kernel,but I think it is smart to have two kernels.Just in case then something goes wrong with one you have other to boot in.

---

### Post by drs305 on 2009-03-17
> **mahela007 said:**
> I checked out your guide. (It's very useful). So does this mean I can delete the older kernel if a want to?

As zvacet stated, it is probably a good idea to keep at least two working kernels on your menu (and in the system). If you start having problems with the new kernel you can use the older one to troubleshoot or use until an even newer kernel appears.

The exact answer to your question is that *yes* you can delete the older kernel if you really want to. This would include the "linux-image-2.6.17-7" or "linux-image-2.6.17-7-generic" (depending on which you have installed) as well as it's associated linux-headers-2.6.17-7... and linux-restricted-modules-2.6.17-7...,  Unless you really need the space, though, I'd keep one backup.

---

