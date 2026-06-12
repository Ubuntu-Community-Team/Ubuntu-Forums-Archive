---
title: "Compiz fusion not working..."
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by Raffo on 2007-08-20
Today compiz fusion stopped working and I don't know why... It seems to be a plugin problem... here is what I get if I type "compiz --replace &" in the terminal:

```
/usr/bin/compiz.real (core) - Error: Couldn't load plugin ' '
/usr/bin/compiz.real (core) - Error: Couldn't load plugin ' '
/usr/bin/compiz.real (core) - Error: Couldn't load plugin ' '
```
And so on... can you help me??

---

### Post by KhaaL on 2007-08-20
could you please tell what repository you're using?

---

### Post by Raffo on 2007-08-20
> **KhaaL said:**
> could you please tell what repository you're using?
Of course... treviño's.

---

### Post by KhaaL on 2007-08-20
several people are having problem with his update, try:

cp ~/.compizconfig/Default.ini ~/.config/compiz/compizconfig/

and see if that helps!

---

### Post by Raffo on 2007-08-21
> **KhaaL said:**
> several people are having problem with his update, try:

cp ~/.compizconfig/Default.ini ~/.config/compiz/compizconfig/

and see if that helps!

Unfortunately, it didn't help....

---

### Post by KhaaL on 2007-08-21
> **Raffo said:**
> Unfortunately, it didn't help....

I just did this and it helped me, hopefully it'll help you too... First, fire up a console and type in:

$ sudo apt-get --purge remove compiz*

This will purge all your compiz stuff, so make sure to backup your settings file if you want to keep it.

After that, do 

$ sudo apt-get clean;sudo apt-get autoclean

After that, head over to [http://vorian.org/?p=82](http://vorian.org/?p=82) and follow his guide...

Things should be working well after that. 


Good luck!

---

### Post by Inxsible on 2007-08-21
> **KhaaL said:**
> several people are having problem with his update, try:

I agree. My window borders disappeared suddenly. I uninstalled compiz-fusion and then used amaranth's guide to install it again.
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

