---
title: "No indication that program is loading"
date: 2012-06-27
forum: Desktop Environments
---

### Post by anaconda on 2012-06-27
When I start firefox starting it takes about 9 seconds!!! 
During that time I have no indication that the program is loading. So sometimes I click firefox icon again, and I end up with 2 (or more) instances of firefox.

In gnome there used to be SOME indication that a program is loading. It appeared on the panel, and mouse pointer started spinning (or something)

Is there any way of getting that same behaviour to xubuntu?

I am very happy with xubuntu, and this is the last unsolved thing that still annoys me 

I have tried googling for a solution, but I can't seem to find any good search words that would describe the problem, so google cant help me.What would be a good search word for this problem?

Another solution to the problem could be preloading firefox  gedit and thunar to the RAM, and keeping them there. So they would start quickly. Is there any way to do that?

---

### Post by LewisTM on 2012-06-27
Edit your launcher or menu item and check "Use Startup Notification". Your cursor will turn into an hourglass when launching that app.

For preloading I recommend you install the **preload** daemon. It will learn from you computer usage and load commonly used libraries in memory for fast startup. It shouldn't otherwise significantly affect performance.

Cheers!

---

### Post by anaconda on 2012-06-27
> **LewisTM said:**
> Edit your launcher or menu item and check "Use Startup Notification". Your cursor will turn into an hourglass when launching that app.
For preloading I recommend you install the **preload** daemon. 

Hmm.. 
I already had the "use Startup Notification" selected (automatically), but it doesn't work. Also tried unselecting it, but it changed nothing, so I reselected it.
Also tried changing mousepointer theme, but it did not help.

Does it work on your machine? 
I have 3 machines with xubuntu 12.04 and Startup Notification doesn't work on ANY of them. They are: Asus eeepc 1005p, Asus eeeBox, and HP dv2000...

I installed the preload program. Sounds promising. Thanks.

And now that I know it is called "startup notification" I can also google it. Thanks. Found one bug report for it already, but no solution yet.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/960191](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/960191)

---

### Post by LewisTM on 2012-06-27
The startup notification doesn't work on all of my computers. It seems to work only on the ones that went through a fresh Xubuntu install as opposed to converted using the xubuntu-desktop metapackage. 

The same is true for changing cursor themes. The Xfce settings manager only correctly applies the theme on those "genuine" machines.

I'm thinking of doing a fresh install, maybe for 12.10, to see if that changes anything.

---

### Post by anaconda on 2012-06-27
All 3 of my machines are new installs and they are installed from xubuntu CD.

Now I am thinking of writing a small program, that would display "Loading" for a few seconds and then disappear. I could make all the most used launchers to launch that and the real program at the same time..

Awful hack, but then I would atleast know if a program is loading, or did I just fail to click the launcher..  (Annoying)

Thanks for the help.

---

