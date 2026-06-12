---
title: "runlevel?"
date: 2005-12-17
forum: Desktop Environments
---

### Post by beijingjj on 2005-12-17
My Ubuntu installation boots into the GUI by default.  I assumed it was set to run level 5 but when I look at /etc/inittab it shows the runlevel as "2"

Has Ubuntu redefined the runlevels?

---

### Post by joshuapurcell on 2005-12-17
This is just how Ubuntu (and Debian as well from what I remember) does it. You could redefine the runlevels if you felt more comfortable running at say level 5 (as Redhat does when running with X server), but it wouldn't change anything with how the computer works.

The runlevels greater than 2 are still there (in fact 0,1, and 6 are still the same as every other Linux system for Ubuntu), but are used only if the user wants to use them for a specific purpose.

The one thing that Redhat uses runlevels for by default that Ubuntu doesn't is for running with or without the X server (runlevel 3 or runlevel 5). Ubuntu does it better in that the window manager is a process that can be turned on or off like any other. It's called gdm, and you can stop, start, restart, etc. while staying in one runlevel. This makes it so that you don't have to start/stop any other process that may be different between runlevels when all you want to do is turn off or restart the desktop. If you wanted to for instance setup runlevel 3 to be like Redhat, you would just make sure /etc/rc3.d looks like /etc/rc2.d, then take out the gdm script link.

---

### Post by beijingjj on 2005-12-18
This is good to know.  I was editing rc5.d scripts all along without knowing any better.  Guess I'll go back to the drawing board with rc2.d

---

### Post by 23meg on 2005-12-18
If you fancy an easy way of tweaking, check out Boot-Up Manager.

[http://ubuntuforums.org/forumdisplay.php?f=75](http://ubuntuforums.org/forumdisplay.php?f=75)

---

### Post by meenfreem on 2005-12-21
I'm totally new when it comes to linux, so here is my runlevel question.

It seems that during a install of a program, my runlevel has been changed, and now it won't start up x automaticly duting start-up. I have to login through terminal and startx by hand... how do I change this back so that x starts automaticly again?

As far as I can see, I am still in runlevel 2 (intitab file says so anyways), so I think I have somehow disabled my GDM. But in sysvconfig it doesn't show up, so I can't adjust it, and in rcconf I didn't see it either.

After running BUM... it seems that GDM is activated (as it does during start up too, it shows the ubuntu logo and all the texts etc), but just before the login screen should come, it switches back to terminal. In BUM-Summary, GDM shows with a red light next to it, this should be green?

Thanks

---

### Post by Kadin2048 on 2005-12-23
[QUOTE=meenfreem]I'm totally new when it comes to linux, so here is my runlevel question.

It seems that during a install of a program, my runlevel has been changed, and now it won't start up x automaticly duting start-up. I have to login through terminal and startx by hand... how do I change this back so that x starts automaticly again?

As far as I can see, I am still in runlevel 2 (intitab file says so anyways), so I think I have somehow disabled my GDM. But in sysvconfig it doesn't show up, so I can't adjust it, and in rcconf I didn't see it either.

After running BUM... it seems that GDM is activated (as it does during start up too, it shows the ubuntu logo and all the texts etc), but just before the login screen should come, it switches back to terminal. In BUM-Summary, GDM shows with a red light next to it, this should be green?

Thanks[/QUOTE]

Sounds like that's not a runlevel question, but more of a "why did this break my GDM install" question. It might be answered better if you asked it that way, or searched for an answer that way. It sounds like GDM is getting started up OK, so your runlevel scripts are fine, it's just getting messed up after that.

---

