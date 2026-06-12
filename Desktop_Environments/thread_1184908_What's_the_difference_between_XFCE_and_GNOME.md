---
title: "What's the difference between XFCE and GNOME?"
date: 2009-06-11
forum: Desktop Environments
---

### Post by Fzang on 2009-06-11
I guess this must be an age-old question, or what? Anyways,

What's the difference between XFCE and GNOME?

They can use the same icons and themes, right? And Thunar on GNOME must mean that XFCE uses GTK as well. I've even heard about some application, gnome.. something.. that allows for even greater compatibility between GNOME and XFCE..

The main difference I can think of is the different applications, but are there any "deep" differences?

---

### Post by sabmo on 2009-06-11
I'm not an expert but I've used both and I'll try to summarize.


The basic toolkit of both systems is GTK+

However GNOME uses extra librarys on top which add extra functionality but the XFCE project was started (I think) because they don't want to be forced to use these dozens of extra GNOME librarys and don't see the added bloat and slowness being worth the extra features.

XFCE does use some of the GNOME librarys but tries to use as few as possible.

In order to do this XFCE has had to re-make some essential functionality to replace the parts of GNOME which they cut out such as Thunar which replaces nautilus, a panel replacement for gnome-panel, a terminal replacement for gnome-terminal and a whole host of other applications which are slimmed down (less featured) versions of standard gnome tools.

The result is you get a desktop with smaller faster applications which works similar to GNOME and uses the same graphics toolkit GTK+ but has a few less features.

Give XFCE a try, you may like it. Personally I ended up switching back to GNOME after a few weeks but I dont have any complaints about XFCE its a nice desktop and I'd run it on an older machine for sure.

---

### Post by Fzang on 2009-06-11
I've heard a lot about running XFCE on Arch is much faster than Ubuntu. Is any of this talk plausible? And does XFCE speed up boot time since there's less to load?

---

### Post by kerry_s on 2009-06-11
> **Fzang said:**
> I've heard a lot about running XFCE on Arch is much faster than Ubuntu. Is any of this talk plausible? And does XFCE speed up boot time since there's less to load?

xfce on arch faster? yes, most every xfce4 distro is faster than ubuntu.
xfce4 does not effect boot time, load time is pretty much the same as gnome when going through gdm.

i'm running a custom install xfce4 on debian testing, my laptop is 450mhz 256mb ram. it's fast enough. :)

---

