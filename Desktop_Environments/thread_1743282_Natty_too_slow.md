---
title: "Natty too slow"
date: 2011-04-29
forum: Desktop Environments
---

### Post by thinhhoang on 2011-04-29
Hi there, I've just upgraded from Kubuntu 10.10 to Kubuntu 11.04 Natty. Natty's responsiveness was pretty slow, much that I had to wait for few seconds even when clicking "Kick off". Has anyone experienced this before? I've never had trouble running Kubuntu 10.10.

---

### Post by dabl on 2011-04-29
11.04 should not run significantly slower than 10.10.  Can you open a Konsole terminal, and enter ```
top
```

What process is consuming a lot of CPU resources?

---

### Post by stwilliams on 2011-04-29
So, I'm also experiencing this incredible 'lag' in response to everything I do.  Typing, opening applications or folders, EVERYTHING is moving slowly, but I typed in the 'Top' command and it says that 'Kwin' is taking up about 90% of my CPU usage?  I'm pretty new to Linux and not really sure what Kwin is or what might be using it.

This is, by the way, using the recently updated 11.04.

---

### Post by Xanthomryr on 2011-04-29
Kwin is a window manager and part of KDE.

[http://en.wikipedia.org/wiki/KWin](http://en.wikipedia.org/wiki/KWin)

---

### Post by stwilliams on 2011-04-29
But 90%+ is a lot of CPU usage,  I can't do anything, is that normal?  I mean, I can do stuff, but there's a delay in everything.  It wasn't doing this before I installed 11.04 last night.  I've been running 10.10 just fine.  The mouse movement is behind, The typing, everything's slow and choppy.

---

### Post by Asraniel on 2011-04-29
i guess its a GPU driver problem.

As a first step, try to deactivate the effects in kwin. Then try to figure out what went wrong with your GPU drivers.

What gpu du you use?

---

### Post by stwilliams on 2011-04-29
I'm afraid I don't know what a GPU is either :/
Please bare with me.

---

### Post by ivanovnegro on 2011-04-29
Running here a fresh install of Kubuntu 11.04, it runs smooth and very fast also with KWin, Kwin consumes normally my resources, I think it has to be the GPU driver.
Maybe try if not yet a fresh install of Kubuntu Natty to see if the problem still remains, upgrades can sometimes cause this.
The GPU is a part of your graphics card, maybe you use a proprietary graphics card and need to install addional drivers for it to take full advantage of it.

---

### Post by stwilliams on 2011-04-29
I ran a program cleverly titled Additional Drivers; it did a search and says specifically 'No proprietary drivers are in use on this system'.

I also JUST upgraded this per the prompt that came up last night.  It's as fresh as it gets as far as I know.

What's my next move?

---

### Post by ivanovnegro on 2011-04-29
> **stwilliams said:**
> I ran a program cleverly titled Additional Drivers; it did a search and says specifically 'No proprietary drivers are in use on this system'.

I also JUST upgraded this per the prompt that came up last night.  It's as fresh as it gets as far as I know.

What's my next move?

No it wasnt a fresh install, it was an upgrade. A fresh install is a new install from  a CD if you select install Kubuntu 11.04. What you did was an upgrade via the Update Manager as far as I have understood you.
What are your hardware specs btw, maybe your machine is not anymore enough powerful for the full blown KDE?
You need at least 1 GB of RAM to use Kubuntu Natty without glitches.
[Here]("https://wiki.kubuntu.org/NattyNarwhal/ReleaseNotes?#Known%20Issues") some important documentation.

---

### Post by dabl on 2011-04-29
> **stwilliams said:**
>  I'm pretty new to Linux and not really sure what Kwin is or what might be using it.



"K" menu > System Settings > Desktop Effects and disable desktop effects.  That should reduce the kwin usage of CPU resources -- check with top.

---

### Post by stwilliams on 2011-04-29
First of all, PERFECT.  I just needed to disable desktop effects.  

However, pertaining to the prior suggestion, I don't know my system specs very well.  
Is there a command I can type in Kernel that would list them?  I've found that most of my problems require @ some point my knowledge of these things, and I'm not sure of what they are...

---

### Post by ivanovnegro on 2011-04-29
> **stwilliams said:**
> First of all, PERFECT.  I just needed to disable desktop effects.  

However, pertaining to the prior suggestion, I don't know my system specs very well.  
Is there a command I can type in Kernel that would list them?  I've found that most of my problems require @ some point my knowledge of these things, and I'm not sure of what they are...

Its easy to find out your specs. Go to the Kick Off Menu-> Applications-> System-> System Info. There you will find all your hardware specs.

---

### Post by dabl on 2011-04-29
Right.  Or you can install hardinfo.

```
sudo apt-get update && sudo apt-get install hardinfo
```

then you can see most of the hardware information in hardinfo.

---

### Post by thinhhoang on 2011-04-29
I'm currently using INTEL GMA 900 (Chipset 915).

---

### Post by ivanovnegro on 2011-04-29
> **thinhhoang said:**
> I'm currently using INTEL GMA 900 (Chipset 915).

Maybe try also to disable the effects.
There are some issues with some effects and Intel cards. For example with my Intel card I have no Blur but everything else works perfectly.

---

### Post by thinhhoang on 2011-04-30
Thanks a lot. Kubuntu works a lot better right now. But one thing that I couldn't understand is why Kubuntu 11.04 is much slower than Kubuntu 10.10, which I installed KDE 4.6.2 from BackPorts too.

---

### Post by thinhhoang on 2011-04-30
> **dabl said:**
> 11.04 should not run significantly slower than 10.10.  Can you open a Konsole terminal, and enter ```
top
```

What process is consuming a lot of CPU resources?

KWin is the one. When Desktop Effects are active, KWin eats up to 90~95% of CPU resources.

---

### Post by Henns Wörst on 2011-04-30
I had exactly the same issue on my Samsung Netbook with intel-graphics. I fixed it by updating the graphics drivers from this *experminental*-ppa :[https://edge.launchpad.net/~xorg-edgers]("https://edge.launchpad.net/%7Exorg-edgers") . After adding the ppa I made a dist-upgrade and now everything is fine. Since this is an experimental ppa, be careful though.

---

### Post by ivanovnegro on 2011-04-30
I forgot to mention, if someone has speed problems with the effects, you could also choose in the settings for the effects to be fast, by default its on normal. 
Enable fast and it will run like a rocket. (System Settings-> Effects-> Speed of animations)

---

### Post by labatts on 2011-05-06
I am getting similar results on a true fresh install.  The update manager did run a few updates after the install, and I have no idea if the problem existed prior to this.  An example is configuring ANY applet on the panel locks the system up.  It eventually gets there, but I can literally vacuum the house while it works.  I turned off desktop effects, and this seems to solve the issues for everyday stuff.

However, running simple games such as Kapman or kblocks still does the same thing, rendering the games unplayable (hardly graphics intensive).  "top" in konsole showed Kapman eating 90% of CPU, so it seems like the same problem.

Point being, fresh install vs upgrade does not seem to matter.  (asus 1005ha netbook, for the record).

---

### Post by ivanovnegro on 2011-05-06
> **labatts said:**
> I am getting similar results on a true fresh install.  The update manager did run a few updates after the install, and I have no idea if the problem existed prior to this.  An example is configuring ANY applet on the panel locks the system up.  It eventually gets there, but I can literally vacuum the house while it works.  I turned off desktop effects, and this seems to solve the issues for everyday stuff.

However, running simple games such as Kapman or kblocks still does the same thing, rendering the games unplayable (hardly graphics intensive).  "top" in konsole showed Kapman eating 90% of CPU, so it seems like the same problem.

Point being, fresh install vs upgrade does not seem to matter.  (asus 1005ha netbook, for the record).

Is Kapman a Flash game on a website?
If so, it would not surprise me.

Edit: Ok, I saw its a KDE game, not sure, I dont use it, could be really a graphics issue in your case.

---

### Post by labatts on 2011-05-06
> **ivanovnegro said:**
> Is Kapman a Flash game on a website?
If so, it would not surprise me.

Edit: Ok, I saw its a KDE game, not sure, I dont use it, could be really a graphics issue in your case.

Its odd.  I ran the same apps in 10.10 no problem.  Thankfully its not a deal breaker since it is only a timewaster game.  libreoffice, etc work fine.  I wish I knew if it did that before I did the updates. =/

---

### Post by labatts on 2011-05-07
Okay, so there are two different issues here (although, I am sure they are related): 1. desktop effects run too slow.  2. certain games that are not very graphiic intensive are running slow.

I found a "fix" for the first issue.   If you uncheck the "blur" effect in the desktop effects settings, everything suddenly works fine.  (no idea why, but whatever).

The games are still running slow - so slow that they are unplayable.  An example is Kapman.  Like I said, not a deal breaker but I would certainly like a fix.  Also, I am worried that it might effect other things such as presentations (I have not been able to test that yet).

Any help is appreciated.

---

### Post by labatts on 2011-05-07
OKAY... any kde game that has an egyptian theme can be changed to a different theme.  THen it works fine.  (sheesh).

---

### Post by ivanovnegro on 2011-05-07
> **labatts said:**
> Okay, so there are two different issues here (although, I am sure they are related): 1. desktop effects run too slow.  2. certain games that are not very graphiic intensive are running slow.

I found a "fix" for the first issue.   If you uncheck the "blur" effect in the desktop effects settings, everything suddenly works fine.  (no idea why, but whatever).

The games are still running slow - so slow that they are unplayable.  An example is Kapman.  Like I said, not a deal breaker but I would certainly like a fix.  Also, I am worried that it might effect other things such as presentations (I have not been able to test that yet).

Any help is appreciated.

Blur is known as problematic at the moment for some graphics card, mine included, the only effect that doesnt work on my machine with Intel integrated. but funny is, its enabled, I did not bother me to shut it off even that it is not working.

---

### Post by thinhhoang on 2011-05-26
You're right ivanovnegro. Blur kills most of intel based systems. I've just reinstalled a fresh install of Kubuntu 11.04, also updated to KDE 4.6.3, but the problem still exists.

---

### Post by ivanovnegro on 2011-05-26
> **thinhhoang said:**
> You're right ivanovnegro. Blur kills most of intel based systems. I've just reinstalled a fresh install of Kubuntu 11.04, also updated to KDE 4.6.3, but the problem still exists.

Just disable Blur, maybe that helps.

---

### Post by thinhhoang on 2011-06-04
I got this when "kwin --replace":
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4). 
I don't know what this mean, anyone can help,please?

---

### Post by thinhhoang on 2011-06-04
Never mind! I downgraded Mesa to 7.9 and blur now comes alive! :popcorn:

---

