---
title: "Stuck with 3d games"
date: 2007-01-19
forum: Gaming &amp; Leisure
---

### Post by cmacis on 2007-01-19
After messing with settings that led to me rending the computer unusable several times I am admitting defeat and have registered to ask for help. ](*,) 

I have gone through some of the walkthroughs for setting up 3d settings, but I am stumped since I don't know what graphics card my laptop uses. I'm using the fujitsu-siemens l7320gw 
[http://www.fujitsu-siemens.co.uk/home/products/notebooks/amilo_l_7320g.html]("http://www.fujitsu-siemens.co.uk/home/products/notebooks/amilo_l_7320g.html")
[http://www.fujitsu-siemens.co.uk/Resources/72/1031346079.pdf]("http://www.fujitsu-siemens.co.uk/Resources/72/1031346079.pdf")

second url is the data sheet for the laptop, I'm reasonably hardware illiterate, but I know more on my software.

As per one of the tutorials I ran glxgears and got this console output:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).

Anyway, I'm tired right now so I'll leave you with that and if you know which questions to ask or if that's enough info (oh I'm running dapper and installed most of the software on automatix), please reply and put me out of my misery.

---

### Post by RomeReactor on 2007-01-24
According to the pdf: 

```
Integrated UniChrome Pro graphics up to 64MB shared memory

```

Anyway, write on a terminal:

```
lspci | grep VGA
```

That should list your card also. Then look for drivers in Synaptic.

---

### Post by dmn_clown on 2007-01-24
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

---

