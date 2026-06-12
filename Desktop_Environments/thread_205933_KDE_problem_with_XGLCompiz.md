---
title: "KDE problem with XGL/Compiz"
date: 2006-06-29
forum: Desktop Environments
---

### Post by emil.s on 2006-06-29
[http://img234.imageshack.us/img234/3489/xglkrngel7oc.jpg](http://img234.imageshack.us/img234/3489/xglkrngel7oc.jpg)
[http://img61.imageshack.us/img61/7184/xglkrngel12bg.jpg](http://img61.imageshack.us/img61/7184/xglkrngel12bg.jpg)

As you see, is all superkaramba themes dark, as a inactive window.
And the lower toolbar works as a window. (I can select it with ALT + Tab)

And the AltGr key, and the super key is not working.

---

### Post by emil.s on 2006-07-02
Please!

I tried to set keyboard layout with xmodmap, but then no XGL things works.

But in KDEs systemsettings i change keboard layout with the kommand "setxkbmap -model pc105 -layout se".
But:
```
Megaleif ~ # setxkbmap -model pc105 -layout se
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmenteringsfel
```
Xorg.conf:
```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection
```
Any idea?

---

### Post by terrax on 2006-09-15
Hey.....
Got the same problem.

```

terrax@terrax-desktop:~$ setxkbmap -layout 'dk,us' -model pc105
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Lagersegmentfejl

```


Just coming from Denmark instead of Sweden :-)

---

### Post by emil.s on 2006-09-16
Ok. My problem is solved. It worked after a upgrade to Edgy. :)

---

### Post by -DarkMind- on 2006-09-17
same problem here with spanisk (ubuntu dapper)


```
darkmind@darkmind-desktop:~$ setxkbmap -model pc105 -layout es
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Fallo de segmentación

```

---

