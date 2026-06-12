---
title: "adding new user to k3b"
date: 2005-05-07
forum: Desktop Environments
---

### Post by msxuser on 2005-05-07
hi! how i can add new user to k3b and recognise the cdwriter? with my normal user the k3b recognise the cdwriter, but with another user not recognise!

where is k3bsetup2?

regards

---

### Post by eivind on 2005-05-09
[QUOTE=msxuser]hi! how i can add new user to k3b and recognise the cdwriter? with my normal user the k3b recognise the cdwriter, but with another user not recognise!

where is k3bsetup2?

regards[/QUOTE]
 Hm. Since k3b is a kde program, you should be able to run it as root _once_ in order to add other users. To do that, click K-menu -> run program -> and type

kdesu k3b 

in the box that appears. Next, you have to type in the sudo password. Maybe this could fix your problem.

Eivind

---

### Post by msxuser on 2005-05-10
[QUOTE=eivind]Hm. Since k3b is a kde program, you should be able to run it as root _once_ in order to add other users. To do that, click K-menu -> run program -> and type

kdesu k3b 

in the box that appears. Next, you have to type in the sudo password. Maybe this could fix your problem.

Eivind[/QUOTE]
 When I enter as user root al k3b is as if will enter with a normal user, there is not any advantage or menu to add users?  

How can I do it?  

Regards,

---

### Post by tomchuk on 2005-05-10
Have you tried adding the other users to the cdrom group? This is the group that owns your cd device and you must be a member of that group to write to the device.

---

### Post by msxuser on 2005-05-13
it settled! really one must add it in the group cdrom, thanks by your contribution :)

[QUOTE=tomchuk]Have you tried adding the other users to the cdrom group? This is the group that owns your cd device and you must be a member of that group to write to the device.[/QUOTE]

---

