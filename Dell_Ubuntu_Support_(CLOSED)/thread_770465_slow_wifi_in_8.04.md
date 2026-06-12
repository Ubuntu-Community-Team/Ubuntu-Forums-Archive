---
title: "slow wifi in 8.04"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by funtomas on 2008-04-27
Dear All

I have installed ubuntu 8.04 on my dell inspiron 6400/E1505

everything is working fine but speed of internet connection is only half

my net connection in vista is 1500 kbps download / 256 kbps upload
in ubuntu it is 760/90

3945ABG intel wireless card
and driver is iwl3945

---

### Post by funtomas on 2008-04-28
I forgot, I am using 64 bit version...

---

### Post by neptho on 2008-04-28
Are you positive that you're using iwl and not ipl?  I had this precise problem when an overzealous fixing of my modules, I accidently reinstated ipl.  That was painful!

Open a terminal and run:
```
lsmod | egrep 'iwl|ipl'
```

If you see ipl, blacklist it, and reload iwl.  If you see iwl; hopefully someone else can assist; I'm only running the 32 bit distribution on my system with a 3945.

---

### Post by pormogo on 2008-04-29
I've had spotty wireless issues since moving to 8.04 on my m1330n. Using the old ipw3945 module I actually had decent luck. The signal strength was all over the place but it was more or less workable (sometimes it had to be loaded and unloaded but very rarely). On 7.10 I heard iwl was more stable, but it always seemed to die completely after a suspend on 7.10 so I never used it. 

Now the module seems to work when suspending however I am having issues staying connected to any access points for long durations of time. I'm waiting for the issue to happen again so I can post some log data here. I am actually having a few problems (like backlight brightness) that I have not been able to fix. I will most likely just make a thread with all of my issues together since some of the common forum fixes (like FN+i[/down 3 brightness levels) do not seem to be working for me.

---

### Post by funtomas on 2008-04-29
tomas@tomas-laptop:~$ lsmod | egrep 'iwl|ipl'
iwl3945               104820  0 
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211
led_class               7176  1 iwl3945

---

### Post by NeverM$4Me on 2008-04-29
I'm having a similar slow connection speed / weak signal strength issue with intel 4965agn card in my m1530 on Hardy with iwl4965. I really hate to say this but on vista I'm constantly getting a strong signal with no slow down at all:(

---

### Post by igorgue on 2008-05-22
Same here, I had to use ndiswrapper... but I like iwl3945 because I can suspend with it :(, anybody know how to fix this error? or at least debug it?

---

### Post by sam_delta on 2008-05-22
just curious , have you guys made all updates on hardy>? , ive heard some people get their intel wireless fixed by updating, i  duno if the same model,but its an intel.
just my 2 cents

sam

---

### Post by igorgue on 2008-05-22
Yes, I also installed the backported(linux-backported-modules enabling the backports repo) to get the latest driver, I might want to try with the older driver, but the one released on the CD wasn't working.

---

### Post by imopen on 2008-06-01
> **NeverM$4Me said:**
> I'm having a similar slow connection speed / weak signal strength issue with intel 4965agn card in my m1530 on Hardy with iwl4965. I really hate to say this but on vista I'm constantly getting a strong signal with no slow down at all:(

try ndiswrapper. I go fast as on Windows ;)

---

