---
title: "xmodmap problems"
date: 2006-10-28
forum: Desktop Environments
---

### Post by Eremit on 2006-10-28
That's the file I use with xmodmap:
```
clear mod1
keysym Alt_R = Mode_switch
add mod1 = Alt_L
clear mod3
add mod3 = Mode_switch

keysym a = a A adiaeresis Adiaeresis
keysym o = o O odiaeresis Odiaeresis
keysym s = s S ssharp section
keysym u = u U udiaeresis Udiaeresis
keysym e = e E currency
```

Worked all the time but now in Edgy it stops working after a few minutes. Then I have to run xmodmap again, but after a few minutes ...

Is there some program or daemon that keeps resetting the keyboard settings?:confused:

---

### Post by Eremit on 2006-10-30
*edit*

the problem solved itself ... Dont' know why, perhaps because I deinstalled scim :)

---

