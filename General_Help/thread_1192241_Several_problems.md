---
title: "Several problems"
date: 2009-06-19
forum: General Help
---

### Post by Darkpriest667 on 2009-06-19
Hello,


  This is my first post on the ubuntu forums so please forgive me.

I'd like to preface this by saying I am not a novice CPU user.  I have had a computer with internet access since 1990 when I was 9 years old.  Which gives me almost 20 years of computer usage (successful and non-successful.)  My first experiences with errors and configurations started mostly without the help of those on the internet.  Running Dos and then later windows 3.1 and 3.11 and on and on until XP professional.   I have finally been converted to the ubuntu way.   While the learning curve is a little steep at my age I am trying my hardest.   So far I like a lot of features ubuntu has to offer.  However, I am experiencing several problems that may have come from my fiddling with it or may not.



I am running ubuntu 9.04 with only winehq as an added feature. i have 100GB of my 500 GB sata partitioned to ubuntu and the other 400 partitioned to windows xp



1.  error x080040708  


Description unable to create required engine components, check whether you have appropriate priveleges to create com components.

Setup will not terminate.

I get this when running winehq 1.1.24

my first installation worked fine.. but then ubuntu needed to restart for upgrades that it had downloaded... It has not worked since.  I also cannot uninstall the game for the same reason.

2.

Now it seems anytime i have an application open if i dont stay in that application for more than 5 seconds it dissapears and i can never get it back again.   Its not anywhere that i can find and i have to reopen the program. And lose all my saved application


Any help would be greatly appreciated

---

### Post by Darkpriest667 on 2009-06-20
still no answer... hoping one of you experts has the information i need..


Thankyou

---

### Post by JoePublic9 on 2009-06-21
If you mean that wine has failed to work after your update then it may be because, if I am not mistaken, there was a kernel update yesterday. Sometimes that will bork up some apps.
  I am also a new user here so I very well could be mistaken. I would troll the wine website and see if there are issues with the new kernel.
  Sorry I can't be of more help.
            Joe

---

### Post by sedawk on 2009-06-21
I recommend to use command line because that will (often) show additional
error messages:

E.g lets assume you want to play the latest Plants vs. Zombies Demo
(28 MB download, works fine here with Ubuntu and Wine).
After downloading a command line session goes like this:
```

# Install demo in isolated wine directory
export WINEPREFIX=~/wine_demo_plants
# run config once to create directory structure
# (set virtual desktop to 800x600 if you like)
wine winecfg
cp <downloaded_exe> ~/wine_emo_plants/drive_c/
wine winefile
# now on c: you see the exe click it. Two small errors during
# installation. But the demo works fine.

```

If your wine installation is completely messed up this should
not have worked. So if there was any error. When did it happen?
What was the error message?

---

### Post by 3rdalbum on 2009-06-21
I'm sorry, you're not giving us enough information.

What program are you trying to install with Wine? If you had the program already installed in Wine before doing any Ubuntu updates, it will still be there - Windows programs reside in your home directory, not in the main filesystem. Also be aware that Wine does not work with the majority of Windows programs - it's the nature of the beast.

With your second problem, are you referring to Linux programs or to Windows programs? What are the names of the programs that exhibit this behaviour?

---

### Post by slyzen on 2009-06-22
Hi,

I got the same error yesterday when I launched the google Sketchup 6 install. I'm running wine v 1.1.23 on Kubuntu jaunty. I updated my system with last updates and now it works fine !

sly

---

### Post by Darkpriest667 on 2009-06-27
> **3rdalbum said:**
> I'm sorry, you're not giving us enough information.

What program are you trying to install with Wine? If you had the program already installed in Wine before doing any Ubuntu updates, it will still be there - Windows programs reside in your home directory, not in the main filesystem. Also be aware that Wine does not work with the majority of Windows programs - it's the nature of the beast.

With your second problem, are you referring to Linux programs or to Windows programs? What are the names of the programs that exhibit this behaviour?


all programs are exhibiting this behavior skype firefox any program that is open if it is not clicked within 25 seconds to a minute it dissapears... these are not windows programs these are linux programs....


also the wine thing... I have yet to look into that further as I want the basic GUI to work correctly before i tinker around with wine again.. It may have been install error on my part... (totally possible) but im more interested in getting basic linux programs to not go away if i walk away to pee.

---

