---
title: "Disabling volume hotkeys in KDE"
date: 2007-08-27
forum: Desktop Environments
---

### Post by Epeli on 2007-08-27
I've got M-Audio Revoltion 7.1 soundcard ja Microsoft Comfort Curve 2000 keyboard. The volumes keys are working  fine, but they icreases volume by 10%  on one click and even  at 30% volume my headphones are blowing my head off. So I want to decrease that. 

I could do the same thing with xbindkeys and with these commands
```
$ amixer -q sset PCM 3+
$ amixer -q sset PCM 3-
```

But! I can't get it working because I haven't found a way how to  disable original hotkey in KDE (kubuntu). Any ideas?

I used this solution in dapper or breezy when there were no support for my keyboard. Now i'm obviously using Kubuntu Feisty.

---

### Post by francf on 2007-08-27
Just disable the Kmilo service in Kcontrol

---

### Post by Epeli on 2007-08-28
> **francf said:**
> Just disable the Kmilo service in Kcontrol
Kmilo? There is no such thing. I think Kmilo is only for laptop hotkeys.

---

### Post by Epeli on 2007-12-12
up

---

