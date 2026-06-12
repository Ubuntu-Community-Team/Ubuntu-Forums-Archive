---
title: "[SOLVED] can not get the desktop......!!!!!!"
date: 2008-12-20
forum: General Help
---

### Post by chinmaya_n on 2008-12-20
[B]This is very serious problem.......!!!

I had just installed compiz....when i was checking all effects it happend....:oops:

when i marked on one effect in compiz settings manager.... it just logged off then it displayed login window.... when i tried to login then it displayed a blue screen and again displayed the login window.... (it is not proceeding to show desktop....) the login password and user name are correct...   when i rebooted it, it acted in the same way... it didn't show the desktop.... just logged in and logged out automatically...........!!!!!:confused:

can anyone please please please help me ..... 

>>can any one give some commands for removeing that compiz using live cd..... so that after getting dektop... i can again install that compiz

NOTE: i'm using 3gb of ram... and c2d processor.... and 128mb graphics inbuilt card ;

I'm stuck with this ....plz help:cry: ( I'm sending this msg 4m the other OS in my system )[/B]

---

### Post by albinootje on 2008-12-20
> **chinmaya_n said:**
> 
>>can any one give some commands for removeing that compiz using live cd..... so that after getting dektop... i can again install that compiz


Boot from the live-cd.
Check whether your Ubuntu-partition is there.

Find out where your Ubuntu partition is mounted by typing :
```
mount 
```

Let's imagine, in this example that your Ubuntu partition is mounted in /media/disk

Then do the following :
```

sudo chroot /media/disk
apt-get remove compiz compiz-core
exit

```
After that reboot without the Ubuntu live cdrom.

---

### Post by chinmaya_n on 2008-12-20
[B]
when i tried to execute these commands on live cd it displayed
"ubuntu@ubuntu:~$ sudo chroot /media/disk-2

 chroot: cannot run command `/bin/bash': Exec format error "

but i runned

 "$apt-get remove compiz compiz-core" 

in the root terminal 4m recovery mode.... then it removed the compiz packages.......... then i got my desktop back..!!! 

Thanks ........ 4 everything.....!!

Does u know the reason why it happend ...???
[/B]

---

