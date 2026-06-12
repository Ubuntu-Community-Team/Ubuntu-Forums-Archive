---
title: "How to choose Desktop"
date: 2006-06-01
forum: Desktop Environments
---

### Post by pradeep79 on 2006-06-01
I installed the server version of ubuntu just to minimise the resources. My desktop of choice was XFCE, so I installed it. XFCE lacks a lot of applications GNOME has, like the network configuration utility. After a lot of fiddling with XFCE I thought its better to have a heavy-weight desktop like GNOME. So I installed GNOME from the server prompt with the command ***sudo aptitude install ubuntu-desktop***. The problem I have now are:

1. When I run the startx command at server prompt only XFCE loads, I don't know how to bring GNOME desktkop.

2. Since I really like XFCE, is there anyone who could give me some idea of how I can configure my wireless network in XFCE, is there a utility? Is there a utility to show the laptop battery power level? it seems pretty basic and lacks a lot of the functions like these. Is there a forum for xubuntu?

Looking forward to hear from you ubuntu folks very soon.

---

### Post by patrickfromspain on 2006-06-01
have you got gdm installed?? Try sudo apt-get install gdm

---

### Post by mula on 2006-06-01
In fact, you can just install the utility that Gnome uses. I did that and it ran absolutely fine. I think there's also an app called *netapplet* that should do the job.

As for the battery, you need to install either *xfce-goodies* or just *xfce4-battery-plugin*. It's simple but I didn't need anything more. But then again, I switched to Gnome after a few weeks. Sometimes I just want it to work...

---

### Post by hostilepenguin on 2006-06-01
Look in your menu, under 'system'. There should be something along the lines of 'Networking' there.

If not... Did you install XFCE via 'apt-get install xubuntu-desktop'?

---

### Post by pradeep79 on 2006-06-01
Thanks for all your replies. I haven't yet run the GNOME desktop, but I will try what Patrick said. After installing the GNOME, I can access a few of the GNOME utilities from XFCE, most importantly the network configuration. I can detect the networks in my location using this GNOME utility, which infact shows the names and stuff. Also the battery monitor popped-up when I right clicked the task bar and chose add new item. But I don't know whether this is GNOME or XFCE utility. For now I'm sorted, but I'm very new to linux, so just fiddling around with it. I think I will stick to XFCE, but would like to get rid of all the unwanted applications GNOME installer has added. Does anyone know what is the easiest way to do it retaining only the utilities I want from GNOME? Also, when I read the forums  before I installed server, it said the server version only takes 34MB of ram, but when I run the server on its own it consumes around 180MB without any desktop. Anyone know the reason, my problem is memory, I have only 256, trying to run on low memory so It would be faster.

---

### Post by PriceChild on 2006-06-01
When you get to the xfce log on screen... can't you click on "sessions" then on "GNOME".

When you log in, it should then ask you whether you want to set gnome as default or not.

This is what i did the opposite way around... ((ie logging into xfce when standardly using gnome))

P.s. not all of the memory being used is actually being used, for example i have 33% used in programs and 61% in cache right now.

Pricey

---

