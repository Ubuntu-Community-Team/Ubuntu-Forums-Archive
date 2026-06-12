---
title: "How stable is Ubuntu?"
date: 2005-08-22
forum: Desktop Environments
---

### Post by MdaG on 2005-08-22
Is Ubuntu divided into stable and unstable like Debian or is there other divisions? How do I know which branch I'm using? I've already noticed that Ubuntu isn't as stable as Gentoo for example since I've already had a couple of programs freeze on me... I did update Ubuntu a few hours ago when I saw an icon blinking in the upper right corner... So, how do I know which packages are stable and which aren't, and how do I only update stable packages?

---

### Post by DJ_Max on 2005-08-22
Ubuntu is not Debian, so it doesn't have different branches. Ubuntu is pretty stable. You having problems doesn't mean the whole distro isn't stable.

---

### Post by Tinuz on 2005-08-22
[QUOTE=MdaG]Is Ubuntu divided into stable and unstable like Debian or is there other divisions? How do I know which branch I'm using? I've already noticed that Ubuntu isn't as stable as Gentoo for example since I've already had a couple of programs freeze on me... I did update Ubuntu a few hours ago when I saw an icon blinking in the upper right corner... So, how do I know which packages are stable and which aren't, and how do I only update stable packages?[/QUOTE]

Hmm, you're mixing some things up here. You are telling that some programs are crashed, and followingly concluded that the OS itself isn't stable. As you said, the PROGRAMS crashed, and not the shell. 

But Ubuntu is pretty stable, I haven't experienced a single crash.
Oh, and there are some programs which tend to crash such as amsn and on some machines XMMS and Beep media player. But both are a result of the new kernel, so they should be fixed some time soon.

---

### Post by xequence on 2005-08-22
Its very stable. Windows blue screened me every day many times, ubuntu hasnt ever froze on me. The closest to that ive came was seeing if wine could run IE and that froze. But just the window, and I easily stopped it.

---

### Post by Chris Cromer on 2005-08-22
The only program I have had trouble with is XMMS, but the OS itself works great and is very stable in my opinion.

---

### Post by KingBahamut on 2005-08-22
Yo, um stable, and stuff. 
=)

---

### Post by ssck on 2005-08-22
so far it has been pretty stable except for nautilus and the panel crashing once in a while.other than that it has been OK.

---

### Post by Dolphin on 2005-08-22
Like a rock.

---

### Post by debian_n00b on 2005-08-23
[QUOTE=xequence]Its very stable. Windows blue screened me every day many times, ubuntu hasnt ever froze on me. The closest to that ive came was seeing if wine could run IE and that froze. But just the window, and I easily stopped it.[/QUOTE]



I use XP at work and havn't experienced a freeze or BSOD in years. Maybe win 98, but thats not fair to compare as it is 10 years old now.

But on topic, I find Ubuntu stable enough to run on the mother-in-law's machine. Thats very stable :-)

---

### Post by mrcbrown on 2005-08-23
[QUOTE=debian_n00b]I use XP at work and havn't experienced a freeze or BSOD in years. Maybe win 98, but thats not fair to compare as it is 10 years old now.

But on topic, I find Ubuntu stable enough to run on the mother-in-law's machine. Thats very stable :-)[/QUOTE]

I'd have to agree - I don't think in Windows I have gotten a BSOD in a LONG time, - I have a XP workstation and a laptop, neither has any BSOD issues, but I also have a mac, but I can crash anything at least once :)

As for Ubuntu, it works, good desktop release, not enjoying how some things compile (or don't) from source for some server elements I wanted, but all in all as a day-to-day OS for desktop use, lovin it.

---

### Post by MdaG on 2005-08-23
[QUOTE=DJ_Max]Ubuntu is not Debian, so it doesn't have different branches. Ubuntu is pretty stable. You having problems doesn't mean the whole distro isn't stable.[/QUOTE]

You misunderstand me, I was wondering if I had somehow installed an "unstable"-version of the program. My question was about if there are stable branches and unstable, like those in Debian and Gentoo. Or is there only one big repository with different levels of support? If so, what does the devs mean by "support"?

---

### Post by Lord Illidan on 2005-08-23
I think the unstable is Breezy Badger, which is still in development. But if you installed Ubuntu from the main website, and used the repos in the ubuntu guide, or had a ship it cd, then you have the stable version, Ubuntu 5.04

---

### Post by MdaG on 2005-08-23
These are in my repository:

[b]deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse[/b]

Is it possible to update from the unstable branch if so, how?

---

### Post by blueturtl on 2005-08-23
> Is it possible to update from the unstable branch if so, how?

I understand this happens by switching all the repositories to their breezy equivalents and then running the apt-dist upgrade or something like that. However currently, the most stable system would be achieved with Hoary Hedgehog as it's the latest official release and has matured for months now with updates.

To make things obvious:

Warty Warthog - old Ubuntu release, stable
Hoary Hedgehog - current Ubuntu release, newest stable
Breezy Badger - due for release in October, in testing (possibly unstable)

I'm currently running Ubuntu Hoary Hedgehog 5.04 on my workstation - and never in my life have I known such stability. Of course before I was a Windows user, but that's beside the point I guess.  ;-)

---

### Post by kahping on 2005-08-23
brief FYI, just replace every instance of hoary with breezy, refresh your repository index files and dist-upgrade to get breezy.

But since you're looking for stability, it's a very bad idea to do that now. Wait for breezy's release this October for that ;-)

kahping

---

### Post by MdaG on 2005-08-23
Thanks now I understand. I yes I'm going to wait. I prefer stability over bleeding edge. I'm wondering though, why OpenOffice is still 1.1.3 and Gaim isn't yet up to 1.4 at least. are they not considered stable? (there are more examples).

edit:
Also, how do I find repositories closer to my physical home? Is there an easy way? I have netselect, but I don't know how to find the repositories to test with.

---

### Post by darkbluesea on 2005-08-23
Replying to the orignal question:

I'm a quite recent user of ubuntu, almost 6-7 months now, and I might say i've *never* had much problems with it. I mean those that i had was for lack of knowledge wich you quickly learn with some patitente and free time (maybe some friends help 8-) )

For the casual user its almost perfect, user-interface and the synaptic packet manager helps a lot. I've converted  few fiends because of its easy of use. And wine helps a lot for those apps you miss from windows. 

I'm also a game addict in some very rare free time, wich cedega helped a lot, and some wine proper configuration. I manage to play World of Warcraft and Warcraft3 so very well in my linux box i never had any complains. 

Has a remote workstation i'm in a test fase, trying to set it up for fun, but so far it hasnt failed once. 
But then again i defent that the stability of a distro depends on the user, and I'm quite "newbie" in linux. If you have time and patitente you can tweak whatever you like.

---

### Post by Lord Illidan on 2005-08-23
[QUOTE=MdaG]Thanks now I understand. I yes I'm going to wait. I prefer stability over bleeding edge. I'm wondering though, why OpenOffice is still 1.1.3 and Gaim isn't yet up to 1.4 at least. are they not considered stable? (there are more examples).


edit:
Also, how do I find repositories closer to my physical home? Is there an easy way? I have netselect, but I don't know how to find the repositories to test with.[/QUOTE]


You can install Open Office 2.0, the beta... try running a simple search in the forums...

About Gaim, well if you have enabled all the repos in the Ubuntu Guide, and typed ```
sudo apt-get upgrade
``` , it should upgrade itself. Otherwise, it hasn't been done yet.

And repositories closer to home... hmm, where do you live?

---

### Post by MdaG on 2005-08-23
[QUOTE=Lord Illidan]
And repositories closer to home... hmm, where do you live?[/QUOTE]

Sweden

---

### Post by Zodiac on 2005-08-23
It is stable provided you do not right click on any file, ever... god help you if you do...

Never got an answer to that little problem either, to me it is the only negative about Ubuntu...  :-?

---

### Post by MdaG on 2005-08-23
What happens if I right click? I tried it on a custom made launcher and it only presented me with a list of options...

---

### Post by tag on 2005-08-23
Nah' everything works fine, except sometimes your printer dissapears and the sound architecture is a mess - but that's the same thing with all Linux distros. In fact Ubuntu works best of all distros i've tried (SuSE, RedHat, Gentoo, Mandrake, Debian Woody).

---

### Post by MdaG on 2005-08-23
For me Gentoo has worked flawlessly. Only problem with that distro is that one has to be up to date with Portage. Maintaining the system in Gentoo is dangerous. I've broken the system at least six times doing a **"emerge -uND world && emerge depclean && revdep-rebuild"**. After the sixth time I was fed up and went searching for a distro that wouldn't force me to constantly monitor the events of the distro and here I am.  :smile:

---

### Post by Reb on 2005-08-23
The difference between stability of Linux distributions is minimal and mostly subjective.

---

### Post by skoal on 2005-08-23
[QUOTE=Reb]The difference between stability of Linux distributions is minimal and mostly subjective.[/QUOTE]
Here, Here, Mr. Gates! Well said. I concur!

Stability? If you were standing on a ladder with any linux distro as your base, some are grass, some are dirt, and some are concrete.  There's no guarantee either will provide you a good footing as you proceed further up that knowledge ladder.  Typically, installing more non base packages and/or building custom -ck kernels is synonymous with that climb.  Conversely, at some point we all come back down a few rungs and find that safe median between stock i386 and bleeding edge...

\\//_

---

### Post by DJ_Max on 2005-08-23
[QUOTE=MdaG]Thanks now I understand. I yes I'm going to wait. I prefer stability over bleeding edge. I'm wondering though, why OpenOffice is still 1.1.3 and Gaim isn't yet up to 1.4 at least. are they not considered stable? (there are more examples).

edit:
Also, how do I find repositories closer to my physical home? Is there an easy way? I have netselect, but I don't know how to find the repositories to test with.[/QUOTE]
 Software such as OpenOffice 1.1.3 has been broven stable during the time of the release of Hoary. After that there are no more updates, only for security.

If you want updated packages, use the backports.

Also, for mirrors closer to your country. [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

### Post by MdaG on 2005-08-24
[QUOTE=DJ_Max]
If you want updated packages, use the backports.
[/QUOTE]

Backports?

---

### Post by chadauld on 2005-08-24
[QUOTE=Dolphin]Like a rock.[/QUOTE]
Agreed...  Got a 64bit and a 32bit version running with no issues to report   :)

---

### Post by Galoot on 2005-08-25
[QUOTE=MdaG]Backports?[/QUOTE]
The [Ubuntu Backports project](http://backports.ubuntuforums.org/).

Adding the following lines to /etc/apt/sources.list will enable you to find more recent versions of many packages.

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

