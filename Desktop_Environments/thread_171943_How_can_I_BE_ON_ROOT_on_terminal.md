---
title: "How can I BE ON ROOT on terminal?"
date: 2006-05-07
forum: Desktop Environments
---

### Post by sidy on 2006-05-07
Hi there,

On my PC I've got 2 hdds one of 40 (slaeve) that I'm running right now and another of 80 (master) where my datos are. (I want to tranfer all the datos from the hdd of 80 to the 40 to have datos in then both, for security reasons)

So, I need to mount the hdds 'A' hda1, hda2, hda3, to get access to the other hd '80'.

But on terminal it tells me to be on root.

HOW CAN I BE ON ROOT?

Thanks again.

---

### Post by green1152 on 2006-05-07
type:
sudo su

Then put in your password. You will be able to do what you want after that.

---

### Post by tennvols_69 on 2006-05-07
[QUOTE=sidy]Hi there,

On my PC I've got 2 hdds one of 40 (slaeve) that I'm running right now and another of 80 (master) where my datos are. (I want to tranfer all the datos from the hdd of 80 to the 40 to have datos in then both, for security reasons)

So, I need to mount the hdds 'A' hda1, hda2, hda3, to get access to the other hd '80'.

But on terminal it tells me to be on root.

HOW CAN I BE ON ROOT?

Thanks again.[/QUOTE]

if you do not have root password set you must do so. to do it hit ctrl+alt+F1 then login  with your username and password then type the following:
sudo su then hit retun
passwd then hit return
then type in the password you want to use as root. this will need to be done twice. after boot hit return. your root password is now set.  you can now hit ctrl+alt+f7 to return back to x.  then do what was posted before.

---

