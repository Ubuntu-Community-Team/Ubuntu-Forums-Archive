---
title: "shutdown fails w/sudo shutdown now, hangs - gui shut works"
date: 2009-01-26
forum: General Help
---

### Post by rocket777 on 2009-01-26
I just upgraded to 8.10 and I have a problem.

First, I really miss the quick shutdown from 8.04. Is there a way to re-enable that so I don't need to do 4 or 5 things to shut down.

I also find that the command line version, 

>sudo shutdown now

hangs on the shutdown progress screen and leaves the power on.

Any ideas? I really am just looking for a quick way to shutdown the system, including power.

---

### Post by malfist on 2009-01-26
```
sudo shutdown -hP "now"
```

Is Fast Applet User Switcher loaded?

---

### Post by rocket777 on 2009-01-26
> **malfist said:**
> ```
sudo shutdown -hP "now"
```

Is Fast Applet User Switcher loaded?

Opps, I should have read the manual page :) Thanks.

Do you mean the power button (red in the upper right corner) that gives you the choice of log off or switch user - only those 2? 

I liked the old one that had 6 options, including shutdown, hibernate, etc. which required no confirmations. I have a single user dedicated use system and I don't need all the extra multi user features.

---

