---
title: "conky 1.9.0-4  ${nvidia gpufreq}"
date: 2015-03-22
forum: Desktop Environments
---

### Post by cosy2 on 2015-03-22
is there any alternative command to 

```
${nvidia gpufreq}
```

because conky show the text > ${nvidia}nothing else

---

### Post by Frogs Hair on 2015-03-23
You could try following syntax as displayed at the link. 

```
${nvidia memfreq} Mhz
```

[http://askubuntu.com/questions/147283/nvidia-plugin-for-conky](http://askubuntu.com/questions/147283/nvidia-plugin-for-conky)

---

### Post by CantankRus on 2015-03-23
Not sure how you installed conky but in Ubuntu 14.04, if you search for and install "conky" through the software centre or via terminal 
you will actually get the conky-std package which is compiled with a limited set of options. The "conky" package is a dummy transitional package.
conky-std is not compiled with **nvidia** features.

You need the "conky-all" package which is compiled with all options.
Just install **conky-all** and it will replace **conky-std**.
```
sudo apt-get install conky-all
```

nvidia should now show, in the compiled features.
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **conky -v**
Conky 1.9.0 compiled Wed Feb 19 18:44:57 UTC 2014 for Linux 3.2.0-37-generic (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  [COLOR="#FF0000"]*** nvidia**[/COLOR]
  * eve-online
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```

---

### Post by cosy2 on 2015-03-24
conky-all do not show in my synaptic

---

### Post by CantankRus on 2015-03-24
Have you enabled the universe repository?
Terminal....
```
software-properties-gtk
```
[ATTACH=CONFIG]260872[/ATTACH]
Close.

Then...
```
sudo apt-get update
```
and...
```
sudo apt-get install conky-all
```

example lines for conky...
```
${color}GPU Temp: ${color green}${nvidia temp} °C
${color}GPU Freq: ${color green}${nvidia gpufreq} Mhz${color}
```
[ATTACH=CONFIG]260873[/ATTACH]

---

### Post by cosy2 on 2015-03-24
yes it is but i use 14.10
> Package conky-all is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  conky-std:i386 conky-cli:i386 conky-std conky-cli

E: Package 'conky-all' has no installation candidate


---

### Post by echotech2 on 2015-03-24
FWIW, conky-all doesn't appear using Synaptic either in 14.10.  Yes, Universe is enabled.

---

### Post by CantankRus on 2015-03-24
Odd...you seem to be right.
I just did a package search for Utopic and there doesn't appear to be a conky-all package.
[http://packages.ubuntu.com/search?keywords=conky&searchon=names&suite=utopic&section=all](http://packages.ubuntu.com/search?keywords=conky&searchon=names&suite=utopic&section=all)
There is a conky-all package in Vivid though.

Try this ppa for Vincent Cheng.
I have used this ppa before for conky.
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
sudo apt-get install conky-all
```

Once installed run ```
conky -v
``` to check it has been compiled with the nvidia option.

---

