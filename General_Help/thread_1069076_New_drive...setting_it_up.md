---
title: "New drive...setting it up"
date: 2009-02-13
forum: General Help
---

### Post by robmypro on 2009-02-13
I am adding another hard drive (internal SATA) to my 8.10 desktop system. I can see the drive on the desktop, but what I would like to do is format it, and then share it out to other users. Some would be Windows clients and others would be Linux users.

What do I need to do to format this drive? I figure I will use Samba once I get that far. 

Ah...to be so green!

Thanks.

---

### Post by olskar on 2009-02-13
> **robmypro said:**
> I am adding another hard drive (internal SATA) to my 8.10 desktop system. I can see the drive on the desktop, but what I would like to do is format it, and then share it out to other users. Some would be Windows clients and others would be Linux users.

What do I need to do to format this drive? I figure I will use Samba once I get that far. 

Ah...to be so green!

Thanks.


To format it you can use gparted avaible in Synaptic

---

### Post by kestrel1 on 2009-02-13
Use Gparted to format the drive.
If you don't have it installed type ```
sudo apt-get install gparted
```
you can either run it from the terminal by typing ```
gparted
```
or go to 
System -> Administration -> Partition Editor.
For the Windows users you would need samba

---

### Post by Yellow Pasque on 2009-02-13
```
sudo apt-get install gparted
```
Make sure the new disk isn't mounted and fire up gparted (System -> Administration -> Partition Editor).

EDIT: I don't type fast enough.

I should also mention that you can use the partition editor on the Ubuntu LiveCD (just make sure to choose the right disk ;) )

---

### Post by robmypro on 2009-02-13
Thanks guys. Works great.

---

### Post by robmypro on 2009-02-13
Okay...I actually have a couple questions. This extra drive. I formatted it as Ext3. So I guess now I have to mount it?

I don't want this drive to show on my desktop, but if I go to Computer I guess it should show? 

What is the norm in this case? It is going to be extra storage. In Windows it would just show as another drive letter. What is the Linux way to do this?

Thanks again.

---

### Post by robmypro on 2009-02-13
Okay got it guys. Is it typical to show internal drives on the desktop?

---

### Post by kestrel1 on 2009-02-13
Mounted drives do show on the desktop

---

### Post by robmypro on 2009-02-13
> **kestrel1 said:**
> Mounted drives do show on the desktop

Thanks!

---

