---
title: "apt-get : could not find package k9copy"
date: 2006-08-04
forum: Desktop Environments
---

### Post by kvalis on 2006-08-04
Was iniatally thinking of installing wine and dvdshrink, but on the Ubuntu pages I got the clear understanding that is the last resort to try. I was then recommended to get hold of K9copy for 6.06.

I then entered command as desribed:

> tore@ubuntu:~$ sudo apt-get install k9copy
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package k9copy

What must I do?

kvalis

---

### Post by cantormath on 2006-08-04
> **kvalis said:**
> Was iniatally thinking of installing wine and dvdshrink, but on the Ubuntu pages I got the clear understanding that is the last resort to try. I was then recommended to get hold of K9copy for 6.06.

I then entered command as desribed:


What must I do?

kvalis

Applications>Add/Remove
click on the commercial and unsupported boxes. reload.
search k9copy, and it should be there.


If you want to do it the hard way............

you need to add the universe repository.

$:\ sudo gedit /etc/apt/sources.list
uncomment universe and save
$:\ sudo apt-get update
$:\ sudo apt-get install k9copy

  After you install it, Its safest to comment out the repository.  You dont want to be updating from the universe/multiverse/backports unless you know what you are doing .

---

### Post by kvalis on 2006-08-04
Thank you cantormath  	


I took the easy route.  Now I will take my time and try it out.
Thanks again

kvalis

---

