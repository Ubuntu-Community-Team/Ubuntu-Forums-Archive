---
title: "[SOLVED] invisible panels!!"
date: 2008-02-14
forum: Desktop Environments
---

### Post by xlv1000 on 2008-02-14
Yesterday i had my first crah in Linux(I use linux about 2 months and I know allmost nothing).
Everything was paused so I reset my pc.After I loged in my pannels was lost.The only thing I can do is to press Alt+F2 and open aplications from a list.I use Ubuntu 7.10 in dual boot with winXP.
Thanks in advance for your time

---

### Post by jan quark on 2008-02-14
push alt+f2

check the box run in terminal

and type in 

```
metacity --replace
```

---

### Post by xlv1000 on 2008-02-14
> **jan quark said:**
> push alt+f2

check the box run in terminal

and type in 

```
metacity --replace
```

thanks for the replay
I did it but nothing happend

---

### Post by samwyse on 2008-02-14
How about running gnome-panel?

---

### Post by xlv1000 on 2008-02-14
> **samwyse said:**
> How about running gnome-panel?

how can i do that?

---

### Post by samwyse on 2008-02-14
> **xlv1000 said:**
> how can i do that?

Can't you type it in the alt+f2 dialog?

---

### Post by xlv1000 on 2008-02-14
> **samwyse said:**
> Can't you type it in the alt+f2 dialog?

I typed it but nothing happend:(:(

---

### Post by brunolabs on 2008-02-14
I also got that same problem for no apparent reason.

Had to reinstall Ubuntu, I didn't find any other solution. :(

---

### Post by xlv1000 on 2008-02-14
> **brunolabs said:**
> I also got that same problem for no apparent reason.

Had to reinstall Ubuntu, I didn't find any other solution. :(

:(:(:(

---

### Post by xlv1000 on 2008-02-20
Any other ideas????:(:(:(anybody???

---

### Post by hogwartsnigel on 2008-02-20
Hi 
I had a similar problem after configuring nvidia all my panels dissappeared. I tried in vain tapping various function keys etc. Random mouse clicks alerted me on the desktop to a tiny almost pixel sized graphic indicating the panels (there were two migrated just off screen). I was able to drag and configure from there. (All hard linux users are tutting now and saying you could have tried this in the terminal) and I am sure there is a more mature competent way but it worked for 3 of the 4 users on this pc.

Good luck

Nigel

---

### Post by Nikos.Alexandris on 2008-02-20
> **samwyse said:**
> How about running gnome-panel?

Thanks,

this worked for me!

* If Alt+F2 does not activate your a launcher, just try with the mouse... right click & open Terminal.

Cheers,

Nikos

---

### Post by xlv1000 on 2008-02-21
I tried many things but the problem stays....No panels, no right or left clicks,no sortcuts  :(:(:(:(

---

### Post by xlv1000 on 2008-02-23
The problem solved!!!!!!!!!!!!(almost):)First I loged in at failsafe gnome I had panels right-left click but no effects.Then I made a new account and I loged in.Everything was ok.I don't know what is wrong with my first account but who care's:):)

---

### Post by firefeather on 2008-02-23
> **jan quark said:**
> push alt+f2

check the box run in terminal

and type in 

```
metacity --replace
```

I think that this keyboard shortcut requires metacity and gnome-panel to be running correctly in the first place.

---

### Post by xlv1000 on 2008-03-05
I also tryed this:I unistalled all the compiz relative files from synaptic and I installed again.Now I have many efects (wall etc) but not the cube.Another problem is that when I push the quit button(system,quit)
everthing halts exept mouse ponter and I have reset my pc....

---

### Post by abhustler on 2008-03-08
I had the same problem, not entirely sure why it worked but go into compiz manager or advanced desktop effects settings and check "clone output" and your panel should instantly reappear

---

