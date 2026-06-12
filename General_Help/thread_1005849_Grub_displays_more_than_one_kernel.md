---
title: "Grub displays more than one kernel"
date: 2008-12-08
forum: General Help
---

### Post by billytalent on 2008-12-08
Hey everyone, 

I have searched around for a solution to this problem but have yet to come across a solution for a new/noob linux user. 

Ubuntu us displaying 2 kernels in the grub menu, what i would like to have is just one + my vista install. 

How can i do this? A step by step would be great. 

Thank you guys!!!

---

### Post by MarblePanther on 2008-12-08
Install startup-manager and use that to organize your grub

uninstall any old kernels you don't need in synaptic

edit:

it is always good to have a backup kernel

---

### Post by binbash on 2008-12-08
you can uninstall the old kernel or the other one.OR you can remove it from grub by editing /boot/grub/menu.lst

---

### Post by scottuss on 2008-12-08
Yes I would agree with having a backup kernel, last thing you want is for an update to be applied to your one and only kernel and have it ruined beyond belief so that it wont boot

---

### Post by billytalent on 2008-12-08
Tried that, with no luck. Ill try marble panthers route. Cheers guys, what a fast reply.

---

### Post by billytalent on 2008-12-08
> **scottuss said:**
> Yes I would agree with having a backup kernel, last thing you want is for an update to be applied to your one and only kernel and have it ruined beyond belief so that it wont boot

see thats what happened, i installed, updated and then somehow ended up with more than one kernel.

---

### Post by MarblePanther on 2008-12-08
Btw, i believe ubuntu keeps your current kernel and a backup and automagically updates grub and removes the third old kernel


You *should* have 2 kernels

---

### Post by scottuss on 2008-12-08
> **MarblePanther said:**
> Btw, i believe ubuntu keeps your current kernel and a backup and automagically updates grub and removes the third old kernel


You *should* have 2 kernels

Yep, that's what it does. It's by design and it's a *good* design!

:lolflag:

---

### Post by MarblePanther on 2008-12-08
Oh yeah, especially if you are learning to compile kernels
:lolflag:

---

### Post by scottuss on 2008-12-08
I'll second that!

---

### Post by Sjeti on 2008-12-08
If you still want to remove the kernels from the list, you just need to open up your grub menu.lst and comment out all the unwanted kernels.

```

sudo gedit /boot/grub/menu.lst

```

---

### Post by Musicalmidget on 2008-12-08
Alternatively, I believe you could uncomment and change the value of *howmany* in /boot/grub/menu.lst to the number of kernels you want to display on boot.  For instance, changing the line to *howmany=2* will only show the latest two kernels, whereas I think the default is *howmany=all*.

---

### Post by billytalent on 2008-12-08
Hey guys, 

tried everything, but i still get 2xkernel + my vista install. 

Must be an Ubuntu auto override.

---

### Post by MarblePanther on 2008-12-08
in startup-manager under one of the tabs you can limit the number of kernels
[ATTACH]95732[/ATTACH]

have you installed startup-manager?

---

### Post by billytalent on 2008-12-08
> **MarblePanther said:**
> in startup-manager under one of the tabs you can limit the number of kernels
[ATTACH]95732[/ATTACH]

have you installed startup-manager?

yeah mate, did all that, the limit is on one kernel, but it aint changing!

dont stress, thanks for the help :)

---

### Post by MarblePanther on 2008-12-08
that's odd, hmmmmm

maybe you can't have less than 2 kernels (I would keep both)

---

