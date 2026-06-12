---
title: "[SOLVED] Change from Gnome Power Mager to KPowersave"
date: 2008-05-31
forum: Desktop Environments
---

### Post by Fred Taka on 2008-05-31
Hi

I spend the last few days trying to disable Gnome Power Manager and start to use Kpowersave. I think had succeed when I learn how to put Kpowersave in the start up list and disable the start up of Gnome Power. But after several minutes of system turn on, the Gnome Power Manager icon show up in the panel. It occur every time I re star the OS. 

How can I disable Gnome Power Manager? Is safe to uninstall that (using Synaptic)? I ask that, because Synaptic will uninstall 2 other programs.

Thanks in advance


PS: My journey from MS Windows to Ubuntu are little difficult but very interesting.

---

### Post by sdennie on 2008-06-01
My first question would be: Why would you want to do that?  I don't know if it's safe to uninstall it or not but, if you are really sure you don't want to use it, the following should prevent it from ever starting but may have other bad side-effects:

```

sudo chmod -rx `which gnome-power-manager`

```

Use at your own risk.

Edit:
To reverse the very crude instructions above, run the same command with "+rx" instead of "-rx".

---

### Post by Fred Taka on 2008-06-02
In fact, I want to disable Gnome power Manager because KPowersave do the same basic job and have several features I like. The most important is to change the power configuration easily between "performance" and "presentation", because is very annoying the turn off of the display back light or even a suspend of system during one of my lectures.

But I do not already get the linux way of think, but if I do something like that in the (RIP) Windows, the system will take sme time trying to execute the file. That is not happen in Linux? There is not other way to disable Gnome Power Manager editing some Operational System option?

---

### Post by sdennie on 2008-06-02
I'm not completely sure what you mean.  Did you try the hack that I posted above?

---

### Post by Fred Taka on 2008-06-04
I try your tip, and in fact, all looks work fine. But in the spirit of "teach a man to fish": Is this approach of disabling read and execution of files a good general formula to stop using an auto-start program? Is this do not result redundant CPU cycles trying to execute the file?

---

### Post by sdennie on 2008-06-04
> **Fred Taka said:**
> I try your tip, and in fact, all looks work fine. But in the spirit of "teach a man to fish": Is this approach of disabling read and execution of files a good general formula to stop using an auto-start program? Is this do not result redundant CPU cycles trying to execute the file?

There are usually more elegant solutions but, removing gnome-power-manager may have other undesirable effects.  The chmod thing is nice because it's very trivial to revert.  Now that you know disabling gnome-power-manager in that way doesn't cause any bad problems, one thing you could do to debug what's causing it to randomly start would be to backup the gnome-power-manager and replace it with a script that prints the name of its parent process to a temporary file.  That may help you find what's causing it to run all the time and lead to a more elegant solution.

---

### Post by Fred Taka on 2008-06-08
Thanks Vor by your help. I will do some homework about the alternative solution that you talk about.

---

