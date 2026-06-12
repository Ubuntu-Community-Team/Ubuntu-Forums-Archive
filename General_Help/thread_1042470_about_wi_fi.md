---
title: "about wi fi"
date: 2009-01-17
forum: General Help
---

### Post by azee heso0 on 2009-01-17
i have linux (ubuntu) opreting system, I wanna turn on the WI FI but i can't doing it.

what is the slotion exactly ??

---

### Post by ac7ss on 2009-01-17
Try using wicd.

if that doesn't work, you will need to explore via the shell.

try finding the wifi unit with 
```
iwconfig
```

you should see something like 
```
eth1      IEEE 802.11b/g  ESSID:"Net"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:11:22:33:44:55
          Bit Rate=24 Mb/s
          Link Quality=89/100  Signal level=32/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
if the adapter is up. If it is down, the ESSID and Access Point fields will be blank.

Beyond this we need more information. What card are you using, what version Ubuntu, is it an internal or USB card. etc.

---

### Post by albinootje on 2009-01-17
> **azee heso0 said:**
> I wanna turn on the WI FI but i can't doing it.

Can you post the output of the following in a terminal :
```

sudo update-usbids
lsusb
lspci
sudo lshw -C network

```
Thanks.

---

### Post by azee heso0 on 2009-01-18
Helo0 , thank 4 us , i will try it now

i c and i tallk us what Happened with me 

thank 4 us again

---

### Post by azee heso0 on 2009-01-19
:cry:  hi bro0 ,, i try it but i dont understed any thing

clear mo0re please

---

### Post by albinootje on 2009-01-19
> **azee heso0 said:**
> :cry:  hi bro0 ,, i try it but i dont understed any thing

clear mo0re please

Please copy & paste the results of those earlier mentioned commands here.

Is another language than english better for you to communicate in ?

---

### Post by azee heso0 on 2009-01-19
o0k bro0 i will try again 

10x 4 u

---

### Post by azee heso0 on 2009-01-20
ok bro0 see

[IMG]http://thumbs.bc.jncdn.com/718ac51ab3a8038ed83db15f8305eac6_s.jpg[/IMG]

---

