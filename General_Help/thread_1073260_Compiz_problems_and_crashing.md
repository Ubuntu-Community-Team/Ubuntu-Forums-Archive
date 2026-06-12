---
title: "Compiz problems and crashing"
date: 2009-02-18
forum: General Help
---

### Post by tehnowhereman on 2009-02-18
I'm fairly new to Linux (since October?) but in the past 3 weeks several problems have shown up.

I haven't upgraded to the latest Ubuntu version, so I'm on the one prior. Compiz has always worked fine, theo ne fine day for apparently no reason evertime I start up the computer it tells me the screen is not composited and to run compiz-fusion or another manager. I click OK, and here's the thing, Compiz starts up normally. No manual start up needed.

In the past 2 weeks the next problem began: Freezing. The screen will look normal and then it just freezes up, everything is unresponsive and you're left looking at what you were just doing. It does this every few hours. In fact it did it WHILE I was typing this message and it does not do it when I boot into XP.

If I leave my laptop on with Linux running, I'll come back from class and it will have froze, the same does not occur when running XP.

---

### Post by tehnowhereman on 2009-02-18
Why

---

### Post by grndslm on 2009-02-18
Because it's not stable.

Try deleting your .compiz/ config file... or it might be .config/compiz/

Can't remember, as I stopped using Compiz when I realized I'd never be able to get work done with it.  It has a ton of usability features, but it's not stable whatsoever.

---

### Post by smo0th on 2009-02-18
I've been using compiz-fusion for about a year now and I had no problems besides missing frames which gets easily fixed by a single terminal line, however in your case I would recommend reinstalling compiz by completely removing it and making a clean install with the latest version which should be more stable.

---

### Post by user-max on 2009-02-19
uninstall / install fresh seems to be the right thing to do. Many people, including myself are using compiz trouble free. 

To uninstall compiz follow this thread:

[http://ubuntuforums.org/showthread.php?t=488342](http://ubuntuforums.org/showthread.php?t=488342)

to install it fresh:

[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)

you may skip emerald part I believe, unless you would like to experiment with that window manager as well.

just remember TO ALWAYS ALLOW SYNAPTIC TO INSTALL DEPENDENCIES

---

### Post by grndslm on 2009-02-20
sudo aptitude purge compiz; sudo aptitude install compiz

should do the trick if the program is the problem.. but it's more likely your config files, which is why I said start fresh by removing your config files

rm -r .compiz/ -OR- is it rm -r .config/compiz/

*I haven't been able to use compiz for more than a day with the settings I make.  Something in it borks and I have to go back to metacity.  =-(

---

### Post by radio_listener on 2009-02-20
Your problems might be related to a hardware error in the 3D-part of your videocard.
Windows XP doesn't use a 3D-desktop so this problem wouldn't show using only the desktop and 2D-application. Do you have 3D applications installed under Windows to test if there are problems with 3D, too?

I had problems with the following bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311)
It might be not that relevant to you but in the comments someone said that one has to delete settings made by compiz in the gconf-framework.
The easiest solution might be to delete per 'rm -r /home/USER/.gconf/apps/compiz'. After that Compiz should use the standard settings.

---

