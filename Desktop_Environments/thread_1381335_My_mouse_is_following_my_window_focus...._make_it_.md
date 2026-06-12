---
title: "My mouse is following my window focus.... make it stop!"
date: 2010-01-14
forum: Desktop Environments
---

### Post by typhen on 2010-01-14
Hi, I have a bizarre trouble that's popped up today in ubuntu in Gnome,

When I switch from one application to another, my mouse moves to the center of that application. It kind of drifts across the screen, takes about one second.

Having no luck googling this because if i search for "mouse follows focus" all i get is results for "focus follows mouse"....

I installed some new packages today -- I can start digging through those if it seems like a good idea -- but hoping there's some simpler option switch i've flicked?

---

### Post by huviduc on 2010-01-16
I had the same issue with my laptop, i disabled mouse polling in compiz and the issue was resolved. I have no real need to use mouse polling so i left it disabled and never looked into it past that though

---

### Post by pritamps on 2010-01-16
If you don't have CCSM installed, install it using 

```
sudo apt-get install compizconfig-settings-manager
```

Then run it from a terminal using 

```
ccsm
```

There, go to

```
General Options -> Focus and Raise Behavior
```

and ensure that both "Click to Focus" and "Raise on Click" are checked and "Auto-Raise" is unchecked.

---

