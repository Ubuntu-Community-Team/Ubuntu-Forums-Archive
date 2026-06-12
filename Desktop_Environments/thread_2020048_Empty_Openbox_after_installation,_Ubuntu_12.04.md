---
title: "Empty Openbox after installation, Ubuntu 12.04"
date: 2012-07-07
forum: Desktop Environments
---

### Post by Places on 2012-07-07
I just installed Ubuntu 12.04 and openbox according to the instructions on this site ([http://techiesdiary.com/archives/28]("http://techiesdiary.com/archives/28")). I'm completely new to Linux and openbox. How do I get the menus, icons, and toolbar? I looked to this site ([http://linuxinside.blogspot.com/2008/03/openbox-introductioncustomization.html]("http://linuxinside.blogspot.com/2008/03/openbox-introductioncustomization.html")) for help, but I got stuck on step 2.

---

### Post by m_duck on 2012-07-07
Openbox, by default, is pretty bare. If you don't explicitly tell it to run something (e.g. a panel) it won't run. That techniesdiary site forgot a fairly important part of Openbox - copying the configs for your user.

Make sure the following directory exists **/home/yourusername/.config/openbox** and create it if it doesn't:```
mkdir -p ~/.config/openbox
```The tilde simply refers to /home/yourusername and the **-p** switch will create the chain of directories should it need to, and not just the top one (i.e. if .config didn't exist, mkdir would fail with the above command without the -p switch).


You will then want to copy the default configurations into your own folder:```
cp /etc/xdg/openbox/* ~/.config/openbox/
```I think there are now 4 configuration files: autostart.sh, menu.xml, rc.xml and environment something.

**autostart.sh** - script to launch programs (this is what you were wanting to do).
**menu.xml** - XML document describing the main right-click menu.
**rc.xml** - XML document describing *most* of the configuration for Openbox (much of it is reachable via obconf).

Let's say you want to run the panel tint2 at login, just add the following to the end of the autostart.sh file:```
tint2 &
```

Finally, let me give a hearty recommendation to reading through [Urukrama's Openbox guide](http://urukrama.wordpress.com/openbox-guide/).

If I've missed anything, or not explained it properly, just say and I will try to clarify.

---

