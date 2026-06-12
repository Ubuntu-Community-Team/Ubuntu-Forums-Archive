---
title: "Linux's &quot;ctrl+alt+delete&quot; equivalent"
date: 2009-04-12
forum: General Help
---

### Post by photoncrusader on 2009-04-12
I've been having trouble with applications freezing the system. I can not access the terminal to cancel a process either. I just migrated from windows and was wondering if there is a Linux equivalent to the "ctrl+alt+delete" command? Thanks.

---

### Post by Thedjatclubrock on 2009-04-12
Not exactly, but you can add the gnome force quit applet to the gnome-panel, or you can ```
 Alt-F2 killall <processname>. 
```

If you need to kill everything in your session, you can ctrl-alt-backspace.

---

### Post by benj1 on 2009-04-12
theres a force quit applet or system monitor if your mouse is still responding

---

### Post by alunw77 on 2009-07-28
> **benj1 said:**
> theres a force quit applet or system monitor if your mouse is still responding

Where do I find this? (sorry, an absolute beginner (I had actually searched on "ctrl-alt-delete" - looking for an equivalent))

---

### Post by philcamlin on 2009-07-28
system > administration > system monitor :popcorn:

---

### Post by alunw77 on 2009-07-28
Thanks, Phil. Is this the same as the 'force quit' applet, or is that somewhere else?

---

### Post by issih on 2009-07-28
The force quit applet is in the list if you right click on a panel and select "add to panel"

Hope that helps

---

### Post by PurposeOfReason on 2009-07-28
> **alunw77 said:**
> Thanks, Phil. Is this the same as the 'force quit' applet, or is that somewhere else?
For that, right click the panel, choose add applet, and look for force quit.

---

### Post by speedwell68 on 2009-07-28
> **Thedjatclubrock said:**
> 

If you need to kill everything in your session, you can ctrl-alt-backspace.

That has been disabled by default in 9.04.

---

### Post by Zorael on 2009-07-28
There is a **dontzap** package in the repositories which will let you enable zapping (ctrl+alt+backspace), though I remember seeing some threads about it not working for everyone?
```
$ sudo dontzap --disable
```
Double negative; disabling don't zap = zap enabled.

If you have some terminal knowhow, you only really want to zap (or otherwise restart X) if X itself is in a loop. In other cases where you can't take care of it from within X, hop to a terminal with ctrl+alt+f1, log in, and then check running processes via **top**. (**Q** quits)

[img]http://www.cyberciti.biz/nixcraft/vivek/blogger/uploaded_images/linux-cpu-utilization-780043.png[/img]

If it says CPU 98.9% on firefox-bin or whatnot, then kill that process and hop back to X with ctrl+alt+f7.
```
$ killall **[COLOR="SeaGreen"]firefox-bin[/COLOR]**
```
Caveat; **killall** will - as its name implies - kill all processes with that name (**[COLOR="SeaGreen"]firefox-bin[/COLOR]** in this example), so if you have several instances of it running - which doesn't translate to several windows of it running - it will kill all of them. The "proper" way is to note the process id (PID) of the process in top, and then kill it via **kill** instead of **killall**.
```
$ kill [COLOR="SeaGreen"]**4421**[/COLOR]
```
Now, those commands ask the process nicely to *terminate* (SIGTERM).
> Two signals can be used to stop a process, SIGTERM and SIGKILL. SIGTERM is the polite way to kill a process; the process can catch the signal, realize that you want it to shut down, close any log files it may have open, and generally finish whatever it is doing at the time before shutting down. In some cases a process may even ignore SIGTERM if it is in the middle of some task that can not be interrupted.

SIGKILL can not be ignored by a process. This is the “I do not care what you are doing, stop right now” signal. If you send SIGKILL to a process then [Linux] will stop that process there and then.
[SIZE="1"][(source)](http://www.freebsd.org/doc/en/books/handbook/basics-daemons.html)[/SIZE]

So in some cases the process will be so borked that it won't listen to SIGTERM. If that's the case, just add the **[COLOR="Red"]-9[/COLOR]** argument to those calls to make it send SIGKILL instead.
```
$ kill **[COLOR="Red"]-9[/COLOR] [COLOR="SeaGreen"]4421[/COLOR]**
$ killall **[COLOR="Red"]-9[/COLOR] [COLOR="SeaGreen"]firefox-bin[/COLOR]**
```


And if, at the end of the day you *can't* do *anything* and in frustration you're reaching for the power/reset button, ***stop***. Go [raise skinny elephants](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html).

---

### Post by ram2008 on 2009-08-23
The ctrl+alt+backspace function can be re-enabled by installing the dontzap app with the Synaptic Package Manager and then, in a terminal, enter the following: sudo dontzap --disable.  That works great for me.  I was very disappointed to see the function disabled in 9.04.

---

### Post by scouser73 on 2009-08-23
The key combination of **ALT, PrtScreen, K** workd just as well.

---

