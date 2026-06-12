---
title: "Freeze after Resume with Blinking Caps and Scroll Lock LEDs"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2008-06-27
Ubuntu on Dell 1420n keeps freezing up after resume with the Caps and Scroll lock LEDs blinking.

What does this mean?

I know this is Ubuntu because Windows XP has no problems resuming on the same laptop.

---

### Post by agentbad on 2008-10-28
I have the same problem on my toshiba laptop with the newest version of ubuntu 8.04.

---

### Post by daemonk on 2008-10-29
I have the same problem toshiba Q210

---

### Post by stir-crazy on 2008-11-07
Me too with a Dell Inspiron B130.  I notice the issue occurs most often when I'm attempting to connect to the internet.  Sometimes not the case, but usually it is.

I'm fairly sure that this has only been since I updated to 8.04.

---

### Post by tekio on 2008-11-19
I'm having the same problem. I'm fairly sure it is a Kernel panic. I'm suspecting the Intel 4965 Wlan card. Anyone else with this card?

---

### Post by tekio on 2008-11-20
I just wanted to add the diagnosis above was correct. The Intel 4965 drivers were causing random kernel panics. I've switched to a Belkin PC Express with Ralink 2860 chipset. After disabling the Intel everything is just perfect. Not sure if there is a fix for the Intel issue yet, as it is quite common with Ubuntu.

---

### Post by obscenic on 2009-01-13
Same problem, same chipset (4965).

Has anyone solved this yet?  Or opened a bug report?

---

### Post by lunatico on 2009-03-20
I think I have this same issue.

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Looking for an answer...

---

### Post by lunatico on 2009-03-23
> **lunatico said:**
> Looking for an answer...

I think I fixed my problem.

Installed the following packages:
linux-backports-modules-2.6.27-11-generic (2.6.27-11.12)
linux-backports-modules-intrepid (2.6.27.11.14)
linux-backports-modules-intrepid-generic (2.6.27.11.14)

Have been using it and no lockups so far. The above updates the wifi drivers to newer ones.

---

### Post by jmlaniel on 2009-03-23
I have the same problem on an inspiron 6400.

I experienced the lockup with 8.10 in 32 and 64 bits.

I will try the solution and see what happens... I'm just glad that other people have experienced the same things because I have read elsewhere that this might be an indication of bad RAM or motherboard!!!

---

### Post by lunatico on 2009-03-23
> **jmlaniel said:**
> I have the same problem on an inspiron 6400.

I experienced the lockup with 8.10 in 32 and 64 bits.

I will try the solution and see what happens... I'm just glad that other people have experienced the same things because I have read elsewhere that this might be an indication of bad RAM or motherboard!!!

Well it could be RAM or motherboard, but if you have the same wireless card as us then have a look at the system logs after this happens again. You can also run a mem test to make sure it's not RAM.

---

### Post by lunatico on 2009-03-27
> **lunatico said:**
> I think I fixed my problem.

Installed the following packages:
linux-backports-modules-2.6.27-11-generic (2.6.27-11.12)
linux-backports-modules-intrepid (2.6.27.11.14)
linux-backports-modules-intrepid-generic (2.6.27.11.14)

Have been using it and no lockups so far. The above updates the wifi drivers to newer ones.

After a week of using the computer I can say now that this fixed the issue.

---

