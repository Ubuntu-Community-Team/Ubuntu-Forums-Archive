---
title: "Good Linux Timer App"
date: 2005-12-09
forum: General Help
---

### Post by racyrefinedraj on 2005-12-09
Hello everyone,

First let me say hi to the forum, as this is my first post. I recently installed Ubuntu on my laptop, representing my third (and vastly most successful :D  ) attempt at linux. I've already used searching the forum and the wiki for the answers to many, many hang ups, so thank you Ubuntu.

Now for the question. I need a timer. At best, it would do all of the following:

-Be small in terms of resource usage
-Allow me to set a countdown timer in minutes and seconds
-Either display the time elapsed on the Taskbar, Remain "always on top" of all other windows, or both
-Save preset Timer lengths
-Customize the sound that plays when time is up using an MP3 or WAV. 
-Be available through apt-get

anyone know where to get the app I am looking for?

---

### Post by matid on 2005-12-09
[QUOTE=racyrefinedraj]anyone know where to get the app I am looking for?[/QUOTE]
Heven't checked it yet, but maybe you could try **timer-applet**.
It's in repositories.

---

### Post by gonçalo on 2005-12-09
timer-applet does all that except custom sound alarms, the sound is a generic system sound. You can change the sound but's not specific of time-applet affecting other actions too. Unless you, like me, don't have system sounds enabled and then, yes you could change the bongo drum sound for something else.

We do need better sound events management on GNOME.

---

### Post by racyrefinedraj on 2005-12-09
Okay, I got timer-applet installed (via synaptic) but how do I run it? The install didn't add anything to the applications menu, and when I try typing "timer-applet" in a terminal, nothing happens.

For example, this is me checking to make sure it is installed an then trying to run it.
```

ryan@lappy35:~$ sudo apt-get install timer-applet
Password:
Reading package lists... Done
Building dependency tree... Done
timer-applet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
ryan@lappy35:~$ timer-applet
ryan@lappy35:~$ 
```

I kinda feel like an idiot here. what am I doing wrong?

---

### Post by Perfect Storm on 2005-12-09
when installed, right click on the panel and choose **add to panel**.
Now select **timer**

---

### Post by racyrefinedraj on 2005-12-09
Oh wait. I figured it out. It goes in the panel!

shit that's nice. Does everything I want it to. Custom sounds are really not that important anyway. Plus, maybe if I get ambitious I'll write my own panel widget for a timer with custom sounds. 

Anyway, thanks a lot.

---

### Post by racyrefinedraj on 2005-12-09
LOL. Solved while I was writing my post about how it was solved.

---

### Post by dancingdiva on 2007-11-05
Hi! Sorry if this comes off as really stupid...my husband installed and set up Ubuntu a little while ago and I'm just starting to barely mess around with it. Anyway, I'm trying to get this timer-applet to work. I got it installed OK (at least Adept Manager says "installed" now), but when I right click the panel and choose Add Applet, Timer isn't listed there. What did I miss?
Thanks!

---

### Post by MichaëlVD on 2007-11-05
Since you're using Adept, I guess that you are using Kubuntu (with KDE) instead of Ubuntu (with Gnome). The applet referred to above is a Gnome panel applet, and I'm not sure whether it's supposed to work with the KDE panel. Someone else may be able to confirm this.

---

### Post by dancingdiva on 2007-11-05
Oops! I was afraid I would come off like an idiot. :)

Thanks for the tip, though. Do you know offhand of a simple timer app I might be able to run easily on *Kubuntu*?

Thanks again!

---

### Post by MichaëlVD on 2007-11-07
Maybe you could try the suggestion at the end of this blog post?

[http://debaday.debian.net/2007/11/07/timer-applet-a-countdown-timer-applet-for-the-gnome-panel/](http://debaday.debian.net/2007/11/07/timer-applet-a-countdown-timer-applet-for-the-gnome-panel/)

---

