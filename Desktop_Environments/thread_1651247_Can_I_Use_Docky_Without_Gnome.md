---
title: "Can I Use Docky Without Gnome?"
date: 2010-12-22
forum: Desktop Environments
---

### Post by LaneLester on 2010-12-22
I like to try different combinations of *buntu in the several partitions on my first drive. One combo I enjoy playing with is the Minimal CD with Openbox or some other small footprint window manager.

I'd like to try Docky, but the need for compositing is a problem for me. I don't want to install Gnome, KDE, or XFCE, because I don't want all the stuff that comes with them.

Can you tell me the packages I need to install to get Docky working? 

Are Compiz and Docky enough?

Will Compiz serve as a standalone window manager and automatically start at logon?

Lane

---

### Post by Version Dependency on 2010-12-23
You can use all the popular docks like Awn, Cairo Dock, and GLX Dock in desktop environments other than Gnome...and in a standalone window manager desktop like Openbox or Compiz.  For compositing, you will need install a composite manager such as xcompmgr.  There may be some issues with the dock applets though.  Expect some of them to not work.

I have used standalone Compiz before ([here]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") is an excellent guide) with [mygtkmenu]("http://sites.google.com/site/jvinla/mygtkmenu") for a right-click menu and [AWN]("http://wiki.awn-project.org/") for the dock.  But some of the applets wouldn't work (logout won't work...I don't think the trash applet worked either...I'm sure there were a couple others that wouldn't work).

---

### Post by LaneLester on 2010-12-23
> **Version Dependency said:**
> I have used standalone Compiz before ([here]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") is an excellent guide) with [mygtkmenu]("http://sites.google.com/site/jvinla/mygtkmenu") for a right-click menu and [AWN]("http://wiki.awn-project.org/") for the dock

Thank you for a very helpful response, especially the link to the CrunchBang thread on how to do it. I'll give it a try today.

I spent some time with CrunchBang a while back. I don't remember why I eventually abandoned it, perhaps because of its Debian base which I find too slow to update to newer goodies.

Lane

---

### Post by nilesr on 2010-12-23
Yes, I used it with xinit on ubuntu server.

---

### Post by Version Dependency on 2010-12-23
> **LaneLester said:**
> Thank you for a very helpful response, especially the link to the CrunchBang thread on how to do it. I'll give it a try today.

I spent some time with CrunchBang a while back. I don't remember why I eventually abandoned it, perhaps because of its Debian base which I find too slow to update to newer goodies.

Lane

That post showing how to setup a Fusion session was back when Crunchbang was Ubuntu-based.  So everything in that guide works in Ubuntu as well.  I followed it step-for-step and had a Fusion session setup in just a few minutes in 10.04.

---

### Post by LaneLester on 2010-12-24
> **Version Dependency said:**
> That post showing how to setup a Fusion session was back when Crunchbang was Ubuntu-based.  So everything in that guide works in Ubuntu as well.  I followed it step-for-step and had a Fusion session setup in just a few minutes in 10.04.

Yes, it worked for me, too, and I'm very pleased with the result.

I started with a fresh install of the Ubuntu Minimal CD 10.04 and used this script to get the basic stuff in:
```
#!/bin/sh
# After the base system is installed, set root pw, log in and use nano to uncomment repositories.
# http://goo.gl/1KAFU for CrunchBang procedure
# Execute this script.
# Install nvidia-current after reboot.
# Copy over working xorg.conf (/mnt/arc/ZipLinux/MinimalCD/).
apt-get update
apt-get install xorg xterm gdm lxpanel compiz fusion-icon compizconfig-settings-manager cairo-dock menu firefox checkgmail emelfm2 htop leafpad feh synaptic --no-install-recommends
service gdm start
```

After that was going, I executed another script to install the rest of the programs I wanted.

I decided to go with Cairo Dock instead of Docky because I wanted the subdocks in order to have more programs available from the dock. I would have tried AWN, but Synaptic wanted to install all of the Gnome stuff.

Lane

---

