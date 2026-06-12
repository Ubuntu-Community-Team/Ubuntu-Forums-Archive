---
title: "Skype&amp;Flash causing laptop to overheat"
date: 2013-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mentorious on 2013-06-08
Hi,


Last times my laptop  is getting hot :mad:


I've just watched Youtube and called to my friend with cam, then **sensors** command got:


```
damian@damian-Studio-1749:~/Arbeitsfläche$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +87.0°C  (high = +80.0°C, crit = +90.0°C)  ALARM (CRIT)
Core 2:       +86.0°C  (high = +80.0°C, crit = +90.0°C)  ALARM (CRIT)

```

Everything lags and freezes because of critical temperature.


I don't know what I should to do. Here's htop screen: [http://screencloud.net/v/e0bN](http://screencloud.net/v/e0bN) 


My laptop's details: Dell Studio 1749

Intel i3-330M (2.13Ghz),  8GB ram (4x2048) DDR3, Graphics: ATI HD 5000. 

I use Catalyst 13.3 drivers from ATI site.

Thanks for the help in advance :)

---

### Post by vuquyen93 on 2013-06-08
please try install tlp, it can save your energy and reduce your heat
if you use ubuntu 12.04 you can install jupiter

---

