---
title: "broad band connection with ubuntu 9.04"
date: 2010-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mann1988 on 2010-01-07
I am unable to connect my bsnl broad internet connection with ubuntu9.04.
I am a begginer so pls help me to sort out my prblm............:(
 
I am currently using dell inspiron 1525 with ubuntu 9.04,simultaneuosly with windows vista.

---

### Post by bobcollard on 2010-01-07
> **mann1988 said:**
> I am unable to connect my bsnl broad internet connection with ubuntu9.04.
I am a begginer so pls help me to sort out my prblm............:(
 
I am currently using dell inspiron 1525 with ubuntu 9.04,simultaneuosly with windows vista.
Here is a step by step link, hope it will help you:                                    *[http://dimitar.me/?p=728](http://dimitar.me/?p=728)*

---

### Post by dineshs on 2010-01-09
BSNL Broadband can be connected in 2 ways. 
1.ALWAYS ON or PPPoE mode. 
2.Bridge mode or using a dialler
In the first method you have to configure your modem using the username and password as given by BSNL.This method is easier because you can directly use your web browser 3 minutes after switching on the modem.
In the second method you have to Bridge the modem then use command line to connect/disconnect broadband.First you have to use the command 
```
sudo pppoeconf
```
to configure then use 
```
pon dsl-provider
```
to connect and
```
poff dsl-provider
```
to disconnect

---

