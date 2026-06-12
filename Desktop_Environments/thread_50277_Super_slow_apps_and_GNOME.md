---
title: "Super slow apps and GNOME"
date: 2005-07-19
forum: Desktop Environments
---

### Post by Quest-Master on 2005-07-19
Ok, so it comes down to this..

The GNOME menu takes about 10 seconds to load and freezes the entire panel as well as Nautilus.

Firefox takes 15-30 seconds to load, while only 5 on Windows.
Rhythmbox takes 5-10, and foobar2000 on Windows takes 2.
X-Chat takes 5-15, while HydraIRC takes less than 5 on Windows.
Nautilus can take up to 15 seconds while Windows's explorer pops up in less than 5 seconds.
Gnome-Terminal can take up to 10 seconds to load, while the command prompt on Windows, though absolutely terrible, takes 2 seconds.

I have enabled prelink'ing and run it after every apt-get operation. DMA is on all of my drives, so, uh.. I really need to figure out what's wrong, because everyday life on Ubuntu has pretty much watered down to something incredibly slow.

Keeping programs open all the time is not a viable option either since when I do memory-intensive tasks, I am required to close these programs, or even if I have too many open I must do this.. otherwise, GNOME/X will crash or simply freeze or become incredibly unresponsive, laggy, and slow.

---

### Post by angkor on 2005-07-19
Nautilus takes 1 sec to load on my 2ghz, 1g ram comp, without any prelinking. What kind of computer are you experiencing this on?

---

### Post by Lunde on 2005-07-19
Quest-Master, you have 448 posts since Nov 2004, so you are almost a veteran here. I guess this is somethng that happend just now, it cannot have been like this the whole time :-)

Is this on a fresh install?
Did this happen after installing something?
Have you installed a new memory chip with the wrong speed maybe? 
Is your hard drive OK? I read somewhere that DMA can damage your hard drive.. 

It can be that loading the programs into memory is the problem and that when they are running in the memory it's OK, but then the swap is messing up

What happens if you move a large file?

---

### Post by Lunde on 2005-07-19
PS! Make it a file you can spare to lose, and just copy it.

---

### Post by Quest-Master on 2005-07-19
[QUOTE=Lunde]Quest-Master, you have 448 posts since Nov 2004, so you are almost a veteran here. I guess this is somethng that happend just now, it cannot have been like this the whole time :-)

Is this on a fresh install?
Did this happen after installing something?
Have you installed a new memory chip with the wrong speed maybe? 
Is your hard drive OK? I read somewhere that DMA can damage your hard drive.. 

It can be that loading the programs into memory is the problem and that when they are running in the memory it's OK, but then the swap is messing up

What happens if you move a large file?[/QUOTE]

Actually, I don't remember it ever being much faster-- I only recently booted back to Windows XP, and compared the loading times which completely baffled me.

This is an install which was dist-upgrade'd from Warty.
My hard drive is fine as well.

And my specs: 2.2 Ghz Intel Celeron, 256MB of RAM, and a 40GB HD.

I will also try out your latter suggestion now and report what happens.

---

### Post by woedend on 2005-07-19
well its obviously not a hardware issue if windows works it just fine.  The only thing I can think of is that you have something installed thats acting up.  BTW - did your computer come like that...ram and hd seem low with that chip.  I have an athlon 3000, which probably runs at about the same clock speed, and everything loads great.

---

### Post by angkor on 2005-07-19
Well from your specs I think it should run faster than what you are experiencing now, even though 256mb ram is not a lot for a modern graphical OS. 

Maybe you should give fluxbox a try and see how it performs with a lighter wm. If it's still too slow you definately have a configuration problem, or something hardware related.

---

### Post by tea_man on 2005-07-19
i noticed that even on my old pc kde/kubuntu loaded up faster then gnome/ubuntu...and all the apps as well

---

### Post by Lunde on 2005-07-19
I'm sure It should run a lot faster and without problems with your specs. I'm trying to look up what damage DMA can do on your files or disk, but it may be that it only damages the stuff on your linux partition cuz that the only place it writes to. 

If your drive clusters are destroyed, it may be just some of them and they can be located on just a part of your disk. I have an old laptop I cannot use the first section of the disk. But it worked fine on the rest. so I made a D drive and installed there instead.

I'll check som more..

---

### Post by Lunde on 2005-07-19
There are som hard drives that cannot handle DMA like:
    * Western Digital WDC AC11000H, AC22100H, AC32500H, AC33100H, AC31600H - all versions
    * Western Digital WDC AC32100H revision 24.09P07
    * Western Digital WDC AC23200L revision 21.10N21


What's the drive's specifications?

---

### Post by Quest-Master on 2005-07-19
Hmm.. Windows says it's a WDC WD400EB-00CPF0..

Also, I'm planning to get another 256MB RAM but still.. if Windows is performing so fast, why shouldn't Ubuntu? :P

Is the DMA problem Linux only? I'm positive it's enabled on Windows too..

---

### Post by Lunde on 2005-07-19
[QUOTE=Quest-Master]Hmm.. Windows says it's a WDC WD400EB-00CPF0..

Also, I'm planning to get another 256MB RAM but still.. if Windows is performing so fast, why shouldn't Ubuntu? :P

Is the DMA problem Linux only? I'm positive it's enabled on Windows too..[/QUOTE]
 Check this out, do you have any similar problems?
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0209.1/0075.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0209.1/0075.html)

---

### Post by Lunde on 2005-07-19
Some more problems related to your disk type
[http://mail-index.netbsd.org/netbsd-bugs/2001/11/30/0001.html](http://mail-index.netbsd.org/netbsd-bugs/2001/11/30/0001.html)

When did you activate DMA, was it like this before?

---

### Post by Quest-Master on 2005-07-19
I highly doubt it could be corruption, but I'll check on it.. also, DMA on my hard drive has been on since I installed Ubuntu back when it was released.

---

### Post by Lunde on 2005-07-19
Any messages in your /var/log/syslog while starting programs?

---

### Post by Quest-Master on 2005-07-20
Heh, the dates in the syslog are a month old..

---

### Post by Lunde on 2005-07-20
[QUOTE=Quest-Master]Heh, the dates in the syslog are a month old..[/QUOTE]
 And you are on correct time in Ubuntu? What about other logs like messages and kern.log?

---

### Post by Quest-Master on 2005-07-20
[QUOTE=Lunde]And you are on correct time in Ubuntu? What about other logs like messages and kern.log?[/QUOTE]
 
They all end on June 27.. o_o

---

### Post by Lunde on 2005-07-20
[QUOTE=Quest-Master]They all end on June 27.. o_o[/QUOTE]
 Can you post the last output from syslog.. 20-30 lines, not multiple entries of same incidences

---

### Post by Lunde on 2005-07-20
And also what's your result on:
$ sudo hdparm -tT /dev/hdXX 
Where XX is your ubuntu partition

---

