---
title: "how to finetune syndaemon parameters?"
date: 2010-05-22
forum: Desktop Environments
---

### Post by akos.maroy on 2010-05-22
when one select System -> Preferences -> Mouse Preferences -> Touchpad -> Enable mouse clicks with touchpad, this results in sydaemon being started with the following parameters:

```
syndaemon -i 0.5 -k
```

while this is fine, for me  the half second threshold seems to be too short, and I experience the cursor being moved by the touchpad while typing.

I wonder how can one adjust these parameters in a nice way?

if course, I could disable the above checkbox, and just add syndeamon to into startup programs with my desired parameters. but still, is there a 'nice', UI friendly way of doing this?

---

### Post by Macchi on 2010-05-24
I have the same problem, and believe that the touchpad delay parameter on syndaemon should be extended or customizable. "Man syndaemon" gives a default of 2 seconds, which would be OK. Personally I prefer 1.7 seconds, but the present value is fixed at 0.5.

Unfortunately, I could not find information on where to adjust it, and apparently parts of the documentation around X, HAL GSynaptics etc are deprecated. I am also looking for a solution that can be applied by the average user without recurring to a command line interface.Obvoiusly it is easy to patch anything on the terminal, but the real challenge is to solve the problem for most users of the distro!

Where can we change the syndaemon parameter value? 
Is it a scrip or it is hardcoded?  If it is in a script it would be easy to change.

---

### Post by Macchi on 2010-05-24
I've just found that the delay length is HARDCODED on gnome-settings-daemon. I wonder how these programmers/developers/hackers (ever) reason on the customization of settings. See: [http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c#n517](http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c#n517)

OUR ALTERNATIVES

1) A workaround is NOT to activate the "disable touchpad while typing" and add the call to "syndaemon -d -i 2" on the startup applications.

2) A temporary solution for several users would be to submit a patch to extend the delay to something closer to 2 seconds, the former default on synaptics. 

3) A more definitive, flexible, and customizable solution would be to add a gconf key with the value. such as: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/409086](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/409086) 

(On this moment I do not have time to get into the source code to solve this issue, but I hope that someone else can do it. We can at least add comments and insist on the bug/suggestion on launchpad. This is not a large issue but anyone with a laptop or netbook certainly has experienced the need for disabling the touchpad while typing. This is a common support question.)

---

### Post by akos.maroy on 2010-05-24
Macchi,

Thanks for the investigation. Yeah, figured the first workaround myself. And it's also beyond me why this delay is hardcoded in the gnome source code.

is there a gnome bugtracker / request tracker, where one could raise this issue?


Akos

---

### Post by Macchi on 2010-05-27
Hello Akos.Maroy,

One example is at:
 [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/409086](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/409086)

and the awful hard-coded user parameter can be seen on the source code at:
[http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498](http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498)

PS: Unfortunately I will not have time to dig into this issue in the following weeks because I have some projects of high priority that need most of my attention. Since I am an independent consultant sometimes basic survival is at stake upon delayed deliveries...

---

### Post by heluani on 2010-08-22
I was searching on the same problem and stumbled upon this thread. Since I couldn't find any acceptable solution I wrote these small patches. The first one is to patch gnome-settings-daemon so that it recognizes another gconf float to control the delay between 0 and 4 seconds. The second patch is to gnome-control-center where the gnome-mouse-properties applet is, so that it shows a slider to control the delay in gconf.

It is not a beauty of code, but it is what I could do in an afternoon, and considering that the last time I wrote something was under MS DOS on an XT 8088 well... it does the trick at least.

It was only tested on 2.28.1 and I did not care to even check if it patches on other versions.

The patch to gnome-settings-daemon: [ATTACH]167239[/ATTACH]

The patch to gnome-control-center: [ATTACH]167238[/ATTACH]

Hope this helps, R.

---

### Post by pcm_man on 2010-12-04
@Macchi

1) A workaround is NOT to activate the "disable touchpad while typing" and add the call to "syndaemon -d -i 2" on the startup applications.

This works and it works very very well!   I have spent hours and hours working on different solutions to this BIG issue.  It would drive me crazy while working on typing with my Dell Notebook and having the touchpad interfere with my typing. What I had failed to realize was that the setups under the System--> Preferences---> settings where interfering with my attempts to make this work at LOGIN for individual users.

THIS JUST WORKS!  IT IS SIMPLE AND IT IS ADJUSTABLE AS TO THE DELAY YOU WANT BETWEEN THE LAST TOUCH OF A KEY AND WHEN THE TOUCHPAD IS AVAILABLE TO YOU.   USE THIS!

---

### Post by novikov on 2013-04-08
> > A workaround is NOT to activate the "disable touchpad while typing" and  add the call to "syndaemon -d -i 2" on the startup applications.
Seems like a good solution to me. Thanks.

---

### Post by oldos2er on 2013-04-08
Old thread closed.

---

