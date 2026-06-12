---
title: "Serious Graphics Card Issues"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by wilson47 on 2008-02-03
I was having trouble with my Desktop effects, and someone suggested checking what graphics drivers I was using. I saw that the ones that were running did not match my installed drivers, so I switched the settings, rebooted, and now I can't even try to reinstall because my computer stops booting at 


*running local boot scripts (/etc/rc.local)


I can still use command line, but I don't know how to revert to the old graphics driver settings... I found ways to fix the other issue, but I need to see my GUI to do that first.

Thanks for your help!

---

### Post by wilson47 on 2008-02-03
I just ran ```
startx
``` and I received 
```
Fatal server error: 
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

```

I hope this helps..

---

### Post by wilson47 on 2008-02-03
Well, luckily I have a friend that can search forums better then I can.
I ran 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and I'm good to go.

---

### Post by erfahren on 2008-02-03
you can try reconfiguring X - from the command line enter:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
and go through the steps - if it doesn't work try it without the "-phigh" option. More info on it [here](http://users.bigpond.net.au/hermanzone/p7.html) and [here](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

EDIT - glad you got it fixed. I'll leave my post - the links might be helpful to someone

---

### Post by wilson47 on 2008-02-03
Thank you very much for your post! I was really freaking out about this

---

