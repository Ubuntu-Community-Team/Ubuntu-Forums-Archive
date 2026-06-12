---
title: "[SOLVED] Fed up with compiz xgl, How to uninstall compiz xgl in a clean way on gutsy?"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by alexandreracine on 2007-11-22
Hi people,

The big question : I can't find a clean way to uninstall compiz/xgl on gutsy. Can someone help me on this?

By clean, I mean EASY :) Like sudo apt-get remove xgl (don't try that, it does not work)

The whys :

I did use compiz/beryl back on Ubuntu 6.10! I was actually very glad that the update to Ubuntu 7.04 actually removed that because I did not want to play around anymore and get stuck with only  a text console in the process. I only had one machine after all. But now, with 7.10, xgl compiz is back that you want it or not. Yeah, you can remove the effects, but xgl and compiz are still there in memory and slowing down the system.

Weirdly, I want to uninstall xgl/compiz for the same reasons that a year ago. It seems that the software did not really evolved.

• Everything is *very* slower on an old machine (GeForce3, P4 2.6Ghz, 2GB ram) mostly anything multimedia, and apps are blacking out from time to time.
• Save-to windows not keeping the size I want.
• Keyboard jam some keys. Like , alt+F4 will close a lot of windows, right arrow will scrool 20 pictures, ALT+T will open 40 tabs in FF

Eventually this machine will become a server for hard drive storage, or anything that does not require video, but for now, I need it to be fast on the screen.

File attached long description : You can see here that the eog program (the default image viewer in gnome) is blackout. In the system monitor you can see that the system load is 7.29; 4,47 and 2.22. This is only by looking at some pictures and happens all the time. xgl use 214MB of RAM there, but at boot it is less then 100MB. It seems like we cache stuff around and that surely slow it down.


Thanks.

---

### Post by dyous87 on 2007-11-23
why don't you just go to System>Preferences>Appearance

the go to the Visual Effects tab and turn off desktop effects?

That would completely shut compiz off. There really isn't any reason to uninstall it to deactivate it.

David

---

### Post by alexandreracine on 2007-11-23
That's great, but it is not compiz who is using cpu and memory (15MB max RAM all the time), it is XGL. In this screen shot, I have disable all effects, and the only things I am doing here is playing with kontact. If you look at the monitor, XGL is using 92% of cpu.

So my question is still : The big question : I can't find a clean way to uninstall compiz/xgl on gutsy. Can someone help me on this?


Thanks.

---

### Post by alexandreracine on 2007-11-23
Actually, it's even slower for some operations (like browsing the internet) when effects are off!


So my question is still : The big question : I can't find a clean way to uninstall compiz/xgl on gutsy. Can someone help me on this?

---

### Post by Quash on 2007-11-23
In the synaptics package manager, find all those compiz things, like compiz manager and such.  Thats how I removed mine.  I cant remember all the names.  Sorry, its been a while

---

### Post by Forlong on 2007-11-24
Either remove Xgl:
```
sudo apt-get remove xserver-xgl
```
or disable it for your current session:
```
mkdir ~/.config/xserver-xgl && touch ~/.config/xserver-xgl/disable
```


P.S. I wouldn't recommend removing Compiz.

---

### Post by alexandreracine on 2007-11-25
Thanks Forlong! Now my machine is fast again! :) (for what I need)


Is there a way to disable it the same way but system wide instead of only for one user?

Thanks.

---

### Post by Forlong on 2007-11-25
If you remove Xgl completely (see above), you don't have to disable it for every user.

---

### Post by alexandreracine on 2007-11-27
Thanks, this is what I needed :)

---

### Post by toomax on 2008-04-08
> **Forlong said:**
> Either remove Xgl:
```
sudo apt-get remove xserver-xgl
```
or disable it for your current session:
```
mkdir ~/.config/xserver-xgl && touch ~/.config/xserver-xgl/disable
```


P.S. I wouldn't recommend removing Compiz.

Great job man!
Same problem, your solution perfectly solved it!

Thanks Forlong

---

