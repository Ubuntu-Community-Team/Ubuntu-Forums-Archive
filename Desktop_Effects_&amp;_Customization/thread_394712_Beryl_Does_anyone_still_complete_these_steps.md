---
title: "Beryl: Does anyone still complete these steps?"
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by rennen01 on 2007-03-27
I usually do this first:
[https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29.(](https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29.()

Is that step even necessary anymore?

---

### Post by chewearn on 2007-03-27
Can't say if the steps are really necessary.  In my case, I didn't use it when I install beryl.  I have nvidia graphics, and use Envy to install the driver.  Then install beryl and emerald:
```
sudo aptitude install beryl emerald emerald-themes
```
Then add "beryl-manager" in my Sessions start-up.

---

### Post by teryan2006 on 2007-03-27
Depends on your hardware and config. In rennen01's case, he has a nvidia card. Thus he is running AIGLX rather than XGL which you are suggesting. Since AIGLX is already configured and included Edgy, all that is needed is to install the beryl and emerald packages.

---

### Post by chewearn on 2007-03-27
> **teryan2006 said:**
> Depends on your hardware and config. In rennen01's case, he has a nvidia card. Thus he is running AIGLX rather than XGL which you are suggesting. Since AIGLX is already configured and included Edgy, all that is needed is to install the beryl and emerald packages.

Huh? :confused:
Did I suggest rennen01 is running XGL?

---

### Post by rennen01 on 2007-03-27
The reason I am asking is because I have a couple of annoying bugs (for example ALT+Tab no longer works).  I am just wondering if I took the wrong steps to install Beryl.

---

### Post by Xenogis on 2007-03-27
Check if that plugin is turned on in beryl. It is named "Application Window Switcher"

---

### Post by rennen01 on 2007-03-27
It was on, but for some reason "Show window list" was off.  It works now :)

Anyone know why when you open a program it shows up behind other windows?

---

### Post by russellc on 2007-03-27
You can turn off focus stealing prevention in the General Options.

---

### Post by rennen01 on 2007-03-28
> **russellc said:**
> You can turn off focus stealing prevention in the General Options.

Found it.  Thank you very much.

---

### Post by russellc on 2007-03-28
No problem :)

---

