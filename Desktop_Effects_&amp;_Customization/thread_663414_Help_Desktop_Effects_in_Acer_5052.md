---
title: "Help Desktop Effects in Acer 5052"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by b4y03sky on 2008-01-10
Help I can run desktop efeects Ubuntu Gutsy on my laptop

The error message says : The composite extention (not available (or else? I forgot))

The Specs of my laptop :

-Acer 5052
-AMD Turion 64 2.2 GHz
-Graphic Cards  ATI Radeon X1100 

HEEELP!!!

---

### Post by Forlong on 2008-01-10
First make sure you enabled the proprietary fglrx driver via *System &#8594; Administration &#8594; Restricted Drivers Manager*

Then install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by b4y03sky on 2008-01-26
Thanks dude, it's work now !!

Compiz in my laptop

---

