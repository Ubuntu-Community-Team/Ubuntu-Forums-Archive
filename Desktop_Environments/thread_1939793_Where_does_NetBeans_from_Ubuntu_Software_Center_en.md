---
title: "Where does NetBeans from Ubuntu Software Center end up?"
date: 2012-03-12
forum: Desktop Environments
---

### Post by Santillana on 2012-03-12
I would love to be able to continue developing Java within NetBeans even now that I am in the process of switching to Ubuntu. I downloaded NetBeans from Ubuntu Software Center (USC), and everything seemed to go smoothly. I was requested to state my password. USC indicates that installation has occurred and gives me a "Remove" option, so NetBeans is clearly in place. But which place? Can't find it, much less launch it.

And another question that seems to go along with the rest: I know some power users like Synaptic better and I am perfectly ready to go with them on that, it's just that I can't seem to find Synaptic anywhere under Applications. I am using 11.10 with GNOME. 

I would greatly appreciate any help or pointers to the right study material from the many competent Ubuntu people on the forum who have been there and seen that. :)

---

### Post by wojox on 2012-03-12
I don't use netbeans, but you could find it with:
```
sudo find / -name netbeans 2> /dev/null
```

As far a Synaptic you would need to install it:
```
sudo apt-get update; sudo apt-get install synaptic
```

---

### Post by Santillana on 2012-03-12
> **wojox said:**
> I don't use netbeans, but you could find it with:
```
sudo find / -name netbeans 2> /dev/null
```As far a Synaptic you would need to install it:
```
sudo apt-get update; sudo apt-get install synaptic
```

Thank you so much, wojox. :p

Killer skills all over the place here. You're no exception.

---

