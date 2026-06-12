---
title: "Time and Date problem"
date: 2009-05-30
forum: General Help
---

### Post by pumber on 2009-05-30
I get dual boot OS, one is Ubuntu and the other is WinXP .

However, the time in Ubuntu is correct but not the WinXP. The time is WinXP is 8 hours slower.

How to fix this problem ?
Thank you !

---

### Post by DeMus on 2009-05-30
> **pumber said:**
> I get dual boot OS, one is Ubuntu and the other is WinXP .

However, the time in Ubuntu is correct but not the WinXP. The time is WinXP is 8 hours slower.

How to fix this problem ?
Thank you !

1) Check time in BIOS
2) Check time zone
3) Check time

---

### Post by CatKiller on 2009-05-30
[https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts)

---

### Post by DeMus on 2009-05-30
> **CatKiller said:**
> [https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts)

Sorry Catkiller, the OP wrote:
However, the time in Ubuntu is correct but not the WinXP. The time is WinXP is 8 hours slower.
You posted a website to set the correct time in Ubuntu, which is already correct. What the OP needs is a way in Windows to make it run at the right time, which as we all know will never happen. :p

My advice is still to look at the following items:

1) Check time in BIOS
2) Check time zone
3) Check time 

Especially nr. 2 is important

---

### Post by QIII on 2009-05-30
sudo gedit /etc/default/rcS

Change the line UTC=yes to UTC=no

---

### Post by CatKiller on 2009-05-30
> **DeMus said:**
> Sorry Catkiller, the OP wrote:
However, the time in Ubuntu is correct but not the WinXP. The time is WinXP is 8 hours slower.
You posted a website to set the correct time in Ubuntu, which is already correct. What the OP needs is a way in Windows to make it run at the right time, which as we all know will never happen.

No. What the OP wants is for Windows and Ubuntu to show the **same** time. If he sets the time in Windows so that it's correct then the time in Ubuntu will be wrong (at least until it gets automatically reset by NTP).

This is a widely-understood problem with dual-booting. So much so that recent versions of Ubuntu default to not using UTC for the hardware clock to help dual-booters, even though having the hardware clock set to UTC is more sensible in general.

---

### Post by pumber on 2009-06-11
So, no solution ?

---

### Post by CatKiller on 2009-06-11
> **pumber said:**
> So, no solution ?

Have you turned off UTC?

---

### Post by colau on 2009-06-11
> **pumber said:**
> So, no solution ?
```

sudo gedit /etc/default/rcS

```
UTC=no

---

### Post by pumber on 2009-06-11
Tried, but it doesn't work !

---

### Post by CatKiller on 2009-06-12
> **pumber said:**
> Tried, but it doesn't work !

What happened?

---

### Post by pumber on 2009-06-12
nothing happened. Same as b4 !

---

### Post by CatKiller on 2009-06-12
> **pumber said:**
> nothing happened. Same as b4 !

That's really not letting us help you much, is it?

Was there text in the file already (that is, did you have to change it to UTC=no)? Did you reboot? Have you now set the clock in Windows? Does it stay accurate over reboots? Are your Time Zones in both Windows and Ubuntu accurate? etc... Without details, there's nothing we can do to help you.

---

### Post by pumber on 2009-06-13
after sync with a time server in WinXP, now it works in both OS after setting UTC = NO 
Thank you !

---

