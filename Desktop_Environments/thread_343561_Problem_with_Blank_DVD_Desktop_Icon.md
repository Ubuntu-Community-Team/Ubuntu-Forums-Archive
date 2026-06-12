---
title: "Problem with Blank DVD Desktop Icon"
date: 2007-01-21
forum: Desktop Environments
---

### Post by lestat on 2007-01-21
HI all,

I am having trouble burning dvd's in ubuntu 6.10. I can burn cds just fine but the dvds that I burn using k3b, the command line or gnomebaker are all corrupt and cannot be read properly.
The problem seems to lie with the icon that gnome loads onto my desktop when I put in a blank dvd. Is there a way to disable that?

I tried removing automounting and autoburning of removable media in System-->Preferences.... but the icon still shows up and seems to be managed by some other gnome process.
If anybody can help me locate what is managing these desktop icons?

THanks

Nitin

---

### Post by blackcrow on 2007-01-21
By default, desktop icons are managed by Nautilus. To turn them off, hit Alt-F2, run **gconf-editor**. Under Applications/Nautilus/Desktop there should be the relevant options.

I can't see why this should cause corruption of DVDs, however...

---

### Post by TransitMan on 2007-01-22
The icons have nothing to do with how a DVD is burned.
Since you can burn CD's fine, i would surmise that the DVD media being used is not beingtaken well by the DVD burner itself. Try some different media to see what happens.
If all else fails, go to [http://www.videohelp.com/dvdmedia](http://www.videohelp.com/dvdmedia) and look at the comments and compatability for the type of DVD media you are using.
Lastly, your DVD burner itself may be failing, even though the CD burning portion still works. The age of the unit itself should be questioned.

I have not burned a coaster using k3b since installing Kubuntu on my Dell system. It has gone through 2 DVD burners with no problems out of either one.

---

### Post by aescnt on 2007-12-12
Hey guys,

I hope you don't mind me hijacking an old thread.

I can burn with my DVD burner (got a "blank dvd-r disc" icon on desktop, but I burned with brasero) -- but when it's done, and I push the cd back in, the icon didn't change (still shows up as "blank dvd-r disc").

I find this a problem since I was expecting it to change to a normal, filled CD, that I can double-click to view up the files in it. But no, Nautilus still thinks its blank and opens the nautilus CD burning dialog.

Btw, I can mount it manually (mount /dev/scd0). Is there a way to fix this?

---

### Post by Lostincyberspace on 2007-12-12
try using K3b to burn and see if that fixes it.

---

