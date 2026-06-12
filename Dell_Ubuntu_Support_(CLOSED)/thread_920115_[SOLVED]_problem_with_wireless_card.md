---
title: "[SOLVED] problem with wireless card"
date: 2008-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by N4zgu1 on 2008-09-14
I have a problem with my wireless card. 
I just installed ubuntu, I have a dual boot with windows vista
The problem is that when I click on network I only have the options of wired conection and point to point connection but I dont have the wireless option.





I have a dell inspiron 1535
this is my wreless card:

```
tarjeta mini-PCI de red inalámbrica WLAN 1395 de Dell
```

P.d: Sorry I have the spanish version of vista, but I will search the correct name

---

### Post by Diggs808 on 2008-09-15
> **N4zgu1 said:**
> I have a problem with my wireless card. 
I just installed ubuntu, I have a dual boot with windows vista
The problem is that when I click on network I only have the options of wired conection and point to point connection but I dont have the wireless option.





I have a dell inspiron 1535
this is my wreless card:

```
tarjeta mini-PCI de red inalámbrica WLAN 1395 de Dell
```P.d: Sorry I have the spanish version of vista, but I will search the correct name

If my Spanish isnt completely rusty...sounds like you have the Dell WLAN 1395 card right?

---

### Post by lronclawbigun on 2008-09-15
Now today we discuss the game of warhammer online. Warhammer online is the full name of this game ,warhammer always abbreviation of war ,so [warhammer power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) often called war power leveling, and in fact. All war power leveling , [war power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling), [warhammer online power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) is the same meaning ,so here not to puzzle with this.firstly ,when you want  [Warhammer cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey),i suggest you go to gamevive.com. They sell the lowest price for warhammer gold and other [warhammer online cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey) .and their delivery  is fastest.it is worth to try.

---

### Post by N4zgu1 on 2008-09-15
Yes, I think that's my wireless card, do you know how can I solve the problem

---

### Post by timjohn7 on 2008-09-15
I don't have the same card, nor am I a Linux or wireless expert but I found that using wicd instead of network manager helped a few people.

Install wicd using Synaptic and reboot.

Let me know what happens!

Cheers

---

### Post by Kevbert on 2008-09-15
I believe that adapter is based on the Broadcom BCM94311.  You can check this by entering
```
lspci
```
in terminal (under Applications - Accessories).  If so you can use this [[COLOR="Red"]post.[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")

---

