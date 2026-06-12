---
title: "networking stopped working after update"
date: 2010-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blinkybunny on 2010-06-30
Hi, I am using a new handle because don't remember my old one. I have been using Ubuntu since around dapper drake / edgy eft time period and this has never happened to me. I am using a dell mini 10v with the full version of ubuntu 10.04 (no netbook remix stuff) with a 320gb hd 2gb ram (which I added after purchase), I installed ubuntu a month ago, dual booting with a cloned image of xp that came from the original HD (probably not relevant but I know its helpful to have as much info as possible).

It all started this morning after updating. after updating I rebooted my netbook and networking stopped working. Wireless never worked right for me, I installed the proprietary drivers that were noted from various ubuntu documentation, and the best I got was I was able to see wireless networks but unable to connect to them. No other notable problems occurred that I can tell. I know the wifi card works because it worked in windows and from live booting knoppix. I restarted networking and wireless to see if that would fix it, and no dice.

---

### Post by mikewhatever on 2010-06-30
Can you post the outputs of the following:

lspci | grep -i net
ifconfig
lsmod | 'grep wl\|r8169'

---

### Post by blinkybunny on 2010-07-01
> **mikewhatever said:**
> Can you post the outputs of the following:

lspci | grep -i net
ifconfig
lsmod | 'grep wl\|r8169'


I am not sure what happened but after I restarted networking several times and rebooted several times my wired network connection started working again. wireless is still not working.

---

### Post by /b/rotard on 2010-07-03
> **blinkybunny said:**
> I am not sure what happened but after I restarted networking several times and rebooted several times my wired network connection started working again. wireless is still not working.

lspci | grep Network

Use this and/or the command the guy above me posted.

---

