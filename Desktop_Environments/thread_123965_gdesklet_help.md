---
title: "gdesklet help"
date: 2006-01-31
forum: Desktop Environments
---

### Post by nami on 2006-01-31
Hi

I'm trying to get a desklet to work which can monitor the temperature of my cpu.

checkout the pic
[[IMG]http://img37.imageshack.us/img37/8425/screenshot7va.th.png[/IMG]](http://img37.imageshack.us/img37/8425/screenshot7va.png) 

How do I get rid of that error?

Thanks
nami

---

### Post by fak3r on 2006-01-31
[QUOTE=nami]
How do I get rid of that error?
[/QUOTE]

Anytime I play around with gdesklets I always get hung up on something like this.  To clear the error you need to delete all of your ~/.gdesklets:

```
rm -rf ~/.gdesklets
```

After that you can rebuild them as you did before, just avoid the one that crashes!  Also, there may be a way to just delete the offending one, but I haven't been patient enough to do that.

---

### Post by nami on 2006-01-31
The ones which crash for me are the ones which need the lm-sensor.  Any idea how to install and configure the lm-sensor?

Thanks
nami

---

### Post by syklitengutt on 2006-01-31
do you have sensor to messure your temp?

---

### Post by nami on 2006-01-31
Yes I have a windows partition and can monitor the temperature of both hard drives, the cpu and the general case temperature.

But don't know how to get them to work in linux ubuntu

---

### Post by nami on 2006-05-21
Is it possible to get the gDesklet to startup each time the computer starts up?

---

### Post by Ramses de Norre on 2006-05-21
system > preferences > session > start up tab
Put in gdesklets with an order of 50.

```
sudo aptitude install lm-sensors
``` installs the package but you might need to set it up.

---

### Post by nami on 2006-05-21
Hi

I just tried the first part and it didn't start automatically?

[[IMG]http://img164.imageshack.us/img164/4659/screenshot5wk.th.png[/IMG]](http://img164.imageshack.us/img164/4659/screenshot5wk.png)

---

### Post by Ramses de Norre on 2006-05-21
It's g**d**esklets, not g**D**esklets ;)

---

### Post by nami on 2006-05-21
That did the trick!  Thanks :)

Now, need to figure out how to get these sensors to work. Any tutorials on how to configure them once installed?

---

