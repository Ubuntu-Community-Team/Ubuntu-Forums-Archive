---
title: "Firestarter isn't working.."
date: 2006-06-03
forum: Desktop Environments
---

### Post by rubso on 2006-06-03
Hi, i've installed Ubuntu Dapper Drake at last :mrgreen: 
i installed Firestarter too, but it didn't work, these are the error messages i get ..
GUI/Firestarter
> Failed to Start the firewall

The device eth0 is not ready

Please Check your network device settings and make sure your internet connection is active
and when i type firestarter in the terminal i get this error message
> rubso@rubso-desktop:~$ sudo firestarter
Internal network device eth0 is not ready. Aborting..

how about helping me ? :-#

---

### Post by meng on 2006-06-03
One assumes that your eth0 is working, correct?

---

### Post by pump on 2006-06-03
How many eth cards do you have?
Do you want to enable NAT?

---

### Post by Rackerz on 2006-06-03
Are you using the internet fine through Dapper? How many connections do you have?

---

### Post by rubso on 2006-06-03
> One assumes that your eth0 is working, correct?
my eth0 is working, "System -> Administration -> Networking" = eth0 is active
> How many eth cards do you have?
1 eth card only
and i want to share my Wireless Internet Connection "ath0" to "Local Area Connection" = "eth0" and i can't do it till now
> Are you using the internet fine through Dapper? How many connections do you have?
yeah everything is working fine i'm connected through a wireless connection, ( 1 wireless internet connection ) only.

---

### Post by pump on 2006-06-03
Check if NAT is enabled from the firestarter config. But that would be very weird as you have just one card.

---

### Post by rubso on 2006-06-03
i don't know where is the firestarter config file ...

---

