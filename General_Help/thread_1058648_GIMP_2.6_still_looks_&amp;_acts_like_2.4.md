---
title: "GIMP 2.6 still looks &amp; acts like 2.4"
date: 2009-02-03
forum: General Help
---

### Post by happinesskills on 2009-02-03
I upgraded to Ubuntu Intrepid tonight & so far I'm fairly happy with it.

I've noticed when opening GIMP 2.6.1 that it still opens in 3 different windows & they all appear in the window-switcher-doo-daa. Another thing I've noticed is that it looks & acts the exact same way as 2.4 in Hardy did.

what's up with that

---

### Post by igknighted on 2009-02-03
> **happinesskills said:**
> I upgraded to Ubuntu Intrepid tonight & so far I'm fairly happy with it.

I've noticed when opening GIMP 2.6.1 that it still opens in 3 different windows & they all appear in the window-switcher-doo-daa. Another thing I've noticed is that it looks & acts the exact same way as 2.4 in Hardy did.

what's up with that

Most of the changes were under the hood.

If you turn off compiz the windows will snap into the main GIMP window, but the version of compiz with Ubuntu doesn't support the docking method used by GIMP.  It should in the future however.

---

### Post by happinesskills on 2009-02-03
how?

I don't even know if I have Compiz on. I haven't downloaded it or anything

---

### Post by igknighted on 2009-02-03
> **happinesskills said:**
> how?

I don't even know if I have Compiz on. I haven't downloaded it or anything

It's installed and activated by default in Ubuntu.  I'm not familiar with Gnome, so I'm not entirely sure how to turn it off, but it is somewhere in System->Preferences... perhaps "Desktop Effects" or "Appearance"?

---

### Post by gackt on 2009-02-03
if compiz is the source of the problem than try this:
1. $ sudo apt-get install compiz-switch
2. $ compiz-switch
3. try run gimp to see any different, if nothing change then run step 2 one more time and try to run the gimp again afterward

Still having no luck? maybe you should re-install it
1. system-administration-snyaptic package manager-gimp (mark it for complete removal)
2. sudo apt-get install gimp

hope it work out!

---

### Post by tornadof3 on 2009-02-03
compiz-switch does not appear to be in the synaptic package manager for me? I have all the repositories enabled inc mediubuntu.

I have the same problem with GIMP; Compiz is fully enabled. Because of compiz, a lot of media programs that play AVI files, as well as my webcam program and Google Earth, all flicker terribly whenever desktop effects are enabled - is this part of the same problem?

---

### Post by gackt on 2009-02-03
> **tornadof3 said:**
> compiz-switch does not appear to be in the synaptic package manager for me? I have all the repositories enabled inc mediubuntu.

I have the same problem with GIMP; Compiz is fully enabled. Because of compiz, a lot of media programs that play AVI files, as well as my webcam program and Google Earth, all flicker terribly whenever desktop effects are enabled - is this part of the same problem?

Yes compiz is known to cause some problems on your ubuntu.
compiz can be found in here: [http://forlong.blogage.de/entries/2008/5/1/Compiz-Switch-04-released](http://forlong.blogage.de/entries/2008/5/1/Compiz-Switch-04-released)

---

### Post by danbuter on 2009-02-03
Go into Appearance, then Visual Effects. Set it to None.
Then go into synaptic and delete compiz and it's plug-ins. Your computer will work much better.

---

### Post by exploder on 2009-02-03
> Then go into synaptic and delete compiz and it's plug-ins. Your computer will work much better.

I wouldn't go that far, just turn it off.

---

### Post by gackt on 2009-02-04
> **exploder said:**
> I wouldn't go that far, just turn it off.

yeah, just install the compiz switch ( i provided the link above)

---

### Post by happinesskills on 2009-02-06
Righto, I'll install compiz switch & then try it.

---

### Post by happinesskills on 2009-02-06
I ran 

```
sudo apt-get install compiz-switch
```

Like gackt said, but return with an error saying that Compiz-switch cannot be found.

I tried turning off visual effects & it worked, they all went into 1 window, but without effects, ubuntu looks shitty & unprofessional

---

