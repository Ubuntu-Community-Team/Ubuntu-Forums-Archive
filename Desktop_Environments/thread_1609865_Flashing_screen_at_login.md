---
title: "Flashing screen at login"
date: 2010-10-30
forum: Desktop Environments
---

### Post by scott.enderle on 2010-10-30
Recently, whenever I restart my computer, I am automatically logged in and a rapid sequence of flashes repeats itself over and over. First a white screeen appears. Then my desktop background appears, dimmed and overlaid with the netbook-launcher's up and down arrows in the upper lefthand corner. Then my desktop background appears in full color, with my panel above it but no launcher. Rinse wash repeat. 

I assume it has something to do with Compiz. When escape to a tty and type "compiz --display :0 --replace &" the loop ends and everything works. 

Any ideas how to avoid having to do this every time I restart? 

I'm running 10.4.1 on an MSI Wind U100.

Sorry if this is a duplicate; I can't find information about this anywhere.

---

### Post by kerry_s on 2010-10-30
sounds like you got a very messed up install.
the standard netbook does not come with compiz for good reason, they clash, makes all kinds of bad things happen. the flashing when you log in is because something is crashing & keeps trying to reload, my guess would be gnome panel, cause maximus+compiz crashes gnome panel.

so i'm guessing you have compiz in your startup?
try removing it?

---

### Post by scott.enderle on 2010-11-01
As a matter of fact, I did the opposite, and now it works fine. (That is, I *added* compiz to my startup apps. But I don't understand why I had to do that.)

I had turned on desktop effects a while ago and it worked fine--using compiz, I'm pretty sure. It hadn't been a problem until now.

EDIT: To clarify, I do not consider this issue resolved, because I don't feel like adding compiz to the startup list was the "Ubuntu Way," and I'm concerned it may break at some point in the future. Why did this happen? Thoughts?

---

