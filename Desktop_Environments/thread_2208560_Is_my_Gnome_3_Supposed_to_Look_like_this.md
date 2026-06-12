---
title: "Is my Gnome 3 Supposed to Look like this?"
date: 2014-02-28
forum: Desktop Environments
---

### Post by kurtcolwell on 2014-02-28
Is my gnome supposed to look like this?

1.
[IMG]http://i.stack.imgur.com/jj7Cr.png[/IMG][CENTER]
My Buttons Dont show up
[/CENTER]

2.
[IMG]http://i.stack.imgur.com/CSi3A.jpg[/IMG]
[CENTER]
Same Thing!






What is wrong with my gnome 3.10?
[/CENTER]

---

### Post by grahammechanical on 2014-03-01
What do you think is wrong? The style of the User Interface? It looks typical for Gnome 3 shell as far as I can see. Or do you mean the grey effect? Yes, it is supposed to look like that. The dialog box has all the focus of attention from the OS. It is a visual indication from the OS.

You see something similar in the fourth image on this Gnome web page.

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

Regards.

---

### Post by sammiev on 2014-03-01
I see what they are talking about now, there is no buttons in the menus. See attached.

---

### Post by badbodh-yahoo on 2014-03-01
ubuntu isn't exactly gnome3 friendly distro due to conflicts between unity and gnome-shell.

firstly it is a bad idea to install both on the same installation. there are known problems with multiple desktop environments on the same system like gnome-cinnamon, gnome-unity pairs. _remove unity/cinnamon if it is there_ . i never tried other combos like kde-lxde, xfce-gnome etc. so feel free to burn the clock trying those ;) , see if issues pop up.

secondly, ubuntu probably patches its packages to gel with unity, so gnome3 tends to struggle. try a fresh install of [http://ubuntugnome.org/](http://ubuntugnome.org/) and see if your problem persists. do note that it is heavily patched gnome-shell so don't expect lot of stability. if it crashes, just open tty shell and reboot

thirdly, ubuntu currently supports upto 3.8. so you have added extra ppa-s to get gnome 3.10. bugs like those are expected since these ppa-s are experimental.


now if you are hell bent on using gnome 3.10 as your primary desktop environment i would suggest to try opensuse 13.1 . it is long term support (3 years minimum) and rock solid.
i have used ubuntu for years, but i hate unity and gnome-shell isn't helping either. it is a good idea to settle down on opensuse . do note that there is a learning curve to it, unlike ubuntu.

---

### Post by ibjsb4 on 2014-03-02
> ubuntu isn't exactly gnome3 friendly

Unity, Gnome-shell, Classic are all built on gnome3.

> firstly it is a bad idea to install both on the same installation

But its in the software center for us to install on same installation.

---

### Post by buzzingrobot on 2014-03-02
> **badbodh-yahoo said:**
> ubuntu isn't exactly gnome3 friendly distro due to conflicts between unity and gnome-shell.



Gnome works well here, whether installed on Unity or via Ubuntu Gnome.

The 14.04 release of Ubuntu Gnome, in April, will run Gnome 3.10. (The alpha is rather nice right now.) The OP's screen caps show the standard Gnome 3.10 look. Gnome running Adwaita (the default theme) looks the same everywhere unless a distro specifically alters something.

---

### Post by badbodh-yahoo on 2014-03-02
yup fingers crossed for the LTS release. 

@ ibjsb4 and buzzingrobot

so far my gnome3 experience on ubuntu has been pretty crappy and buggy. last time i tried parallel unity/gnome-shell was back in 12.10 or .04 i think. had to migrate to other options to get my work done. sleep/hibernate/resume were erratic , default applications kept resetting. not to mention frequent shell-crashes and general sluggishness . even unity is sluggish on my old laptop. used xubuntu for most of the previous year. good to know you had better luck.

try gnome-shell on fedora or suse and you will instantly notice the difference. crashless and snappy.

hoping LTS to change that. all the best to ubuntuGnome team.

@ ibjsb4

ubuntu's isn't the most reliable repo among major distros. i have been using it since 8.04, and updates have broken my system on multiple occassions. especially kernel upgrades. don't assume everything in software center is peach, always keep a backup before you start playing :D (software-center ! what kind of ubuntu-head does not use synaptic ?? just kidding ! m old school)


**and back to kurt's problem**, before removing unity etc., also try this once: create a separate root password and convert your user account from 'admin' to 'standard'. reboot and check. just a hunch.

---

### Post by ibjsb4 on 2014-03-02
> buntu's isn't the most reliable repo among major distros. i have been using it since 8.04, and updates have broken my system on multiple occassions. especially kernel upgrades. don't assume everything in software center is peach, always keep a backup before you start playing (software-center ! what kind of ubuntu-head does not use synaptic ?? just kidding ! m old school)

Hummm :-k
Been using ubuntu myself since 8o4.  I don't have the software-center installed; I am also old school :)

And back to kurt :D

---

### Post by buzzingrobot on 2014-03-02
> **badbodh-yahoo said:**
> 

so far my gnome3 experience on ubuntu has been pretty crappy and buggy. 

Not at all like my experience.  The stock Ubuntu Gnome 3.8 release, or the equivalent install on Unity 13.10, was solid and reliable here. Unity, compiz, etc., do not run under Gnome (so I don't really understand the need to uninstall it).  The conflicts you saw did not happen here. When I install another DE on Unity, I do  routinely edit the Startup Applications to eliminate any duplications that appear.  E.g., it's easy to have two power managers or two screensavers launched at startup. I just disable the ones I don't want to run.

Many people seem to install Gnome on Ubuntu incorrectly or add PPA's that bring in untested packages. (Too many web sites and blogs have cut-and-paste instructions for updating Ubuntu Gnome 3.8 to Gnome 3.10 that add those PPA's without warning people.  If users visit the PPA's actual page on LaunchPad, the warnings are very evident.)

 > ...my old laptop

That might be the problem. ;)

> try gnome-shell on fedora...

I have, extensively. F20 is a very solid release, and was solid even in its alpha days.  But here, on my hardware, so was the current Ubuntu Gnome.

F20 is a 3.10 release, while Ubuntu Gnome is 3.8.  Ubuntu Gnome's release cycle is also out-of-sync with Gnome's, while Fedora's, unsurprisingly, is very much in sync with it.  That accounts for Ubuntu Gnome usually being, more or less, a version behind the current Gnome release, and for the mix and match of package versions that results as the devs populate the staging and testing PPA's.
 

(Meanwhile, at the moment I'm on 14.04 running Mate (from the Mate repos except for the newer packages that have made their way to the Ubuntu repos) plus the MintMenu and themes purloined from the Mint repo. So far -- two days -- it's  been fine.  I'll stay with until it breaks, which will surely happen as Ubuntu moves toward the 14.04 release and Mate releases its new version, probably later this month.)

---

### Post by Jake_Paine on 2014-03-04
I much prefer Gnome over Unity and with 13.10 of Ubuntu Gnome for me its been pretty darn solid, might you I'm not using any 3rd party 3.10 Gnome PPAs. Really impressed.

I'll agree Fedora is always way more stable but the lack of unrestricted packages and being so used to Ubuntu prevents me from switching.

OP: Did you resolve this in the end?

---

### Post by monkeybrain20122 on 2014-03-04
> **buzzingrobot said:**
> 
I have, extensively. F20 is a very solid release, and was solid even in its alpha days.  But here, on my hardware, so was the current Ubuntu Gnome.



Fedora was solid even in Alpha days?? Are you serious? 

 Typing from Fedora 20 right now.

BTW, there isn't even a logout button on fedora's vanilla gnome without some tweaks, so sure OP's problem won't arise in a way. :)

**Edited:** Crap. Shortly after writing this post did a Fedora update and now system won't boot. Must be punished by the Fedora God. Now back to the Ubuntu partition.

---

### Post by monkeybrain20122 on 2014-03-05
> **Jake_Paine said:**
> 

I'll agree Fedora is always way more stable but the lack of unrestricted packages and being so used to Ubuntu prevents me from switching.



HAHAHAHAHA!!!! Well Ubuntu may not be the most stable but next to Fedora it is rock solid. I have been dual booting for a while and I can tell you there are so many times I curse at Fedora (like now, have been trying to boot for more than an hour, just a normal yum upgrade and I am toasted) I can't count how many times I have to reinstall Fedora, but never  Ubuntu except when I screw it up myself.On Ubuntu I am playing a bit fast and loose sometimes but on Fedora I stick to pretty standard installation and upgrades, I take more risks in Ubuntu, but guess what, Ubuntu is still a lot more stable, reliable and problem free comparing to Fedora. I can count on Ubuntu but not Fedora. Fedora maybe getting more polished now and may be good for some special tasks (overall not too bad a distro if you know its quirks and use it for experimentation)  but I wouldn't trade Ubuntu for it, not in a million years.

---

### Post by Jake_Paine on 2014-03-05
> **monkeybrain20122 said:**
> **Edited:** Crap. Shortly after writing this post did a Fedora update and now system won't boot. Must be punished by the Fedora God. Now back to the Ubuntu partition.

Hahahahahaha! This!! You deserve extra beans!

I must say my experience has always been different, however due to the restricted packages I've never settled with Fedora properly :(

Ubuntu is usually pretty good yeah, it's usually me moving to something bleeding edge that messes it up haha.

---

### Post by buzzingrobot on 2014-03-05
> **monkeybrain20122 said:**
> Fedora was solid even in Alpha days?? Are you serious?...

 Typing from Fedora 20 right now.

BTW, there isn't even a logout button on fedora's vanilla gnome without some tweaks, so sure OP's problem won't arise in a way. :)



Very serious.  F20 was solid for me from the alphas all the way through. Not every release has been.

I would not recommend Fedora for a newbie because it doesn't target new users. It is well supported but little handholding is provided; there's an implicit assumption the user comes to Fedora with Unix/Linux experience.

I don't agree with a number of design choices Gnome has made, but that's their call.  Designers and developers aren't under any obligations to users. Like authors, musicians and other creative people, they take their chances about whether or not anyone will like what they make.

The logout function can be restored with an extension. (Or, adding another user, as I recall.) Extensions are as much a fundamental part of Gnome Shell as widgets are to KDE or panel applets are elsewhere. Adding them is the first thing I do to a Gnome Shell installation.  Takes about 10 minutes.  (My Gnome installs have looked and behaved the same since 3.4.)

---

### Post by su:bhatta on 2014-03-05
> **buzzingrobot said:**
> 
....and Mate releases its new version, probably later this month.)

Wonder what OP meant and did he sort it out !


Mate 1.8 released :
[URL="http://www.webupd8.org/2014/03/mate-desktop-18-released.html"]http://www.webupd8.org/2014/03/mate-desktop-18-released.html

[/URL]

---

### Post by buzzingrobot on 2014-03-05
> **Jake_Paine said:**
> ... due to the restricted packages I've never settled with Fedora ...

Yeah, Red Hat is in a different liability position than distros not based in the U.S. And, RH customers get indemnification, which only increases the incentive to keep litigation-attracting-software off the servers.

Plus, they're pretty adamant about being FOSS-only.

For ordinary folks, of course, who just wanna watch a movie and don't know or care about any of this, Fedora/Red Hat just look inadequate and stubborn.

---

### Post by monkeybrain20122 on 2014-03-05
> **buzzingrobot said:**
> Very serious.  F20 was solid for me from the alphas all the way through. Not every release has been.

I would not recommend Fedora for a newbie because it doesn't target new users. It is well supported but little handholding is provided; there's an implicit assumption the user comes to Fedora with Unix/Linux experience.

I don't agree with a number of design choices Gnome has made, but that's their call.  Designers and developers aren't under any obligations to users. Like authors, musicians and other creative people, they take their chances about whether or not anyone will like what they make.

The logout function can be restored with an extension. (Or, adding another user, as I recall.) Extensions are as much a fundamental part of Gnome Shell as widgets are to KDE or panel applets are elsewhere. Adding them is the first thing I do to a Gnome Shell installation.  Takes about 10 minutes.  (My Gnome installs have looked and behaved the same since 3.4.)

Well I don't call it 'stable' when akmod failed to build for months (may still do, but I have been installing kmod along just in case) and gnome shell's dash doesn't record events (fixed only not long ago). Why couldn't I boot yesterday? For some strange reason after an update it was trying to connect to IPV6 when there was none (the genius of systemd?) and boot just hanged. I couldn't find a way to disable it before or during boot after trying various things so have to reinstall yet again! I disabled IPV6 now it boots.

In Ubuntu I keep a separate /home just for distro upgrade. In Fedora I keep a separate /home (and a list of installed software) for anticipated f*** up and the policy pays off

Can you believe this? I backup my systems by cloning them and it has  worked well for all distros I tried EXCEPT fedora. Restoring a Fedora  clone to a different device is like a lucky draw but with my other systems it is a routine thing.

Extensions are great as long as they work. But many have stopped working because of gnome changes or maybe devs just lost interest. I have not been able to find a replacement of something that does edge flipping (like in Unity-compiz) There were several extensions that forked off the original but none work in  F20.

**Aside:** Stability aside I find Ubuntu to be a more capable system out of the box.I tried to compile something in Fedora the other day. It didn't work because it needed an old gcc version. As a proof of concept I did it. Took me almost a whole day to compile gcc 4.4 and set up the switching mechanism (to hunt down patches, recompile .. googling..) In Ubuntu I tried the same exercise it took a minute as various versions of gcc are already in the repo and Debian's way of update-alternatives by changing symlink is pure genius. 

There is also no equivalent to autoremove in the rpm world as far as I know so you cannot uninstall the dependencies when you remove a program.

I am not an inexperienced user but why waste time doing things the  hard way when you can be more productive otherwise?  Some Linux users almost have a perverse pride in doing things in the most ineffective ways just to prove that they are 'real men'. But ineffectiveness is just that, not something to be proud of. I have tried to spend my time more evenly on both systems by moving some of my operations to Fedora. But the more time I spend on Fedora, the more I find out how good Ubuntu is and I have been expanding the Ubuntu partition and shrinking Fedora's steadily.

---

### Post by buzzingrobot on 2014-03-05
Not arguing that Fedora is perfect.  Just that I found F20 to be smooth and stable from very early on, installed on my hardware. OTOH, there have been Fedora releases I couldnt even install.

> **monkeybrain20122 said:**
> Well I don't call it 'stable' when akmod failed to build...

Isn't that a third-party thing?

> Extensions are great as long as they work. But many have stopped working because of gnome changes or maybe devs just lost interest   Agreed.  The ones I use seem to be bumped up rather quickly, happily.


>  Stability aside I find Ubuntu to be a more capable system out of the box.

Agree with that, too.  But, Fedora and Ubuntu have very different missions in life.  Ubuntu wants to be capable of being everyone's desktop.  Fedora wants to be a pure FOSS Linux that feeds technology to its Red Hat sponsor. I wouldn't recommend running a Fedora on a production machine. 

> ...why waste time doing things the  hard way when you can be more productive otherwise?  Some Linux users almost have a perverse pride in doing things in the most ineffective ways just to prove that they are 'real men'.

Ain't that the truth?  I know how to do a lot of things the hard way.  I don't see the point, though, when there's no payoff.

---

