---
title: "[SOLVED] Ubuntu hangs after login"
date: 2008-08-01
forum: Desktop Environments
---

### Post by Bloesum on 2008-08-01
Since yesterday when I try to login, my screen turns into this beige Ubuntu color just with my mouse cursor. After a few second a white panel appears in the left top corner. Then nothing. When I tried to restart in de recovery mode -> try fix xserver I noticed that 3 packages failed while loading: [FAIL]. I was aible to read one failure: starting the winbind daemon winbind. I have been trying to configure my WLAN settings for the last days, so what went wrong?

Please help, because I am nowhere without a graphical interface.

Bloesum

---

### Post by K2712 on 2008-08-01
Check your /var/log/messages and/or 
```
dmesg | more
```
output and see if you can find any relevant error messages.

---

### Post by Bodhidharmazen on 2008-08-01
> **Bloesum said:**
> Since yesterday when I try to login, my screen turns into this beige Ubuntu color just with my mouse cursor. After a few second a white panel appears in the left top corner. Then nothing. When I tried to restart in de recovery mode -> try fix xserver I noticed that 3 packages failed while loading: [FAIL]. I was aible to read one failure: starting the winbind daemon winbind. I have been trying to configure my WLAN settings for the last days, so what went wrong?

Please help, because I am nowhere without a graphical interface.

Bloesum

EXACTLY my problem: [http://ubuntuforums.org/showthread.php?t=875456](http://ubuntuforums.org/showthread.php?t=875456) btw, nobody in the forum has been able to solve it... yet, in my thread I found an alternative solution! Hope it helps you.

---

### Post by Bloesum on 2008-08-05
I found the solution myself. Something was wrong with /etc/network/interfaces, see [https://answers.launchpad.net/ubuntu/+question/40913](https://answers.launchpad.net/ubuntu/+question/40913)

Cheers,

Bloesum

---

