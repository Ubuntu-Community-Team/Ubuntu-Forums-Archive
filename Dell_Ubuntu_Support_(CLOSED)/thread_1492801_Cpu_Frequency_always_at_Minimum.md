---
title: "Cpu Frequency always at Minimum"
date: 2010-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Heero_Yuy_X on 2010-05-25
Hi I have a dell vostro A860 and have recently upgraded to Ubuntu 10.04 Lucid Lynx...
My problem is that the CPU Frequency always remains to the minimum...
My clock options are 1.80GHZ and 1.20GHZ.
Even on AC it remains locked at 1.20GHZ

I tried to change it several times from the CPU applet but it simply stuck there...

Is there any other way to force it to change the frequency ?

---

### Post by dvwolfman on 2010-05-25
There is a way to "Tune your processor" I got a walkthrough on this from a friend, but it can really mess up you system if you do it wrong. If the Gui apps don't do the trick, there is a program available from the debian archives, depending how ambitious you are:

one of them that I know of is command-line and is called cpufreq

[http://www.linux.it/~malattia/wiki/index.php/Cpufreqd]("http://www.linux.it/%7Emalattia/wiki/index.php/Cpufreqd")

don't use it unless you read up on how to first, maybe ask around some more, there may be an easier way, but this may be one way, good luck:)

---

### Post by Heero_Yuy_X on 2010-05-25
Thanks for the quick reply !!!

Well I installed it already but I have no idea how to use it.

Why isn't the CPU Scaling applet not working in the first place ! 
Is there any other way without getting my hands dirty?

I've already messed mine enough for the damn thing to grow arms and eat me alive !!! :)

---

### Post by dvwolfman on 2010-05-25
I think the easier program to use, though it is command line, is 'powernowd' available from the add/remove programs button in ubuntu.
install powernowd
then open a terminal and type 
powernowd --help

you should read that document carefully before actually using the program...

to do what you want to do is risky, and there is a lot involved, if I understand you right, are you trying to optimize your system or overclock it?

You know, I wish I knew more to help, cause I delt with the same thing, but if you don't have a performance problem, I suggest leaving it as is till you get a very clear answer, sorry to waste your time....

this is kinda what it looks like on my Quad core:
it gets messy.

user@user-desktop:~$ sudo powernowd
[sudo] password for user: 
powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
powernowd: Found 4 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1998Mhz - 2331Mhz (2 steps)
powernowd:   cpu1: 1998Mhz - 2331Mhz (2 steps)
powernowd:   cpu2: 1998Mhz - 2331Mhz (2 steps)
powernowd:   cpu3: 1998Mhz - 2331Mhz (2 steps)


I don't know of a gui app that does this...sorry

---

### Post by Marlonsm on 2010-05-25
It's normal for the frequency not to max even if on AC.
It should only max when you actually need it.
Try, for example, looking at the frequency when you're starting OpenOffice. If everything if fine, the clock should go up to the max while it's loading, and then decrease after it's loaded.

---

### Post by dvwolfman on 2010-05-25
however, I have a far less destructive idea for you, there is a gui app that controls power managment profiles, I think it affects the setting you want to change...it was like a year ago I delt w/ this so bear with me...


ok have a look at the summary of this program, as I recall it is point and click and allows you to change your power management settings, along with the cpu freq setting:
this is one solution that won't hurt so much:

here is the link to the installer, but maybe just do it from add/remove programs, xfce4-power-manager


[http://apt.ubuntu.com/p/xfce4-power-manager](http://apt.ubuntu.com/p/xfce4-power-manager)

I know this solved alot for me, but it's been a while, the simplest solution is probably the best...

---

### Post by dvwolfman on 2010-05-25
> **Marlonsm said:**
> It's normal for the frequency not to max even if on AC.
It should only max when you actually need it.
Try, for example, looking at the frequency when you're starting OpenOffice. If everything if fine, the clock should go up to the max while it's loading, and then decrease after it's loaded.

good point, sorry to confuse anyone with my take on the issue, this sounds right :)

---

### Post by wilee-nilee on 2010-05-25
Run the live cd and see if the applet doesn't work while using it. This will give you a a clue as to maybe a reinstall may be a better idea then breaking your setup and losing stuff that you can't lose.

I have noticed with Lucid that the panel applets have anomalies and sometimes I have to reload or restart x to get them to work. Have you just deleted the applet not working and put in another to see if it does.

---

### Post by Heero_Yuy_X on 2010-05-26
Wiliee-Nileee you were right !!!

I changed the Profile to "Performance" in the CPU Applet and reset the laptop by accident, when I got back in Ubuntu it actually stayed at 1.80 GHZ !!! :)

I think it's a bug of some sort, back in Karmic I used to switch between frequencies with no restart all the time. Well it's better than nothing !

I'll try deleting the applet and creating a new one to see if it works too !

Thanks alot for the help guys ! Much appreciated ! :KS

---

