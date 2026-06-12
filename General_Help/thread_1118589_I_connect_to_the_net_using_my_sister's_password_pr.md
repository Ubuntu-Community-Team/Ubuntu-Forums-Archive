---
title: "I connect to the net using my sister's password protected Netgear with no password"
date: 2009-04-07
forum: General Help
---

### Post by wandalalakers on 2009-04-07
I can connect to the Internet using my sister's password protected Netgear with no password.  Has anyone seen this?  I'm using kubuntu 8.04.2.
I have a Linksys at home that I use at home to connect my Dell laptop to the Internet wirelessly. I took my laptop to my sister's house and I can connect to her Netgear with the same laptop and it doesn't prompt me for a password. I password protected her Netgear and knetwork manager has a lock next to the wireless network name. Just for giggles, I selected another wireless network and then tried my sister's again but I still was able to connect without a password. I was just wondering if anyone else has had this problem. I guess if I had a windows laptop I would try it. (This laptop used to have windows on it but of course since I discovered *buntu, that what I use on it)
You know I thought I would have to setup her wireless settings on my laptop. If I had a windows laptop I would have to do this, right? I guess I'm kinda confused. I had to do this for my Linksys, at least from what I remember. Basically, I'm pretty sure I had to input my wireless info on my laptop in order to use my Linksys at home. I did access the router using 192.168.x.x and it prompted me for a username and password. I just thought that I had to enter the wireless info on this laptop in order to use my sister's Netgear. I'm using WPA at home and she's using WEP. I've been meaning to change her setup to WPA.

---

### Post by plucky on 2009-04-07
What does ```
sudo iwlist scan
``` show you for her network?

---

### Post by lisati on 2009-04-07
I have a Netgear router - it has two passwords, one for WEP or WPA or whatever, and one for admin options. It doesn't need a password for a wired connection when accessing the internet.

---

### Post by wandalalakers on 2009-04-07
> **plucky said:**
> What does ```
sudo iwlist scan
``` show you for her network?

I'm home now.  I guess I'll have to go back to her place.  Thx.

---

### Post by wandalalakers on 2009-04-07
> **lisati said:**
> I have a Netgear router - it has two passwords, one for WEP or WPA or whatever, and one for admin options. It doesn't need a password for a wired connection when accessing the internet.

I'm accessing the Internet via wireless at her place with no password even though I've password protected her Netgear.  I'll try to go back to her place this weekend.  Thx.

---

