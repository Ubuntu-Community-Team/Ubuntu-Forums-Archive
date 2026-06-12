---
title: "Desktop appears weird, icons change - See pics"
date: 2009-05-07
forum: Desktop Environments
---

### Post by ubuser_7 on 2009-05-07
Hi

I am running Jaunty on a Thinkpad T61, T7300. I use compiz. 

I have a weird problem (IMO). 

My desktop usually looks like [this]("http://isingh.info/downloads/Problem/Screenshot-1.png") [IMG]http://isingh.info/downloads/Problem/Screenshot-1.png[/IMG]

However, all of a sudden something will happen and it starts to look like [this]("http://isingh.info/downloads/Problem/Screenshot_Bad.png") [IMG]http://isingh.info/downloads/Problem/Screenshot_Bad.png[/IMG]

Notice how the menu bar and awn look different. The icons and everything is of a completely different theme. The menu bar reminds me of the menu bar that appears on programs when I start them with root privledges. (like i do a gksudo gedit, then it has this same feel). 

Now the weird thing is there is absolutely nothing in the logs. I checked /var/log/syslog, /var/log/messages, dmesg but nothing at all.

Just FYI, the two images above are taken at different times. The error happens almost any random time. In intrepid I rarely saw this, and when I did I would loose the styling on my windows too (which doesnt happen anymore). In Jaunty this is more common (nearly once in 1-2 days). A simple restart of gdm is enough. 

I still havent found a common link in terms of apps I am running when I see this. Apps like terminal, firefox etc are always on, so I wouldnt be able to tell. Compiz runs fine, even after this.

Any suggestions, any questions?

Thanks!

---

### Post by mcduck on 2009-05-07
Looks like gnome-settings-daemon failing, for some reason or other. Try loking in the ~/.xsession-errors -file if you can find anything..

---

### Post by ubuser_7 on 2009-05-07
> (emerald:21900): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(emerald:21900): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(emerald:21900): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(emerald:21900): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


This *might* be the problem. Since the file doesnt have time stamps, it difficult to tell. These lines stand out in the log, while other errors are repeated. 

I can upload the whole file if needed.

---

### Post by ubuser_7 on 2009-05-12
Bump

---

### Post by G|N| on 2009-05-12
I have the same problem!

The panel is still "themed" but the icons in the notification area aren't

---

