---
title: "Kde wont logout, shutdown or anything, unless its with the command line..."
date: 2010-03-16
forum: Desktop Environments
---

### Post by AndeeeUk on 2010-03-16
Hi,

I am very confused as to what is going on. I have all the applications installed for the shutdown and logout but when i click them, they dont seem to be doing anything?

Any feedback would be great?

Thanks
Andy

---

### Post by matrix14 on 2010-03-16
@AndeeUK:

It seemed likely KDE 4x bugs. It also happen when I try Kubuntu Intrepid Ibex. Some other Kubuntu users also got this trouble. You may report it to Ubuntu Launchpad.

---

### Post by AndeeeUk on 2010-03-16
Hi matrix14,

thanks for the reply. Is there any known fix for this? this is not a minor bug and has been reported by many users, i would hope there is a fix for this somewhere?

Thanks
Andy

---

### Post by t.rei on 2010-03-16
are you on a kubuntu install or have you installed kde to an ubuntu system?

I think there was something about 'what login manager you use' that used to affect these options.

If you are running gdm: try running 'sudo dpkg-reconfigure kdm' in terminal, pick kdm from the menu that shows up and reboot.

---

### Post by matrix14 on 2010-03-16
@t.rei:

I have installed Kubuntu 8.10 on different PC, but than I got such trouble. 2 week's ago I also helped my neighbor to install Kubuntu 9.10, but he then got similar problem.
However, I should have to try what you suggested, in case I don't really expert to use KDE 4.x, as I am using ubuntu 8.04 (gnome) for daily works. THX...

---

### Post by Chame_Wizard on 2010-03-16
@OP Which Kubuntu do you use?

otherwise
```
sudo shutdown -h 0
```

---

### Post by moron on 2010-03-17
This just started happening to me as well sometime Monday, March 15, 2010.  
Running KDE 4.3.2 (according to hel- -> about KDE under Kubuntu 9.10).  It's hard to gauge what exactly triggered it of course as I did not notice the machine had not shut down until the next morning.

The answer above is not a solution, only a temporary workaround.

There are a few bug reports blaming knotify and / or system sounds:

[http://bugs.kde.org/show_bug.cgi?id=201569](http://bugs.kde.org/show_bug.cgi?id=201569)
[http://bugs.kde.org/show_bug.cgi?id=228005](http://bugs.kde.org/show_bug.cgi?id=228005)

The suggested work around for the bug above however did not help me, still looking to find the cause and solution.

Cheers

---

### Post by clappr on 2010-03-18
After hours of fffing around ctrl-alt f12 shutdown my Acer Aspire netbook.  What a pain in the ***.  Kde plasma is awesome, but not practical and usable in its current state.

---

### Post by lykwydchykyn on 2010-03-18
I had this problem and it turned out krunner was locked up.  Apparently commands like shutdown, logout, lock screen, etc are processed through krunner.

You'll know it's this if alt-f2 also does nothing.

My solution was to kill and restart krunner:
```

pkill krunner && krunner &disown

```

What version are you on?  This hasn't happened to me since I upgraded to 4.4.1.

---

