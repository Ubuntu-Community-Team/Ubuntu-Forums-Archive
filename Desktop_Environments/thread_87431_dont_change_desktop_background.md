---
title: "dont change desktop background"
date: 2005-11-08
forum: Desktop Environments
---

### Post by erez1012 on 2005-11-08
in xfce, i choose an image in the desktop setting and its not appear on the backround??

---

### Post by cyrax on 2005-11-08
tryed fbsetbg? or bsetbg or setbg?

---

### Post by erez1012 on 2005-11-08
what is it??

---

### Post by manicka on 2005-11-08
[QUOTE=erez1012]in xfce, i choose an image in the desktop setting and its not appear on the backround??[/QUOTE]

What type of image is it? I have a vague recollection that xfce doesn't support some formats like svg.

---

### Post by erez1012 on 2005-11-08
jpg

---

### Post by erez1012 on 2005-11-08
i do this bus it dont load in the nex time i log on the computer:

Code:
sudo apt-get install feh.
When you install it you should find a file in you home dir (hidden) called .fehbg. if you don't find it then run 
Code:
feh --bg-scale FILE name of bg you want

---

