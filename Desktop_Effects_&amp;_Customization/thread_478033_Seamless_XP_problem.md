---
title: "Seamless XP problem"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by DiamondX on 2007-06-18
Im following the picture tutorial at [http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html) and its not working for me. On step 3, when I type```
sudo ifconfig eth0 0.0.0.0 down
sudo ifconfig eth0 0.0.0.0 up
```
my internet never comes back. Any ideas what is wrong? Im pretty good with linux and the terminal, but I know almost nothing about networking.

---

### Post by reclusivemonkey on 2007-06-19
> **DiamondX said:**
> Im following the picture tutorial at [http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html) and its not working for me. On step 3, when I type```
sudo ifconfig eth0 0.0.0.0 down
sudo ifconfig eth0 0.0.0.0 up
```
my internet never comes back. Any ideas what is wrong? Im pretty good with linux and the terminal, but I know almost nothing about networking.

After those, try

```

sudo dhclient

```

---

### Post by DiamondX on 2007-06-21
That worked, now my internet is back, but on the next command I get an error:
```
sudo route add default gw 192.168.1.1 br0
SIOCADDRT: Network is unreachable
```

---

