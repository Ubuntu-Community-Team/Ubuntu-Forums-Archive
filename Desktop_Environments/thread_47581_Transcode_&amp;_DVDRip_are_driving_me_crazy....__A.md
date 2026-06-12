---
title: "Transcode &amp; DVDRip are driving me crazy....  Absolutely bloody crazy."
date: 2005-07-09
forum: Desktop Environments
---

### Post by Raptor Ramjet on 2005-07-09
Hello,

A week ago I got a nice DVD burner for my Linux machine.  Since then I have been trying to install dvdrip & transcode etc. but it is driving me crazy.   I have been through the forum, have looked at all the various posts and have tried various things but all to no avail...

So after much messing around the "state of the art" is that when I try to install dvdrip using Synaptic I get the following error:

dvdrip:
 Depends: transcode but it is not going to be installed

But when I try to install install transcode I get the following error:

transcode:
  Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed


Fantastic...  So if anyone could tell me what bloody combination of repositories I should have in /etc/apt/sources.list to get these bloody things installed I'd be most grateful ?

Sadly it seems to me that current state of X86 computing boils down to the following...

Windows: You can't anything done because you spend all your time trying to secure the box, remove adware, spyware & viruses and fight against the operating system trying to do (the wrong) things for you.

Linux: You can't get anything done because you spend all your time trying to get the bloody software configured.

Mac: You can't get anything done because you can't afford the bloody hardware in the first place (and no, a Mac Mini does not fit my needs)

For fricks sake I think I'll just use DVDShrink on my bloody Windows box and go down the pub instead.....  A thoroughly, thoroughly unsatisfactory start to the weekend :(

---

### Post by emmet on 2005-07-09
Errrr, hi...

Do you want some help with your installation? 

If you do a little search on the ubuntuforums....for DVDRip for example, you get some nice links where people in exactly your situation have solved the very same problem.

Have a look here:
[http://www.ubuntuforums.org/showthread.php?t=548](http://www.ubuntuforums.org/showthread.php?t=548) 

I think this is most applicable. I went through the same process when I installed DVDRIp. It now works well.

On the other hand, if it's a nice day, then maybe time would be best served by toddling off down to the pub, sit in the beer garden with a pint of bitter and a packet of salt'n'vinegar crisps...sounds much better.

 ;-) 

Emmet

---

### Post by simion on 2005-07-17
Actually I'm with the first poster.  This is absolutely stuffed.  So many links that hint at a solution but noe that actually solve a problem.  I'm not having a go at anyone on the forums but none of these links are of any assistance.  Does anyone have a solution to this?  Or perhaps a better question is WHY THE HELL IS LINUX STILL SUFFERING FROM DEPENDANCY HELL!

I mean come on, how long has linux in its various flavour been around?  How hard can this be?

---

### Post by jiyuu0 on 2005-07-18
have you tried this?
[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)

if you really can't get anything to work, or tired of configuring... check this out
[http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)
*reinstall your ubuntu, then use the add-on cd to install the rest

---

### Post by Navin_Johnson on 2005-07-18
I'm with the original poster here too.  I've tried multiple solutions suggested here, and while I certainly appreciate everyone's efforts -- so far none have worked and I've resigned myself to use DVDShrink under Wine.

In my opinion this is a major problem that needs a real solution rather than several workarounds which some people get to work and others don't.

---

### Post by linuxNewb on 2005-07-18
If you just want to rip dvds to your hard drive, then apt-get dvdbackup. It installs and works perfectly.

---

### Post by Navin_Johnson on 2005-07-20
linuxnewb:  thank you for your suggestion, I'll give it a try.

I still think that it should not take such a great effort to get dvdauthor and transcode (and therefore also lxdvdrip) working under ubuntu, and hopefully others have more success than I.

---

### Post by Magneto on 2005-08-04
[QUOTE=Navin_Johnson]linuxnewb:  thank you for your suggestion, I'll give it a try.

I still think that it should not take such a great effort to get dvdauthor and transcode (and therefore also lxdvdrip) working under ubuntu, and hopefully others have more success than I.[/QUOTE]
 1 word 2 syllables

Backports

Add the backports and no need for marillat's dependency hell

thank you guys for workin on them all this time - I used to wonder why zen (i think) and those guys would crank those out all the time, now I know its so people can grovel before them

---

### Post by sinbad782 on 2005-08-04
I think the problem is with not using the right repositories. Marillat conflicts with the ubuntu-backports project etc. etc.

You could use acidrip as well. Just don't forget to install lame at the same time. I find this works pretty well - I've ripped a couple of DVDs and encoding them into DivX on the fly using this - this is quite a bit slower than straight ripping though.

---

### Post by WayneT on 2005-08-04
[QUOTE=Magneto]1 word 2 syllables

Backports

Add the backports and no need for marillat's dependency hell

thank you guys for workin on them all this time - I used to wonder why zen (i think) and those guys would crank those out all the time, now I know its so people can grovel before them[/QUOTE]
 Ok, how specifically do you install backports?

---

### Post by Magneto on 2005-08-04
Yeah its a repo problem. People keep trying to use marillat repos when they don't need to. If you use the marillat repos you are going to have to find the right packages to satisfy all those dependencies and install them by hand. Then you wonder why you left Gentoo etc etc come back crying to the forums and discover...............if you just add the backport repos dvdrip and transcode will install problem free. That's why people keep directing others to the ubuntu 5.04 starter guide but for some reason folks don't want to follow the directions listed. 


start here and there isn't a need for marrilat or parmilat or whatever
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
:)

---

### Post by Magneto on 2005-08-04
[QUOTE=WayneT]Ok, how specifically do you install backports?[/QUOTE]
 sorry i was responding and hadn't refreshed the screen yet

to add backports 

add these two lines to /etc/apt/sources.list

from the command line

sudo nano -w /etc/apt/sources.list



scroll down and type


## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


type control O to save it

sudo apt-get update

sudo apt-get install transcode dvdrip

---

### Post by Hep on 2005-08-23
Hi Guys,

I tried to use the "backports". but transcode/dvdrip is not found.
apt-get install transcode
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Aucune version du paquet transcode n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source
Cependant les paquets suivants le remplacent :
  transcode-doc
E: Aucun paquet ne correspond au paquet transcode

apt-get install dvdrip
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet dvdrip

---

