---
title: "Cannot log out"
date: 2005-11-01
forum: Desktop Environments
---

### Post by ddon on 2005-11-01
Everything seems to be working fine on Breezy; but when I try to log out the log-in screen appears, and the two tiny words in the lower left corner offering  to reboot or shut down flash on, then off again,  all too fast for me to get my mouse over them.  My only recourse is to log in again or reach for the off switch on the computer, which is a poor way to leave.

Is there a delay setting somewhere for the exit screen?

ddon

---

### Post by Ampersand on 2005-11-01
I've not come across that problem before, but as a workaround you could try shutting down from a terminal. 
Open a terminal (or press ctrl, alt and f1 and log in) then use the command 
```
sudo shutdown now
```
or to reboot
```
sudo shutdown -r now
```

---

