---
title: "Add Crucnhbang to Ubuntu"
date: 2009-03-14
forum: Desktop Environments
---

### Post by RD1 on 2009-03-14
I've been playing around with the Crunchbang live CD and I do enjoy the minimal GUI. It remind me of my Win2000/Litestep days.

I was wondering if it was possible to add the Crunchbang desktop to my Ubuntu install. I do not want to start with a clean install and I do not want to dual boot.I also would like to retain my Ubuntu desktop and have the choice of which to use at login. Just like choosing Gnome or KDE.

Could I simply install over Ubuntu, choosing not to format any partitions?

Could I simply add Crunchbang's repositories to synaptic and then install Crunchbang-desktop?

Any suggestions?

---

### Post by perlluver on 2009-03-14
> **RD1 said:**
> I've been playing around with the Crunchbang live CD and I do enjoy the minimal GUI. It remind me of my Win2000/Litestep days.

I was wondering if it was possible to add the Crunchbang desktop to my Ubuntu install. I do not want to start with a clean install and I do not want to dual boot.I also would like to retain my Ubuntu desktop and have the choice of which to use at login. Just like choosing Gnome or KDE.

Could I simply install over Ubuntu, choosing not to format any partitions?

Could I simply add Crunchbang's repositories to synaptic and then install Crunchbang-desktop?

Any suggestions?

You could, but it is not recommended.  You would be better off to install Openbox and configure it how you want it.  [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/), this guide should be of help.

---

### Post by RD1 on 2009-03-14
> You could, but it is not recommended. You would be better off to install Openbox and configure it how you want it. [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/), this guide should be of help.

Maybe I'll just go that route. I do like the fact that Crunchbang has so much of the configuration done already.

---

### Post by perlluver on 2009-03-14
> **RD1 said:**
> Maybe I'll just go that route. I do like the fact that Crunchbang has so much of the configuration done already.

That is a plus to Crunchbang, I kinda liked it, but found it missing some things, and it automatically turned off my screen, which messed up my resolution.

---

### Post by gjoellee on 2009-03-14
CrunchBang=Ubuntu+Openbox+Configuration

It is not hard to make your Ubuntu installation become "#!CrunchBang"

---

### Post by jjgomera on 2009-03-14
if you run crunbank liveCD, you can copy openbox configuration, copy folder /home/usuario/.config/openbox to a pendrive.
In ubuntu, install openbox, copy the configuration to your ubuntu instalation configuration, check menu and install other app crumbang use

---

### Post by RD1 on 2009-03-14
> That is a plus to Crunchbang, I kinda liked it, but found it missing some things...

Which is why I want to keep my Ubuntu install. :D

> if you run crunbank liveCD, you can copy openbox configuration, copy folder /home/usuario/.config/openbox to a pendrive.
In ubuntu, install openbox, copy the configuration to your ubuntu instalation configuration, check menu and install other app crumbang use

Now why didn't I think of that?! :o Sounds like the way to go.

---

### Post by snowpine on 2009-03-15
Hi RD1, 
Crunchbang has an install script. You can install it on top of your existing Ubuntu install by following these instructions: *edit: see below*

---

### Post by Kangarooo on 2009-07-18
> **jjgomera said:**
> if you run crunbank liveCD, you can copy openbox configuration, copy folder /home/usuario/.config/openbox to a pendrive.
In ubuntu, install openbox, copy the configuration to your ubuntu instalation configuration, check menu and install other app crumbang use

Actually you dont need live cd. Default is posted here for reasons if sometimes messing with it its messed up :) [http://crunchbang.org/wiki/crunchbang-linux-conky-config/](http://crunchbang.org/wiki/crunchbang-linux-conky-config/)

---

### Post by b.a.w on 2009-07-18
Thats conky config file not openbox config. I would do as suggested above, just copying it from crunchbang. Openbox can be a pain from scratch.

---

### Post by snowpine on 2009-07-19
Here's the new Crunchbang script for 9.04:

[http://www.crunchbanglinux.org/wiki/downloads#alternative_installation](http://www.crunchbanglinux.org/wiki/downloads#alternative_installation)

---

