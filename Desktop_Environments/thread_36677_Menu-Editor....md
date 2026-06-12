---
title: "Menu-Editor..."
date: 2005-05-24
forum: Desktop Environments
---

### Post by tommy04 on 2005-05-24
> tommy@Fry:~$ menu-editor
Traceback (most recent call last):
  File "/usr/bin/menu-editor", line 33, in ?
    import gtk
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode

As you can see, I've been getting an error when running GNOME Menu-Editor. I've been having a lot of problems with import in python programs, as, for example, none of my games can find PyGame. Any ideas?

---

### Post by kleeman on 2005-05-24
You may want to google on your error message. I found quite a number of threads with this error message. The first said the error was caused by using packages compiled on other distros???

---

### Post by tommy04 on 2005-05-24
The thing is it was working before so I don't know what the problem is -_-

---

### Post by tommy04 on 2005-05-26
Bump...

are there any problems caused when you have both Python 2.3 and 2.4 installed? I'm still getting errors from when I mixed apache/apache2 modules, so is this like that...?

---

### Post by kleeman on 2005-05-26
Check this Yoper thread:

[http://www.yoper.com/forum2/index.php?showtopic=3804](http://www.yoper.com/forum2/index.php?showtopic=3804)

Sounds like they solved their problems by reinstalling python using synaptic....

---

### Post by tommy04 on 2005-05-26
Reinstalling python didn't help ;_;

I bet it has something to do with the mixing of python 2.3/2.4, but some of my programs require 2.3...

---

### Post by kleeman on 2005-05-26
Well I have both and don't get the same error. I have attached all my python packages for your comaparison. I used 

wajig listnames pyth

to get them

(wajig is cool and in the universe repository)

---

