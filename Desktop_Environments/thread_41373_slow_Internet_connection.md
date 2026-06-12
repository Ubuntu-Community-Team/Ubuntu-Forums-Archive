---
title: "slow Internet connection"
date: 2005-06-13
forum: Desktop Environments
---

### Post by jrev on 2005-06-13
Hi all,
I just installed the ubuntu 5.04 on my desktop 
and my connection runs at 1or 2 Kb/sec instead of the 5 or  6 Kb/sec It used to be on the same computer with suse 9.1 & 9.2 
What can be the problem ?
thanks

---

### Post by defkewl on 2005-06-13
Too many services or application running. CMIIW

---

### Post by jrev on 2005-06-13
only firefox running with the external modem olitec...

---

### Post by defkewl on 2005-06-16
Type 
$ ps -aux

to see what services is running

---

### Post by jrev on 2005-06-17
I installed ubuntu 5.04 twice :

first time with the DVD I bought from my local news agent 
the second time from a CD downloaded and burnt OK

the installation went fine to the end both times & I could configure my browser and all

I am using a dialup connection with an external modem 56K and 
this doesn't suit Ubuntu

Why ? this is the question 
Did I do something wrong ?
This is not the first time that a Linux distro doesn't boot or doesn't work on my 3 PC's

I just wondered if anybody had the same problem. The answer is "Yes"

and sorry to say it but it's not the load or anything wrong with my machine which operated for a year now with suse 9.1 or 9.2 without any problem.

There must be a bug with this distro and the dialup connection...

 :)

---

### Post by defkewl on 2005-06-19
Have you turned ppp service on?

---

### Post by desdinova on 2005-06-19
Install "setserial" and set your serial ports to hispeed

---

### Post by dbk on 2005-06-19
1.#apt-get install pppconfig
 man pon,man poff
or
2.#apt-get install minicom
  $minicom -s

---

### Post by jrev on 2005-06-19
thanks for your help ...
it was the gnome-ppp package that was missing on the install DVD and also on the Install CD I used 
a Ubuntu bug as it was ! ! !
I downloaded it from another PC and installed it

---

