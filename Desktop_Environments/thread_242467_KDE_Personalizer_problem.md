---
title: "KDE Personalizer problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by infoseeker on 2006-08-23
Hi
I recently installed a theme (embassy - a good one :)), but ever since doing this the KDE personalizer wizard always pops up when restarting up KDE. This is only supposed to happen when KDE starts up the first time (asks for personal preferences, locale, performance, etc.)
In an attempt to resolve this issue I renamed the .kde directory, but doing this did not resolve the problem. Settings like mouse single/double clicking, etc are lost on PC restart.

Any suggestions ?

---

### Post by Gideon on 2006-08-23
I'm having this problem. About the only useful thing I can say is that if you click to cancel the personaliser, you keep your original settings. 

What it seems to be is that the personaliser is running whether it needs to or not.

---

### Post by aysiu on 2006-08-23
Have you tried this? ```
sudo chown -R infoseeker:infoseeker /home/infoseeker
sudo aptitude remove kpersonalizer
```

---

### Post by Emerzen on 2006-08-23
I had this problem and found the solution on the forums, but don't have the original poster to give due credit, well, here it is:

To stop the initial KDE wizard set to false the following line in /usr/bin/startkde 

kpersonalizerrc General FirstLogin true

---

### Post by infoseeker on 2006-08-24
> **Emerzen said:**
> I had this problem and found the solution on the forums, but don't have the original poster to give due credit, well, here it is:

To stop the initial KDE wizard set to false the following line in /usr/bin/startkde 

kpersonalizerrc General FirstLogin true

Worked like a charm. TYVM

---

