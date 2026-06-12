---
title: "cant detect my wirless router but can see others?"
date: 2008-12-28
forum: General Help
---

### Post by ohmyjibbonjones on 2008-12-28
hey guys,
        i recently decided to install ubuntu 8.10 after having previous experience with an older version (7.04 i belive).when using 7.04 all seemed to work fine with my dell xps m1330 (ie wifi card,graphics card etc) but upon installing 8.10 nothing seems to work.
when i go to connect to my router via wi-fi it is not visable (i can see my neighbours routers) which has led me to belive it is not a driver issue.it also will not let me install my graphics drivers so that i can experience the full interface.
if there is anyone who can provide sum assistance it would be grately appreciated.
thanks

---

### Post by hxcgrunger on 2008-12-28
It might not be Ubuntu thats the problem. Is the router setup to broadcast it's SSID?

---

### Post by ohmyjibbonjones on 2008-12-28
no but i even set it top broadcast and it still wouldnt work.its a netgear dg834g if that helps.
edit: oh and i forgot to mention when i look at the wpa key after i type in the correct one it turns into 20 digits of gibberish (after i try to connect)
i think i read somwhere that the key gets "lost"?

---

### Post by hxcgrunger on 2008-12-28
So you've tried entering the ESSID manualy then?

---

### Post by melojo on 2008-12-28
Open a terminal and post the ouput of

```
iwlist scan
```

---

### Post by zzztownsend on 2009-01-14
Hi

I had the same problem. I fixed it by going into the netgear wireless setup and changing the channel number from 12 to 5, using a PC on a wired connection.

No idea why this caused a problem because my eeepc has no problem connecting regurlarly and reliably using default xandros linux OS, but I could not get ubuntu to work, despite my neighbours routers being visible.

to scan to see if your router is visible to your laptop, do 
$ sudo iwlist scan

Mystery !

Matt

---

### Post by tbj61898 on 2009-01-21
> **zzztownsend said:**
> Hi

I had the same problem. I fixed it by going into the netgear wireless setup and changing the channel number from 12 to 5, using a PC on a wired connection.


Yep. That's due to different wireless frequency law between different place. As an example in Italy we get channels from 1 to 13, but others only get it to 12 or even less, japan should support channels until 14. Other nations only have a channel or two.

so: if the driver you are using is not aware of your geographical location it may not be able to set/scan proper channels and would be, indeed, illegal since it may use prohibited frequencies.

Bye,
Andrè:KS

---

