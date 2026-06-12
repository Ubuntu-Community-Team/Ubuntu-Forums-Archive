---
title: "Indicator Plugin Bugged(?)"
date: 2014-11-01
forum: Desktop Environments
---

### Post by theo5 on 2014-11-01
Hello.

I have some issues with Indicator Plugin (Xubuntu 14.04 - Xubuntu Session).

First of all, when I "Hide" something (right click -> properties -> hidden) I have to restart the computer in order to apply the change. Is that normal or just a bug?

My second problem is that when I press left click -> time & date settings on "Date and Time" nothing happens.

Any ideas?

---

### Post by Bucky Ball on 2014-11-01
First question: Yes, well actually, you just need to restart the panel. Try this in a terminal:

```
xfce4-panel --restart
```

Second question: Can't help as not using the Indicator Plugin clock.

---

### Post by theo5 on 2014-11-01
> **Bucky Ball said:**
> First question: Yes, well actually, you just need to restart the panel.

Second question: Can't help as not using the Indicator Plugin clock.

1) Ok, so I have to log out or restart the panel.

2) I turned on Orange Panel Clock with " %a %x %H: %M: %S " those clock options, so it' s 24H and looks the same with the plugin indicator clock.

Thanks :)

---

### Post by Bucky Ball on 2014-11-01
I set my clock layout to 'Fuzzy'. Personal preference and something different. You can also make it VERY fuzzy! ;)

When you're satisfied your issues are solved on this thread, please follow the second link in my signature. Thanks. ;)

---

### Post by ajgreeny on 2014-11-01
No need to logout to restart the panel; just use the command given by Bucky Ball, or even more the simply, the command ```
xfce4-panel -r
```will also do the same thing.

For the panel clock I personally prefer the date-time plugin, but I think you need to install that as it's not a default applet.  It is much more flexible and configurable than the clock applet.

---

