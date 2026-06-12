---
title: "Gnome Panel Freeze"
date: 2007-02-08
forum: Desktop Environments
---

### Post by feed5000 on 2007-02-08
I'm having a problem with my Gnome panels freezing.  Both the top and bottom panels become completely unusable.

I can still use the mouse and keyboard.  I can still select icons on the desktop.  And, oddly enough, I can still bring up the trash via the icon in the lower righthand corner.

Any one else have this problem?  Anyone know what going on?

Also, because when this happen I can no longer use the shutdown menu in the upper righthand corner, I've been using the restart button on my computer's case to get it working again.  Is there a way to logout or restart via keyboard commands, so I wouldn't have to do this?

Thanks.

---

### Post by paparucino on 2007-02-08
> **feed5000 said:**
> I'm having a problem with my Gnome panels freezing.  Both the top and bottom panels become completely unusable.

I can still use the mouse and keyboard.  I can still select icons on the desktop.  And, oddly enough, I can still bring up the trash via the icon in the lower righthand corner.

Any one else have this problem?  Anyone know what going on?


I don't know the cause, but I can suggest you to remove a panel, the bottom one, then add a new one.
Take care of the apps you have on the panel so to restore them.

---

### Post by dannyboy79 on 2007-02-08
yeah, it's never a good idea to use the restart because I don't know if it stops your hdd correctly let along all the services your running etc etc. you would want to run this command from a terminal

sudo shutdown -r +1
this will shutdown everything correctly within 1 minute and will reboot also, if you don't want it to reboot, don't include the -r. also, if you just want to shutdown now, then do
sudo shutdown now

you can read all about in the man pages. man shutdown

good luck

---

### Post by feed5000 on 2007-02-08
Thank you two for the helpful ideas.

I deleted the bottom panel and recreated it. I'll monitor the system over the next few days to see if that worked. Hopefully.

The shutdown command is sure handy. Thanks for the tip! There's definitely been times where I've needed this. I'll check out the man for it soon to learn it. Sometimes, though, after one of these partial freezes I can't figure out how to even get a terminal running. I obviously can't bring in up via the application menu. And alt-f2 won't work to bring up the run application window. So is there another way to use the keyboard to get a terminal that might work? Is there anything like Microsoft's ctrl-alt-del that gives the keyboard power over a system in this state, which could shut it down even without a terminal? Even with the shutdown command, I'm still going to have to resort to the restart button a few times a week.

---

### Post by shareMenaPeace on 2007-02-08
You can try 

```
killall gnome-panel 
```

i had something similar and this fixed it.

---

### Post by dannyboy79 on 2007-02-09
> **shareMenaPeace said:**
> You can try 

```
killall gnome-panel 
```

i had something similar and this fixed it.

yeah but that won't work because he can't even get a terminal  to type that in to. So you could try to kill your x server, that's done by hitting ctrl-alt-backspace. this will kill your x-server session and allow you to relogin I believe. other than that I can't help. I have also been looking for a solution for when my keyboard and mouse freeze up and unfortunately all I can ever do is hit the reset button on the computer case which I believe shuts down the hard drives properly but doesn't properly shut down all the services and programs that are running which can cause problems sometimes.

---

### Post by parrot5 on 2007-02-24
> **shareMenaPeace said:**
> You can try 

```
killall gnome-panel 
```

i had something similar and this fixed it.

I have the same problem as the original poster.  I have set up a keyboard shortcut to bring up the terminal, so have access to the terminal to try your method.  The panels disappear for half a second and then comes right back on, BUT it's still frozen.  

***UPDATE*  Problem solved.**
With my very limited knowledge of Unix, I managed to remember how to view current processes with [FONT="Courier New"]ps aux[/FONT].  Found a few gnome applets that I newly added, so I used [FONT="Courier New"]apt-get remove[/FONT] to uninstall them.  Then used what *shareMenaPeace* suggested above to reload the panel.  Voila!

---

### Post by lviggiano on 2008-06-05
Same problem. 
[http://en.newinstance.it/2008/05/23/gnome-panel-freezes/](http://en.newinstance.it/2008/05/23/gnome-panel-freezes/)

I guess, could it be due to some network timeout set to infinite?

I tried to add a new bottom panel and remove the old one. I'll come back to you to tell if this solved.

Update: 6-Jun-2008
Today gnome panel didn't crash. It was happening one/two times per day. I suppose the problem is fixed. I'll update again on next days.

Update: 9-Jun-2008
Today gnome panel crashed. Solution didn't work for me.

---

### Post by MatthewPlanchard on 2008-07-16
Check [this thread]("http://ubuntuforums.org/showthread.php?p=5401057#post5401057") for another possible solution.

---

