---
title: "Where did Helios Screensaver go in 9.10?"
date: 2009-11-18
forum: Desktop Environments
---

### Post by JimiOB on 2009-11-18
All

Upgraded to 9.10 and my favorite screensaver (helios) is GONE! 

Where oh where did it go?????

Thanks
Jim

---

### Post by Ugeen on 2009-11-18
Helios is my favorite Screensaver too.

Applications, Accessories, Terminal
```
sudo apt-get install rss-glx
```
From Post: [#5]("http://ubuntuforums.org/showpost.php?p=8231561&postcount=5") in Thread: [Where are all the screen savers in karmic]("http://ubuntuforums.org/showthread.php?t=1311587"). And even though the thread says, "karmic."  It seems to be working for Ubuntu 9.10 too.

You may want to take a look at [cpu-killer/power-eater screen savers]("https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/390308").

---

### Post by LeDmagNeT on 2010-02-13
Yes same here.
Although rss-glx includes the file for helios, it's not available in the list of screensavers when you run something like xscreensaver.
Looks like the package is broken to me.
As for the "Resource Eaters" in the other forums, I think it's up to the user to decide.
Frankly I'm happy to run OpenGL screen savers on my laptop.

Ubuntu please fix the Helios broken screen saver in rss-glx.

---

### Post by Dreamer-of-Days on 2010-02-14
I was looking in synaptic for some screen savers 'cause on the fresh install of 9.10 it doesn't have the "molecule" by default. I did this:

System-> Administration-> Synaptic Package Manager

and then type

xscreensaver-gl-extra

this gets you the extra 3D screen savers

xscreensaver-data-extra 

this one gets you the 2D ones. Might not have to do both, but I did. Adds ALOT (I think 200) of screen savers to your system. Also, in synaptic try just typing in screensavers to see all that comes up. I never found any add-ons for "molecule" but some of them are sweet. I didn't see "helios" in it though. :/ Might be in one of the other packages...

---

### Post by strobe on 2010-02-14
You can also find the helios screensaver in Ubuntu Studio 9.10.  
 
Not to hijack, but, my only problem is that on my PentM 1.5ghz laptop, it is really jerky in gnome.  I have tried it in xfce4 and strangely, it is liquid smooth.  I have to figure out what the problem is in gnome that makes it not work well.  I really like the gui of Ubuntu Studio (I know its a petty thing), but, not if xfce4 runs so much smoother.  Now if I can just get the Studio theme to run in Xfce4....

---

### Post by T.E.N. on 2012-06-02
> **LeDmagNeT said:**
> Yes same here.
Although rss-glx includes the file for helios, it's not available in the list of screensavers when you run something like xscreensaver.
Looks like the package is broken to me.
[...]
Ubuntu please fix the Helios broken screen saver in rss-glx.rss-glx_install needs to be run once (by 12.04 still) in the shell for Helios to show up in xscreensaver-demo, cf. [http://ubuntuforums.org/showthread.php?p=11990996#post11990996](http://ubuntuforums.org/showthread.php?p=11990996#post11990996).
No idea why the installer would keep omitting the final steps described there.

---

