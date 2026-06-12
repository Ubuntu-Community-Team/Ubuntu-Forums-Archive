---
title: "Dapper unbelievably slow after kernel upgrade"
date: 2006-07-20
forum: Desktop Environments
---

### Post by declaration on 2006-07-20
Hi,

I once had a beautifully working Dapper installation.

I then thought I would update the kernel for some reason. After that, on boot up the wireless app fails and the battery monitor fails. Ubuntu is then unbelievably slow.

I cannot think how to resolve this. The system is unusable speed wise whereas before it flew and the wireless wont work

Help would be much appreciated.

---

### Post by Lord Illidan on 2006-07-20
Run top in a terminal and post output here.

---

### Post by declaration on 2006-07-20
Hi,

Thx for the response.

I dont think it is that. The cpu usage is always very low (1-2%) and the idle usage is low (about 1%).

I think the problem may be to do with the apps failing. My gnome wireless app and the battery monitor app both fail and it asks me whether I would like to delete them?

---

### Post by Mickeysofine1972 on 2006-07-20
You can always press ESC at the grub startup bit when you switch on you computer.

The you can select what kernel to boot into

Mike

---

### Post by declaration on 2006-07-20
> **Mickeysofine1972 said:**
> You can always press ESC at the grub startup bit when you switch on you computer.

The you can select what kernel to boot into

Mike

Thanks. That worked.

My wireless isnt working still but that may be another problem altogether. Is there any way of making Grub boot a particular kernel for now? I don't wanna have to explain to my girlfriend that she has to press escape and select something every boot up.

---

### Post by Johnathon on 2006-07-21
I have had exactly the same problem, on upgrading to 2.15.26. can someone help me set the grub to boot the last version (2.16.23) as well please? 
(For me it was the clock and the network monitor!)

---

### Post by Mickeysofine1972 on 2006-07-21
Once you have booted into the old stable kernel you can remove the new one and then GRUB should boot from the kernel that is left in the list.

Mike

BTW I have the same problems with the .26 kernel, I kills my nvidia video drivers. Even after a re-install of the drivers I just get the Kubuntu startup screen and no KDE!. so my only solution is to revert back to the older kernel too ](*,)

---

### Post by Johnathon on 2006-07-21
Thanks for the help! Thats worked :)

---

