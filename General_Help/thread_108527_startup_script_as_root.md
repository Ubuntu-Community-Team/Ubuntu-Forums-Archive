---
title: "startup script as root?"
date: 2005-12-26
forum: General Help
---

### Post by bonsiware on 2005-12-26
Because of my heat problems i've followed this thread to undervolt my Pentium-M

[http://ubuntuforums.org/showthread.php?t=97043]("http://ubuntuforums.org/showthread.php?t=97043")

It worked fine!

But I need to execute the following commands everytime my system bootup:

```

sudo -s
echo "1212,1212,1212,1212,1212,1116,1052,988,924,860" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table

```

is it possible to set it on startup?
is it possible without typeing my password every time?

thank you all

---

