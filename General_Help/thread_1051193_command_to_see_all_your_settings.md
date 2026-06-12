---
title: "command to see all your settings?"
date: 2009-01-26
forum: General Help
---

### Post by WannabeFantasma on 2009-01-26
Is there a command to see all your settings?

somehow my laptop (HP550) used to have like couple of loadcycles per half hour, and now (for some reason) it stays the same for hours (only see more loadcycles when i restart pc)

i want to know since i want to make a fresh install of ubuntu (with bigger hard drive space)  and it's good to see the HDD stopped loadcycling that much after thinkin i had the HDD killer bug

and somehow it might help other people too? (which have HDD Killer Bug)

---

### Post by snova on 2009-01-26
I'm not entirely sure what you mean, but if you're trying to make sure you copy them over to your new installation, they're stored in hidden folders within your home directory.

(Application wise that is: system settings are generally stored elsewhere.)

---

### Post by cdtech on 2009-01-26
To query S.M.A.R.T. data you need to install smartmontools :
```
sudo apt-get install smartmontools
```
> If smartctl says your drive isn’t healthy anymore (for any reason) your harddrive might start dying soon.
```
sudo smartctl -H /dev/sda
```
> Now check how fast your Load_Cycle_Count is increasing (the last number is your Load_Cycle_Count):
```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

**Retrieved from here:**
[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

---

### Post by WannabeFantasma on 2009-01-27
but what's fast? 

(damn i thought i stopped it (didn't go up when i logged on but now i think it started again)) :(

think it's only when you're on battery?

---

