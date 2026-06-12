---
title: "Desktop panel switching is slow"
date: 2006-08-16
forum: Desktop Environments
---

### Post by tizatron on 2006-08-16
My first post - *cough*.  I am new to ubuntu, I switched from RedHat/WindowMaker to Ubuntu/Gnome.

During my initial setup I was tweaking gdm to allow X connections from my Unix world.  Eventually I got things working, but a short while later I noticed that switching from panel to panel was very slow, over a minute, sometimes even longer.

It usually happens like this - I click on the panel I want in the panel selector and nothing happens.  The applications in the current panel remain active - I can sendmail, browse the web etc. but I cannot use any icons from the desktop nor can use any Applications from the menu bar.

Eventually, the desktop switches to the requested panel and all is normal.  I can move from panel to panel instantly.  Then I settle in on a panel and an hour or so later - the same effect.

I thought I might be CPU bound - so I installed a CPU monitor on the menu bar.  The CPU seems fine - even when the panel is locked.

Any thoughts?  Could it be related to my gdm tweaks?  Is there any logs that I can check?  Perhaps there is a related thread?

Gnome 2.14.3 Ubuntu 2.6.15-26-386

Thanks...

---

### Post by tizatron on 2006-08-21
Appears to be related to the portmapper.  Checked the messages file - some complaints about the portmapper - installed the portmapper with synaptic and seems to be better.  Panel switching is much better.

However, I should also note that I turned off all my power management in the computer bios.  I also walked my process list with ps() and removed a couple of non-required programs - no real difference - pretty sure it was the portmapper.

Perhaps in a sane moment I will turn the power management back on a see if there is any affect.

---

