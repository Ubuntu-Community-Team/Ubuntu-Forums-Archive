---
title: "clock is off by 6minutes :("
date: 2009-05-22
forum: General Help
---

### Post by jasonmh on 2009-05-22
Is anyone else having a problem with Ubuntu 9.04 syncing the correct time? I live in Portland, OR and have Vancouver, BC time zone selected.  I've also installed NTP.  I can manually sync the time, but this seems ridiculous to me since every time I reboot the clock is back to 6 minutes off.

---

### Post by 73ckn797 on 2009-05-22
Check the clock setting in the computer BIOS.

---

### Post by jasonmh on 2009-05-26
> **73ckn797 said:**
> Check the clock setting in the computer BIOS.

I corrected the time in the BIOS, and now the Ubuntu clock is off by almost an hour :-| I've rechecked the BIOS time, and insured my location is correct for the Ubuntu clock.

Google says the current time is 11:44am and Ubuntu is saying it's 12:25pm.  I guess I should be happy that the date is correct for most of the time.

---

### Post by Girl™ on 2009-05-26
> **jasonmh said:**
> Google says the current time is 11:44am and Ubuntu is saying it's 12:25pm.  I guess I should be happy that the date is correct for most of the time.

Hm.. how about using *ntpdate* to to synchronize with another server?

---

### Post by 73ckn797 on 2009-05-26
> **jasonmh said:**
> I corrected the time in the BIOS, and now the Ubuntu clock is off by almost an hour :-| I've rechecked the BIOS time, and insured my location is correct for the Ubuntu clock.

Google says the current time is 11:44am and Ubuntu is saying it's 12:25pm.  I guess I should be happy that the date is correct for most of the time.


I wish I could give you another solution, sorry.

---

### Post by walkerk on 2009-05-26
Just add the following to your startup script:
```
sudo ntpdate time.nist.gov &
```

You'll need to allow ntpdate to run w/out a password (sudoers)

---

### Post by mkvnmtr on 2009-05-26
I seem to remember on my installs it asked me if I wished to use an internet time server or I wished to do it myself. I choose the internet server and my time is always correct. I did not pay much attention because it was much the same as the last 8 or 10 times I have installed. Maybe you picked the wrong one. I have no idea how to correct it now that you are up and running but there must be a way.

---

### Post by 73ckn797 on 2009-05-26
Maybe? Can't you just right click the time/date in upper panel and adjust the time? If you have tried that I assume it is not staying set?

---

### Post by jasonmh on 2009-05-26
> **walkerk said:**
> Just add the following to your startup script:
```
sudo ntpdate time.nist.gov &
```

There is a ntp script already in there, should I add it to that or make another file?  If I add it to the one that's already there, where should I put it?  I'm not familiar with linux scripting at all.

---

