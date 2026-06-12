---
title: "xorg grabbing all cpu"
date: 2012-08-02
forum: Desktop Environments
---

### Post by degarb on 2012-08-02
I am on old machine ( 2ghz )with Ubuntu 12 with lxde.

conky is showing xorg as grabbing wayyyy tooo much cpu. Often taking machine responsiveness down when I try to wake up the machine after being idle.

I see old threads that do not apply to 12.

---

### Post by ajgreeny on 2012-08-02
What hardware, in particular your graphic card?

If you don't know what it is, let's see the output of ```
lspci
``` and perhaps also ```
sudo lshw -C display
```in terminal.

---

### Post by degarb on 2012-08-02
I type and type that in, but keep getting bad syntax..... Wait, on another machine, running XP Home.  Do I need to be on that machine or just one running Linux.  Does the version of Ubuntu matter?  

Sorry, joking for those reading with undiagnosted Asbergers tendencies. I will get on the machine by Sunday. 


I do know this 2002 video card gave debian 2010 fits (or other way around), because the video card would go narcoleptic.  Thus I used xp, and debian quit autoupdating with no login for over a year.

I found old thread of mine: [http://forums.linuxmint.com/viewtopic.php?f=90&t=62362&p=358266](http://forums.linuxmint.com/viewtopic.php?f=90&t=62362&p=358266)

Graphics: Card Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device X.Org 1.7.7 Res: 1280x1024@60.0hz 
GLX Renderer N/A GLX Version N/A

---

### Post by degarb on 2012-08-02
[http://askubuntu.com/questions/69120/100-cpu-usage-with-on-demand-setting-due-to-xorg](http://askubuntu.com/questions/69120/100-cpu-usage-with-on-demand-setting-due-to-xorg)  looks promising.

---

