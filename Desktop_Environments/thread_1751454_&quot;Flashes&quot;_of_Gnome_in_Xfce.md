---
title: "&quot;Flashes&quot; of Gnome in Xfce"
date: 2011-05-06
forum: Desktop Environments
---

### Post by Buntero on 2011-05-06
Hello

I recently installed Xubuntu from Ubuntu 10.04 using "sudo aptitude update && sudo aptitude install xubuntu-desktop" to allow using Gnome or Xfce with Ubuntu.

The problem I have encountered is that I get brief "flashes" of Gnome, that is the desktop background and desktop items switch to Gnome, while using Xfce, apparently for no reason. Generally it changes back after a second or so, although one time Gnome got "stuck".

I suppose uninstalling Gnome would solve the problem, but I haven't tried this because I would like to have both desktop environments installed.

Performance has been acceptable, about the same as when I was using Gnome, but I suspect Gnome is running in the background and therefore I could improve performance if I removed the problem.

Anyone have a clue?

Thanks.

---

### Post by jerrrys on 2011-05-10
interesting; i too have just changed to xubuntu and find things faster on my box.  as to adding x to ubuntu, i dont know.  i did add kde to ubuntu and turned out not to be a good idea.  too much extra crap happening...

install it by itself if ya got the room.  works best....

---

### Post by edgue on 2011-05-10
> **Buntero said:**
> Hello

The problem I have encountered is that I get brief "flashes" of Gnome, 

You might check if "nautilus" is still running for some reason.
One way to be sure ... open a console and try 

"nautilus -q" 

or was it -quit ... but that did help me sometimes.

Did help me when I started using xubuntu on top of ubuntu.

(I turned to a pure xubuntu install afterwards; adding the few gnomish things I need seems to be the better way for me)

---

### Post by jerrrys on 2011-05-10
don't think its nautilus.  i have nautilus installed on x.

---

### Post by edgue on 2011-05-10
> **jerrrys said:**
> don't think its nautilus.  i have nautilus installed on x.

Sorry, not sure if you got me right: you have to make sure that nautilus is NOT running.

I had exactly the thing you described; and every time I forced nautilus to stop ... the gnome flashes stopped.

---

### Post by jerrrys on 2011-05-10
ok, now im hearing you **edgue**. give it a try **buntero**. but i still think the best way to go is a independent  install

---

### Post by ManualSparrow on 2011-05-10
It's Nautilus taking over your desktop - I had this problem with some docks, and eventually fixed it but can't remember how precisely. Google tells me you can diable Nautilus' drawing to the desktop in the command line like this: 

gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false 

but I believe there is a GUI-based way as well.

---

### Post by Buntero on 2011-05-10
Hi

I tried "nautilus -q". This stops three processes from running, but doesn't solve the problem. In fact, some times running that command several times actually caused a flash and after a few more times I got stuck in gnome.

Just now I used "gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false", and I'll wait to see if it gets any results. Since the problem is infrequent and unpredictable I'll get back to you guys in a couple of weeks or so.

Thanks.

---

### Post by ufugu on 2011-05-17
Any updates?

In case that didn't work, [this worked]("http://cmpstuff.blogspot.com/2009/09/securing-xfces-control-over-desktop.html") for me.

---

### Post by hhh on 2011-05-17
The problem is that the nautilus process will automatically restart even if you kill it, unless you...
Go to Xfce Settings Manager>>Session and Startup>>Session. Double click the "Restart Style" field for nautilus and set it to "Never". Now kill nautilus and log out of Xfce, making sure to check the box in the logout window for "Save session for future logins".

---

### Post by Buntero on 2011-05-17
ufugu: using gconf-editor is actually the GUI-based method ManualSparrow was talking about.

While I had no more problems this week, just in case I still implemented hhh's solution to kill nautilus definitely.

---

