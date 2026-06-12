---
title: "Wired Networks, Device not managed"
date: 2010-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ndegwa on 2010-05-29
Hi Team,

   Kindly note that i installed the laptop below with the noted Ubuntu OS and at first worked fine with Ethernet until i updated the system and the subject line shows up at the Network icon when clicked.
  
   Dell Vostro A860 System BIOS, A02 ,Lucid Lynx 10.04


  Also note that i've gone through BIOS settings and the only item pertaining to Networks is the wireless adapter with the usual disable/enable options.


Anyone to my rescue!!!!!!!!!!!!!!!!!!!

---

### Post by ugm6hr on 2010-05-30
> **Ndegwa said:**
> .. the subject line shows up at the Network icon when clicked.

Sorry - don't get what you mean.

It appears you have had a problem with an update - it might help to know what chipset you are using to see if this has been reported.

```
lshw -class network
ifconfig
```

---

### Post by rahmads89 on 2011-07-22
I have a same trouble. 
My chipset is sis 191, I use ubuntu 10.04 kernel 2.6.32-21-generic
Network notification display information that the "device not managed"

I try with dmesg, and the result :

[ 3830.828031] eth0: auto-negotiating...
[ 3840.852036] eth0: auto-negotiating...
[ 3850.876137] eth0: auto-negotiating...

I try to change MTU to whatever except 1500,  but It did'nt work

---

