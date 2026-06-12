---
title: "system locks up after some time"
date: 2009-02-07
forum: General Help
---

### Post by broekskw on 2009-02-07
morning everyone, this one computer that i have keeps locking up on me , some time right away after it boots up and other times later on after boot up.when it dose i have no control over it, the only way to get out is to pull the power cable or ctrl+alt+backspace then it goes to a black screen with a bunch of commands looks like it is trying to access the system but with no luck.some of the time i am playing music and playing games at the same time and when it locks up all i hear is a loud screeching noise from the music, other times i click on firefox and that locks it up. i am using 8.04 ubuntu and all is updated have been using this for some time without and lockups or crashes until now.

is there a way to log onto my system so that next time it locks up i can get a report so i can post here so all here can look at :popcorn:

thanks in advance for any feed back:lolflag:

---

### Post by taurus on 2009-02-07
Sounds to me like it could be either a bad video card or a faulty memory--RAM.

---

### Post by broekskw on 2009-02-07
Thanks taurus for you quick reply, forgot to mention that this is a dual boot with xp also on it on a diff h/drive.i did have 768mb of memory but both stick must of been diff because i had problems with the system very slow or other problems (can not remember what) so i took out the 256mb stick and then every thing ran ok, this was some time ago.

---

### Post by LoonyLeif on 2009-02-07
This same thing is happening to me. I haven't tried control+alt+backspace (Windows user here, go easy on me). But yes this happens when I've been leaving my computer idle for a while, or when I'm using Firefox.

I have a Dell Dimension 3000 desktop with integrated graphics (Intel, 82865G) 

What logs can I pull and look at that would help diagnose my issue? Also, what can I do as the problem is occuring (frozen screen) that might help me "escape" to a command prompt, if possible?

Also as a side note what the hell does Windows+R do? I'm used to using that for Start > Run shortcuts in Windows XP but it seems like the Ubuntu community is playing a trick on me.  Haha.... M-m-magnification!

---

### Post by HermanAB on 2009-02-07
Hardware issues are hard to find.  It helps if you have a junk box full of spare parts to exchange.  Random freezes are frequently caused by bad power quality, either due to a bad PSU or due to a motherboard capacitor problem.  You need to do a divide an conquer exercise to find hardware faults.  

For example, start by removing/unplugging everything that isn't absolutely essential to operation.  Leave one memory stick, one HDD and use the on-board video if it has it.  Run it for a few days to see if it is stable, now add one thing at a time until it phucks up and then you know.

Note that it may even be the keyboard!  The keyboard sits on the 5V power and can cause the machine to screw up.

Once you have the machine open, take a good look at all the electrolytic capacitors.  Their tops should be flat and there should be no brown goop bubbling out of them. If you find distended capacitors, then you need a good quality temperature controlled soldering iron and a lot of patience to replace them.

Cheers,

Herman

---

### Post by many_boomers on 2009-05-03
Same Dell dimension, with two identical sticks of 1gb ddr2 ram, bios rev3, 160gb hdd p4 3.2ghz. Very similar problem on ubuntu studio 8.04 when my system hangs, the display fritz's out and displays a checkerboard pattern. Weird.

no bum capacitors, and does the same thing about as frequently (2-5 times a week) if I take out a ram stick and disconnect the CDR drive. It does however have a wussy little 250w power supply.:confused:

---

