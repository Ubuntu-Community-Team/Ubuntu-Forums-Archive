---
title: "Need tips for speeding up Gnome"
date: 2005-08-31
forum: Desktop Environments
---

### Post by elemental_silver on 2005-08-31
I'm sorry if this has been asked a million times, but I have a twist on this popular question. My computer runs SLOW (about 5 minutes to open open office.org) and I'd like to compile a list of tips for my own and future reference of how to tweek it to increase speed without installing additional software. Again, sorry if this has been asked alot, but I'm generally new to the Linux world.

---

### Post by byen on 2005-08-31
hey buddy...lets start out with some specs.....

---

### Post by bored2k on 2005-08-31
1. Enable prelink. [http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=1971&highlight=prelink) . You want this.
2. Install and replace metacity with Openbox. [http://www.ubuntuforums.org/showthread.php?t=34239&highlight=openbox](http://www.ubuntuforums.org/showthread.php?t=34239&highlight=openbox) You may not like this (it will still be Gnome).
3. Use a lighter browser like epiphany-browser.
4. Stay away from java.

---

### Post by elemental_silver on 2005-08-31
[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=92804&cc=us&docname=c00008588](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=softwareCategory&lc=en&product=92804&cc=us&docname=c00008588)
That's the stock specs I have on it, but I've installed a second 4 gig HD for lots of extra swap space(2 gigs worth). I also installed more ram, but not much. I'm up to a whopping 64 megs of ram, I believe. Too bad it only has one ram slot... I might have more ram, though, haven't checked it out in a while. *sigh* Its not much of a computer, but I'm doing what I can with the parts I have.

---

### Post by Crimguy on 2005-08-31
[QUOTE=elemental_silver]I'm sorry if this has been asked a million times, but I have a twist on this popular question. My computer runs SLOW (about 5 minutes to open open office.org) and I'd like to compile a list of tips for my own and future reference of how to tweek it to increase speed without installing additional software. Again, sorry if this has been asked alot, but I'm generally new to the Linux world.[/QUOTE]
 Well, these<i>does</i> involve installing software - see if they still have the OOo quickstarter.  Loads up as an applet on the panel, and will greatly cut your load times for OpenOffice.  It used to be pretty buggy, but maybe it's gotten better.

Also, install your appropriate graphics drivers.  nVidias package is surprisingly easy in ubuntu.

Consider changing the default way the filemanager works via gconf.  Change it to the traditional Nautilus setup.  It reduces the workload by having a few less windows open.  Check your .bashrc to see if any unnecessary files are loading up at start.  Avoid gdesklets, and keep the number of applets to a minimum.

If it's still too slow, you need to consider a new wm.  gnome isn't the end-all be-all.  Try kde, which I think is just a tad faster.  I'm a big fan of fluxbox, which is very lightweight, but not as useable. xfce is very hip these days too (haven't tried it but it looks nice). 

If you're really adventurous, and don't mind devlopment software, and have hours to kill, try to get E17 going ([www.enlightenment.org)](www.enlightenment.org)).  I hear it's incredibly fast, and looks amazing.  That'll be my next project.

---

### Post by byen on 2005-08-31
i strongly suggest XFCE desktop (plus some XFCE tuning mentioned in vaious threads) or fluxbox! .gnome/kde...do need some meat and that is what you do not have,,,,if you ask me...i think XFCE/fluxbox is the way to go!

---

### Post by elemental_silver on 2005-09-01
Tried KDE which ran much MUCH slower than Gnome... But thanks for the couple tips. My big problem is that I don't want to run programs back and forth on CD... I don't have a network or internet connection to my linux box

---

### Post by sb73542 on 2005-09-01
[QUOTE=elemental_silver]Tried KDE which ran much MUCH slower than Gnome... But thanks for the couple tips. My big problem is that I don't want to run programs back and forth on CD... I don't have a network or internet connection to my linux box[/QUOTE]
 XFCE4 is pretty slow, even with 128MB of RAM.

---

### Post by Wolki on 2005-09-01
[QUOTE=Crimguy]
Consider changing the default way the filemanager works via gconf.  Change it to the traditional Nautilus setup.  It reduces the workload by having a few less windows open.  [/QUOTE]

Not necessarily. You can still keep the number of windows down with spatial nautilus, and since it's a bit lighter the single windows are faster. I have directories that are instantly accessible using spatial nautilus, while taking noticably longer using the browser mode.

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 fluxbox is nice and light.....and its no secret gnome isn't light on resources, its actually one of the main issues you always hear come up

---

