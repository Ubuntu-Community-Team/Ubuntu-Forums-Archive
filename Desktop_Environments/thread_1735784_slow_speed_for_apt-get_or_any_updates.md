---
title: "slow speed for apt-get or any updates"
date: 2011-04-21
forum: Desktop Environments
---

### Post by bardminz on 2011-04-21
Hi,

I have a very strange problem. The download speed drops dramatically a few seconds after I start apt-get actions (from 100 K/s to 1k B/s). I'm using Comcast with a 100k-200k normal download speed. I've tried automatically selecting the source but ubuntu fails finding any best one. The one in use is osuosl.org, which is ok if I update my system at school.

Does anybody know what's going on here?

Thanks in advance,
XL

---

### Post by bardminz on 2011-04-27
bump

It bothered me a lot. Could anyone shed some light here? I can paste some log file although am not sure about which one.

---

### Post by Yellow Pasque on 2011-04-27
Where are you located? Open Synaptic, Settings -> Repositories, and it will quickly let you change what mirror you use. Try different ones.

---

### Post by bardminz on 2011-04-27
> **Temüjin said:**
> Where are you located? Open Synaptic, Settings -> Repositories, and it will quickly let you change what mirror you use. Try different ones.

I'm in Seattle. I tried several different ones. Same issue. I also tried automatically selecting one but the system failed to find a suitable one.

---

### Post by RJARRRPCGP on 2011-04-27
> **bardminz said:**
> Hi,

I have a very strange problem. The download speed drops dramatically a few seconds after I start apt-get actions (from 100 K/s to 1k B/s). I'm using Comcast with a 100k-200k normal download speed. 

For Comcast, unless you have the rare "economy" service, you should be at least 11 Mbit sustained, on fast mirrors, especially the MIT one. 
(And start off at around 30 Mbit.)

And 1.6 Mbit (200 KB/s) is like the worst DSL!

---

### Post by bardminz on 2011-04-28
> **RJARRRPCGP said:**
> For Comcast, unless you have the rare "economy" service, you should be at least 11 Mbit sustained, on fast mirrors, especially the MIT one. 
(And start off at around 30 Mbit.)

And 1.6 Mbit (200 KB/s) is like the worst DSL!

Surprisingly, the MIT one does work for me this time! I did try several different ones (that I used to work fine with), none of which worked before. Then I stopped trying and started thinking about what's wrong with my connection.

Actually, comcast claimed that my service is  15 Mbps. But 200k/s is kind of normal in my case.

Thanks for all who replied!

---

### Post by Rephiscorth on 2011-05-14
I'm having the same Issue, Im getting like 40-50KBps but it should be over 400KBps.  I tried changing the sources.list   and removing the  'us.'   in the URL.

gonna try changing the mirror.

---

