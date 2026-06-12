---
title: "[SOLVED] Oops, there goes my time."
date: 2008-12-10
forum: General Help
---

### Post by mathfreak123 on 2008-12-10
Hi, Linux beginner here.

I want to know how to get my system time to automatically update. I accidentally changed the time to be behind by about 20 seconds than what it's supposed to be, and I need it to be very accurate for what I use it for.

---

### Post by ibutho on 2008-12-10
To update the time, you can use ntpd and ntpdate. For one off updates to your clock, you can do something like
```
sudo ntpdate ntp.somehost.com
```
To keep the clock regularly in sync with a time server, you may wish to run the ntpd service. More information on how to do this is available [here]("https://help.ubuntu.com/community/UbuntuTime").

---

### Post by mathfreak123 on 2008-12-10
Ah, ok. Thanks a lot!

My problem has been resolved. :D

---

