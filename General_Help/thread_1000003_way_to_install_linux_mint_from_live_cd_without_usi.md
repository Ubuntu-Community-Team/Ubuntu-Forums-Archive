---
title: "way to install linux mint from live cd without using live desktop?"
date: 2008-12-02
forum: General Help
---

### Post by jeromey on 2008-12-02
so i have this dilemma


i have a computer that has i think 512 mb ram

it has been running ubuntu 7.10 up untill today  (i decided it was time for an upgrade)


so i thought i would go with linux mint 5 this time since its based on ubuntu 8.04 and mostly everything is the same but looks better


the problem is that ubuntu 8.04 comes with compiz enabled by defualt if you have a compatible graphics chip 

my computer has a compatible graphics chip, but unfortunatly i dont have enough resources to run compiz from the live cd

so if i try to load up the live cd the computer works so hard but it takes like 20 minutes to load up the desktop then if i click something everything gets messed up and it takes like 5 minutes just to open the menu


so what i did was logout and log back in with GNOME failsafe (that way compiz would not be running)


this helped alot but it is still very laggy while using the live cd


so i startted the install anyway 
(i figured when it finishes i can just log in to my install with gnome failsafe and turn off desktop effects for good)


the problem is that i left the computer for a few minutes and the screen saver kicked on


now it wont go away, its been just a blank screen for like 10 minutes  and i cant tell if the install is finished or not  (it was at like 65% last time i saw)


so clearly the live cd is not going to work for me

i tried looking for an alternative install cd but i cant find one

does anybody have any ideas?

---

### Post by cariboo on 2008-12-02
It sounds more like you don't have enough ram to run the LiveCD. Linux Mint needs 512Mb ram to install, but will run fine on 256Mb ram. I would suggest you check how much ram you have, by opening a terminal and typing:

```
free -m
```

The result will look something like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1078        930          0         53        554
-/+ buffers/cache:        470       1538
Swap:         5530          0       5530
```

I've got 2Gb ram, so your results will differ.

Jim

---

### Post by jeromey on 2008-12-02
ok i finally ran the command

it turns out that the computer only has 256 mb ram (although i could have sworn it had more)


anyway i ended up installing linux mint with xfce because i figured it would run faster then gnome anyway

but now i fear that i have really screwed thing up

with ubuntu 7.10 the computer ran perfectly, it was a little bit laggy sometimes but nothing serious

now with mint 5 xfce (which should in theory be like xubuntu 8.04)  it is so bad

if i open firefox it takes like 5 minutes for the window to even come up


what the hell is making this so slow?

why is there that much of a difference between 7.10 and 8.04?

if i reinstall ubuntu 7.10 how long will it continue to be supported?


this really sucks, its like going from gnome desktop that runs smoothly to plain old xfce and it runs like crap

what is going on here?

EDIT:  does mint with xfce come with compiz enabled by defualt?

---

### Post by marshag63 on 2008-12-02
Try re-installing, but when the partitoner starts, click on manual and make an 800 MB swap partition.   I just installed Mint 5 (Gnome) on a Dell Latitude with 256 MB and its doable.  If you choose the xfce edition, that should be better.

Hope this helps!

MarshaG.

---

