---
title: "Simple Gnome Panel Applet in Python"
date: 2011-05-18
forum: Desktop Environments
---

### Post by 7times9 on 2011-05-18
Hi,

When I'm on the train to work I connect my netbook to my Nexus One's wifi hotspot. As I go through a tunnel my phone obviously loses it's 3G connection and takes a while to re-establish once the train emerges. But the netbook wifi logo stays constant as it's still connected to the phone itself.

I've written a little python program that attempts to ping a server and thus decides if internet is available (feel free to suggest a method that would be either quicker or use less bandwidth as I am capped per month).

My question is: how can I create an applet for GNOME Panel 2.30.2 in Python, to display this status, so I can decide when to continue clicking links and expecting internet to work.

I got this [example]("http://ubuntuforums.org/showthread.php?t=496185") with a panel button to work but would like an icon that changes depending on the situation.

I've used Python for a few years haven't coded gnome before. I'm using the ubuntu desktop edition as my login rather than unity, on 10.04.

thanks!

---

### Post by 7times9 on 2011-08-16
Just to update this post, I [asked my question]("http://stackoverflow.com/questions/6094506/simple-gnome-panel-applet-in-python") on another site and received [this great answer]("http://stackoverflow.com/questions/6094506/simple-gnome-panel-applet-in-python/6188423#6188423").

My toy implementation called [net-panel]("https://github.com/tomviner/net-panel") is on github.

---

