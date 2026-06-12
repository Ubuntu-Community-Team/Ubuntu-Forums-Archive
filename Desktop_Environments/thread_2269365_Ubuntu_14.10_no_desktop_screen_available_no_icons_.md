---
title: "Ubuntu 14.10 no desktop screen available no icons and minimize buttons as well."
date: 2015-03-15
forum: Desktop Environments
---

### Post by vishal_ on 2015-03-15
I was playing around with ubuntu. Due to overflow of memory everything disappeared. Later cleared memory and logged in just to see the top bar and side bar and minimize close buttons vanished.. I followed some online suggestion and typed in "sudo lightdm stop" just to see even the firefox and everything except the terminal vanish. "Sudo lightdm start" isnt bringing back things. And for everything it says error:cannot open display
I have somehow got this terminal running.. Need some help.
I tried unity --reset
It says error: the reset option is now deprecated

---

### Post by grahammechanical on 2015-03-15
Things change over time. Two useful commands to make a note of are

```
dconf reset -f /org/compiz/
```

to reset compiz and to restart Unity

```
setsid unity
```

then there is 

```
 unity --reset-icons
```

Regards.

---

