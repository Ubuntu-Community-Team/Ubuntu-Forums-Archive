---
title: "Unexplained slow down"
date: 2007-08-25
forum: Desktop Environments
---

### Post by jigal on 2007-08-25
Hi guys.

I am quite puzzled by the behaviour of my ubuntu.
The specs of my system should be good:
Pentium D 930 (2 cores x 2MB L2 cache @ 3GHz)
2GB of DDR (667).
6600gt nVidia graphics - using nVidia driver (tried Beryl - stupendous - but mostly worked without it).
I run 7.04 + KDE (though Gnome is also installed - and I use it for my wife's user - gnome is simply beautiful desktop environment, but much less customizable than KDE, at least for the normal non-command-line user).

The thing is that *lately* - I get sluggish/slow response from my desktop.
Command line seems to be functioning correctly at machine speed, but, 
I get slow response when I perform GUI stuff, such as scrolling down, selecting.
I mostly use firefox...., but I also use evince, acrobat reader, etc.
Trying to run system-monitor reveals no offender - the system is mostly quiet - but even then - the monitor itself may reach 15-20% CPU - as if the CPU itself is very sluggish.
I do not see any shortage of memory usage - though my linux partition is at 87% capacity, which is usually, bad - but I rarely see any harsh hdd activity - it seems mostly cpu/memory oriented problem (e.g., could it be poor L2 cache hit rate?)

I used to get lightning response time from Ubuntu - and I used to think my h/w system had good performance too....

Any suggestions would be very appreciated.

Thanx.

---

### Post by iamhugeinjapan on 2007-08-25
Have you started using any different themes lately? Not all themes perform at the same speed.

---

### Post by jigal on 2007-08-26
Nop - I use a modified KDE theme....

Can system monitor consume constantly at about 20% CPU?
I also observe that Xorg is constantly beneath it at 6-15% (mostly at 10%, though....)

Also - is there a more fine grained CPU monitor, that disects CPU consumption to individual modules?

---

### Post by trippinnik on 2007-08-26
What services are you running?  Does it only happen with firefox open?  Do you have any firefox extensions?

---

### Post by jigal on 2007-08-26
Good questions - I an running  firefox with extensions - and there are quite a few services executing as well (using KDE System-->Services viewer).

I am thinking whether it could be related to image repainting or font rendering.

When you tab-switch between applications - say firefox and thunderbird, or just gedit for that matter - what is the expected delay?
 see delay of approx 1 sec - which I think is mostly attributed to the painting of the newly exposed window.

Actually - after thinking about it - it seems the problem is related to KDE configuration of
KDE-->Settings-->Control Center-->Appearance & Themes-->Style: GUI effects.
I just cleared the GUI effects and the system seems more responsive - and the windows are painted alot quicker.

Perhaps I should work with Beryl - as it uses H/W acceleration to achieve this eye-candy.... - what do you think?

Thanx.
Jigal.

---

### Post by trippinnik on 2007-08-30
Depends on the hardware you have and the driver support for your gfx card.  Even on my low end (old) laptop Beryl was running fine, but the drivers opensource drivers for ATI are so crappy it would hard crash often.

---

### Post by gtdaqua on 2007-08-30
Do you have SWAP configured? If not you system will become painfully slow as you keep working. If you have not configured SWAP, then it is time to.

Go here and get it done:

[http://ubuntuforums.org/showthread.php?t=36877]("http://ubuntuforums.org/showthread.php?t=36877")

Its better if SWAP is double the size of physical RAM. Or atleast equivalent to the RAM.

---

### Post by trippinnik on 2007-08-30
Although anything over 4Gb Memory and SWAP combined is overkill (unless you are running 64bit kernel).

---

### Post by jigal on 2007-08-30
Ok - I have a swap of approx. 3.7GB size, which is just below 2x my RAM size, though I seldom reach large memory requirements...

Also, after some days of good experience with the KDE GUI effects, I can say that the KDE GUI effects are quite expensive, even for a system I thought was rated ok in terms of CPU/memory performance.
Well, not in the level of the newer Core2 or AMD K7, but still, for Linux with considerable L2 cache, I thought it was more than enough.

Is Beryl faster on GUI effects than KDE?
I imagine it should since it uses OpenGL for this, and since I am using nVidia's glx drivers, which I thought were considered ok (nobody knows for sure since they're closed, right).

On the same token - is there a more advanced profiling program I can use for diagnosing system bottlenecks, especially in terms of performance?
I mean, guessing on hunch is not a reliable method, don't you think?

Thanx for the help!

---

### Post by gtdaqua on 2007-08-31
SWAP looks ok. 

did u try running "top" from command line and see whats is eating up all that resources? Beryl has several side effects - i would not suggest to try Beryl on ur system now (it already is slow for some reason, right? thats why). "top" is a good utility to start with.

to be honest, i have witnessed several pentium processors to be very slow - but that is a diff story. 

u could try some performance tweaks (actually works). Its forcing ubuntu to use the SWAP in the way you want. Its called 'swappiness' which has a value between 0 and 100. The value determines how fast the kernel should fill up your swap space. Value 100 means swap will be used immediately and 0 means swap will be used as late as possible.

The default is 60. Reduce the value 15 or 20 and u might see some improvement in application responsiveness.

EDIT: see the next post how to tweak "swappiness"

---

### Post by gtdaqua on 2007-08-31
sorry, forgot to add how it is done. Here you go

check the value here: 
# sudo cat /proc/sys/vm/swappiness   

change the values: edit the file:
# sudo nano /etc/sysctl.conf:

add this line at the end of the file: (without quotes)
"vm.swappiness=15"

You could try lowering the value - doesnt harm but 15 or 10 should be more than ok.

save and reboot.

Let us know if u see any difference.

---

### Post by jigal on 2007-09-01
Well - I tried the system monitor that comes with KDE, I think.
It didn't show a particular offender - though xorg was always 2nd/3rd with something like 10-20% CPU (don't have history graph for this).
In fact, system monitor itself did show consumption that overshadowed the xorg...
Though, once again, vlc plays well in the background, and say, cli applications (like what I am writing for my thesis) works pretty fast - they do not consume any graphics except printing small stuff on the gnome-terminal....
But even cpu consuming like tar+bzip2 weren't affected by this.

The most notable effect was the laziness of the display, of switching between windows, scrolling up/down, moving, resizing, etc....

I will try swapiness.... - never new about it (like the other 10,000++ kernel tweaks and tricks...)

Is there a more in depth performance monitor there? Something that could profile a running process?

---

