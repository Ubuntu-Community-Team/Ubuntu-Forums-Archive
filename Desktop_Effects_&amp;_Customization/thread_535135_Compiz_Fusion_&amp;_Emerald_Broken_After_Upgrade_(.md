---
title: "Compiz Fusion &amp; Emerald Broken After Upgrade (Terminal ouputs attached)"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by shafin on 2007-08-26
I upgraded to the 0.5.2 version using trevino's repo last night,and my whole compiz is broken now!

I'm on 64 bit feisty,with Intel GMA 950 Graphics.Everything was running fine,until I decided,It's time for an update.

The errors generated in the console are


For CCSM
```
:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /var/lib/python-support/python2.5/compizconfig.so: undefined symbol: ccsStringToEdges

```For Compiz Fusion

```
:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /var/lib/python-support/python2.5/compizconfig.so: undefined symbol: ccsStringToEdges

```For Emerald:
```
emerald --replace

(emerald:8216): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8216): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8216): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8216): Wnck-WARNING **: Unhandled action type (nil)


```Please show me a way out of this,at least tell me how I can downgrade to my previous system.

---

### Post by hyperair on 2007-08-26
Trevino's repository? 0.5.2?! Trevino's has 0.5.5. Go upgrade again:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by shafin on 2007-08-26
you sure there are 0.5.5 versions for 64 bit?I cant find it there.

---

### Post by crush304 on 2007-08-26
same problem, x64, no working fusion and only 5.2 avaliable

---

### Post by hyperair on 2007-08-26
Oh damn. I didn't notice you were using x64. Looks like you'll have to compile yourself. =(

---

### Post by crush304 on 2007-08-27
switched from gconf backend to flat file backend and that fixed my problem

---

### Post by shafin on 2007-08-29
Problem Solved :)

Uninstalled everything related to compiz and installed again.

I love the new key-binding interface.

---

### Post by michael37 on 2007-08-29
> **shafin said:**
> Problem Solved :)

Uninstalled everything related to compiz and installed again.

I love the new key-binding interface.

+1

Followed this example and everything works.    I am running 0.5.5 on x64 -- Trevino just added them

Also, gconf is not working for me either.  Works fine with flat file.

---

