---
title: "system monitor with stats in top bar"
date: 2008-10-19
forum: Desktop Environments
---

### Post by .vinsai. on 2008-10-19
I'm a recent convert from the MS Devil, and lemme say, glad to be here.

That said, I was wondering if there were any addons similar to this [www.statbar.nl](www.statbar.nl) for Linux.  If you still use windows, do yourself a favor and download that program.  Screens here, every version of windows should come with it. [http://www.statbar.nl/index.php?action=screenshots](http://www.statbar.nl/index.php?action=screenshots)

In a nutshell, its a little bar that sits on top of your screen and can be configured to display CPU and RAM usage in realtime, up and download speed also in real time, shortcuts to programs and all kinds of niftiness.  Since Linux can already do most of that, I'd just be happy with finding something that displays my RAM and CPU usage up there for me.

---

### Post by hansdown on 2008-10-19
Hi . vinsai.

There is a fairly good applet and tutorial here.

[http://ubuntu-tutorials.com/2008/06/20/at-a-glance-system-monitoring-with-panel-applets/](http://ubuntu-tutorials.com/2008/06/20/at-a-glance-system-monitoring-with-panel-applets/)

---

### Post by mcduck on 2008-10-20
Just use a combnation of any panel applets you want. There's a bunch already installed, and more available in the repositories. I recommend getting the hardware-monitor applet at least. It monitors CPU , RAM and network usage, temperatures, fan speeds and pretty much everything you'd want to know about your system. And of course you can add many instances of the same applet, configured to display different information.

[http://people.iola.dk/olau/hardware-monitor/]("http://people.iola.dk/olau/hardware-monitor/") (The package is in Ubuntus repositories)

Then just drop all the applets in to the panel, locate them where you want them and if you wish, configure the panel background/color or set it to use a picture as background. Transparent .PNG:s make great looking panel backgrounds..

---

### Post by .vinsai. on 2008-10-20
Very cool, thanks for the replies.  Is there any way to manipulate these to display just the percentages?  The little lines don't do much for me.

Also, system monitor indicates that over 77% of my memory is in cache, hardly any of it is free, but when I actually open the System Monitor applet, it indicates I'm barely using over 320mb of my 2.0gb of RAM.  What is the cache?

**Edit
Anyone know any more programs for that sort of thing?  I couldn't get statbar to run in wine >.<

---

### Post by mcduck on 2008-10-23
at least the hardware-monitor applet has many different ways to show your information..

What comes to the cache thing, the system monitor only shows the actual used memory and doesn't include buffers or cache. That makes sense, in a way, since most of the time the cache uses all free RAM. If your programs need more RAM some data will simply be dropped from cache. So the RAM sued by cache would still count as "free".

Cache is just used for storing files you access to RAM, so if you need them again the system doesn't need to read them from disk again. It can simply get the data directly from RAM instead. As RAM is much faster thn your hard disk this increases your system's performance quite a lot..

..besides, if the RAM isn't used for anything it's simply wasted. Better to use it as cache when your programs don't need it. ;)

---

### Post by bondmatt on 2010-02-02
Out of nowhere system monitor is showing 33% of my RAM as being used for cache. I am running Ubuntu 8.04 (actually I run CAELinux but it is just Ubuntu 8.04 with a bunch if engineering software preloaded). I stopped a simulation of fluid flow before shutting my computer down the last time. Could this be causing the cache memory usage?

Thanks,
- Matt Bondy

---

### Post by mcduck on 2010-02-03
> **bondmatt said:**
> Out of nowhere system monitor is showing 33% of my RAM as being used for cache. I am running Ubuntu 8.04 (actually I run CAELinux but it is just Ubuntu 8.04 with a bunch if engineering software preloaded). I stopped a simulation of fluid flow before shutting my computer down the last time. Could this be causing the cache memory usage?

Thanks,
- Matt Bondy

All the RAM that isn't used for anything else is _supposed to be used as cache_.

Having compeltely unused RAM doesn't benefit you in any way. Which is why Linux uses it to store recebntly accessed data, to avoid having to read it again from the hard drive. Should any program need more RAM, some cached data is simply dropped so that part of memory stoll counts as free from any program's point of view.

---

