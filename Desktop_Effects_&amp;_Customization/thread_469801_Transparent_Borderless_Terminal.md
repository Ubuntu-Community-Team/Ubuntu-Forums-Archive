---
title: "Transparent Borderless Terminal"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by Nythain on 2007-06-10
Ok, so im running KDE before anyone decides to give me advice for gnome-terminall here.

With that out of the way, im in the market for a good transparent borderless terminal program to sit on my desktop like in these screenshots here:
[http://www.lynucs.org/index.php?screen_type=1&screen_id=1197321751405b6d278ae7f&m=screen](http://www.lynucs.org/index.php?screen_type=1&screen_id=1197321751405b6d278ae7f&m=screen)
[http://www.lynucs.org/index.php?screen_type=1&screen_id=1809751816408cbe3db51c1&m=screen](http://www.lynucs.org/index.php?screen_type=1&screen_id=1809751816408cbe3db51c1&m=screen)

i know of two popular emulators to accomplish at the moment
eterm
aterm

so my question... any recomendations on one over the other (keep in mind of what i want to accomplish)
if you have a recomendation of one over the other, any help on setting it up to be transparent and borderless

once i get that far i think i can get it to run automatically when i log in, thats the easy part

---

### Post by Nythain on 2007-06-10
oh yeah... forgot to add... can either one of them run skipping the taskbar... like no show up down in my taskbar that its running???

---

### Post by notwen on 2007-06-10
+1 eterm

---

### Post by steveneddy on 2007-06-10
+1 eterm

I did that for a little while. It looks cool, but I think Beryl put a border around it or something. I don't remember why I stopped, but I do agree that it IS a very cool desktop eye candy.

---

### Post by steveneddy on 2007-06-10
Here is an old Dapper (I think) desktop I did with eterm and no window borders.

I don't remember much about it, bit I do remember that you have to tell it where on the screen to launch because it can't be moved. something with the -x -y placement.

---

### Post by Nythain on 2007-06-10
thanks for the responses and suggestions...
still any word on wether or not eterm can run without being down in the taskbar, like is there a skiptaskbar flag i can use???

---

### Post by notwen on 2007-06-10
```
eterm --help
```  maybe? not too sure on my end, use eterm the few times im in a gui on my server box, which is few & far.  =p

---

### Post by Nythain on 2007-06-10
no help there... i did stumble upon wmctrl in a few google searches, yet have no idea how to use it...

my end goal here now that i have eterm installed and have figured out how to make it run transparent and borderless on my desktop is to create a .desktop file in my ~/.kde/autostart directory that will launch eterm the way i want, where i want (both of wich i can do) and WITHOUT it appearing in the taskbar (wich i cant do yet)

---

### Post by Nythain on 2007-06-10
Effing SWEET... found the solution to my problems... why is the world not made aware of kstart.

if anyone is having similar problems to mine, here's your solution:
```

kstart --skiptaskbar Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x52+30+30 --foreground-color=black

```
remembering to change the geometries and foreground(text) color as needed

---

