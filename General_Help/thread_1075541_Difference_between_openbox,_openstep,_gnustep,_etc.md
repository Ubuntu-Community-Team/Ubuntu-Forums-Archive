---
title: "Difference between openbox, openstep, gnustep, etc..."
date: 2009-02-20
forum: General Help
---

### Post by grndslm on 2009-02-20
Soo... riddle me this:  What is the difference between openbox, openstep, gnustep, & windowmaker ???

---

### Post by grndslm on 2009-02-20
Openbox & Window Maker are more just window managers, while Openstep & Gnustep try to be more like desktop environments?!?

Does anybody use Openstep and Gnustep anymore?  I hear about Openbox & Window Maker every so often, but not the *steps.

---

### Post by grndslm on 2009-02-20
Seriously?  Nobody knows?

Should I just use OpenBox and be happy?

---

### Post by snova on 2009-02-20
As far as I can tell, OpenStep and GNUstep aren't window managers at all. OpenStep seems to be an API (Cocoa perhaps being the most prominent implementation), GNUstep is an implementation of that API for GNU.

---

### Post by grndslm on 2009-02-21
Hmmm... I did find some Openbox comparisons you guys might wanna check out:

- [http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/](http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/)
- [http://david.chalkskeletons.com/blog/?p=43](http://david.chalkskeletons.com/blog/?p=43)
- [http://osnews.com/thread?261255](http://osnews.com/thread?261255)

Then some Openbox documentation:

- [http://wiki.archlinux.org/index.php/Openbox](http://wiki.archlinux.org/index.php/Openbox)
- [https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

Short story is that Openbox is up to date and still actively supported.

I noticed that Openbox has easy integration with GNOME, which I have been a fan of because of the applets.  Tho, obviously the real benefit of Openbox is dropping GNOME altogether, so I'm gonna try that out, looks like.  Gonna be rough, but hopefully I can turn my desktop into something BETTER than GNOME!!

---

### Post by handy on 2009-02-21
> **grndslm said:**
> 
Should I just use OpenBox and be happy?

YES.

Openbox is very popular, simple, quick & configurable.

Many of us love our Openbox. :D

---

### Post by mb_webguy on 2009-02-21
I'm using an Openbox session as an alternative to my regular Gnome login.  It took a little bit of configuration to get it how I wanted (mostly involving edits to the menu), but I'm pretty happy with it.  

If you want a simple menubar, I suggest PyPanel.  It's lightweight, but it has a decent amount of functionality (such as a desktop switcher, task bar, system tray, and clock).  It's easily configurable and fairly attractive, and all of the independently executable Gnome applets will work with it.

---

### Post by lykwydchykyn on 2009-02-21
I've used windowmaker before, though I didn't like it enough to stick with it.  Why not check it out?  It's pretty lightweight, and definitely not another WIMP clone.

---

### Post by handy on 2009-02-22
I use the xfce4-panel with Openbox, my desktop looks identical to when I was running Xfce, except the computer is noticeably faster.  I also like my Openbox menu better than what I had with Xfce.

The only thing I have lost is a session-manager. Which means that Openbox doesn't remember what I had open when I log out.

So what I have done is start my regularly used tools in the .config/openbox/autostart.sh file.

This starts all of the files I called automatically when I open Openbox, but they are all on desktop.1.

Apparently one way I can solve this is to use [*_Devil's Pie_*]("http://burtonini.com/blog/computers/devilspie") which will allow me to configure what happens on each desktop. I haven't got around to trying Devil's Pie yet.

I did try using the Xfce session-manager, but it slowed the machine down to Xfce speed, it really seemed as though I was just running Xfce.

---

### Post by grndslm on 2009-02-22
> **mb_webguy said:**
> If you want a simple menubar, I suggest PyPanel.  It's lightweight, but it has a decent amount of functionality (such as a desktop switcher, task bar, system tray, and clock).  It's easily configurable and fairly attractive, **and all of the independently executable Gnome applets will work with it.**What do you mean by independently executable Gnome applets?

... like the volume, weather, and system monitor applets??  or gdesklet applets??

---

### Post by mb_webguy on 2009-02-22
I mean those you can run independently of gnome-panel, such as the Network Monitor applet (nm-applet), Power Manager applet (gnome-power-manager), and Bluetooth applet (bluetooth-applet), but not the Volume applet, as that's apparently hard-coded into gnome-panel.  Anything you can initiate from the command-line.

---

### Post by handy on 2009-02-22
The xfce4-panel also allows you to use all of the plugins & items that are available for it in Xfce.

The Xfce panel page:

*_[http://www.us.xfce.org/projects/xfce4-panel/](http://www.us.xfce.org/projects/xfce4-panel/)_*

Panel plugins from the Xfce goodies project:

*_[http://goodies.xfce.org/projects/panel-plugins/start](http://goodies.xfce.org/projects/panel-plugins/start)_*

---

### Post by grndslm on 2009-02-22
Damm!  If I coulda gotten those three applets on Openbox, it'd be a sure fit... but I'm not sure I can live without all three of those applets, or at least ones that behave exactly like them.

The volume applet in Xfce won't allow you to scroll the volume up/down with the wheel unless you're in a certain section of the applet (i.e. - not the green volume meter)... and the weather applet doesn't display the temp at all times, but it does display wind speed and direction (nice!)... and the system monitor doesn't show as much stuff as GNOME's, and whn you click on GNOME's system monitor applet, the gnome-system-monitor pops up.  GNOME appears basic and bloated, but it's as intuitive as a desktop has gotten for me yet.

---

### Post by mikjp on 2009-02-22
> **grndslm said:**
> Soo... riddle me this:  What is the difference between openbox, openstep, gnustep, & windowmaker ???

The difference between openbox and windowmaker is clear once you install windowmaker :-)

---

### Post by handy on 2009-02-22
> **grndslm said:**
> 
The volume applet in Xfce won't allow you to scroll the volume up/down with the wheel unless you're in a certain section of the applet (i.e. - not the green volume meter)... 

I can adjust the volume with the mouse wheel as long as the pointer is anywhere on the applet?

You can also set a keyboard combo' like ctrl + up arrow to adjust volume up, or whatever other combination you like.

This how-to is great for Openbox:

*_[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)_*

---

