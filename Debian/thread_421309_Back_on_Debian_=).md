---
title: "Back on Debian =)"
date: 2007-04-24
forum: Debian
---

### Post by plb on 2007-04-24
Well after about a 5month voyage on Ubuntu, I'm back on Debian. To all those interested in trying out Debian, Lenny makes a superb desktop.

---

### Post by bwhite82 on 2007-04-24
> **plb said:**
> Well after about a 5month voyage on Ubuntu, I'm back on Debian. To all those interested in trying out Debian, Lenny makes a superb desktop.

Kudos. Exactly what I'm using. I tried a little foray into Sid, had some problems (was expected), changed back to Lenny.

---

### Post by plb on 2007-04-24
Yeah, unstable is a gamble sometimes.

---

### Post by Pobega on 2007-04-24
Welcome back, I didn't even know that you left!

Unstable broke recently, with a new XOrg update. Or at least nVidia users felt the worst of it. I'd recommend sticking with testing if you need your computer for things other than messing around.

---

### Post by bwhite82 on 2007-04-24
> **Pobega said:**
> Welcome back, I didn't even know that you left!

Unstable broke recently, with a new XOrg update. Or at least nVidia users felt the worst of it. I'd recommend sticking with testing if you need your computer for things other than messing around.

Yep, that was exactly the problem (not just Nvidia users). My system was only recognizing Xorg as version 1.something for everything that I did with it.

---

### Post by elcu on 2007-07-28
Sorry for digging up an old thread.

> **plb said:**
> Well after about a 5month voyage on Ubuntu, I'm back on Debian. To all those interested in trying out Debian, Lenny makes a superb desktop.

I've been interested in moving to Debian for a while now.  I love Ubuntu, but for some weird reason I would feel better running Debian proper.  8-[

My experience with it is limited - I only started trying other distros out recently.  A few questions:

- Out of curiosity, why did you (or others who have done the same thing) move back? 
- You recommended using Lenny.  I tried a Sid install but was put off when 100MB worth of updates showed up a couple of days after I thought I just updated.   I get the impression unstable moves very fast.  Is Lenny as quick to update?

---

### Post by b9anders on 2007-07-28
lenny has gone through a rapid development cycle recently, but things seems to have slowed down a bit lately. Aside from Compiz Fusion which is updated almost daily, I get about a handful of updated packages every two or three days at the moment. Nothing too severe but you do get a system that is being upgraded at a fairly fast rate.

Running sid requires some skill to maintain your system. Lenny *is* a testing branch so some breakage can occur although rare, but I find it to be as stable as any distro I have tried. Ponder this: Ubuntu is built off a snapshot of debian sid that then goes through development for five months or so until a new version of ubuntu is released - Testing is based off the most recent stable version of Debian and new stuff then gradually trickle in from sid when they are deemed ready. The breakage that may occur in testing is with recently introduced stuff and is hence fixed relatively quickly (and in the meantime, you can fix it yourself by simply reverting the upgrade) rather than untested and undiscovered bugs that may not have been adequately tested in sid.

Personally, I went from Ubuntu to Debian because I found Ubuntu a bit too bloated and overly configured. I am by no means proficient enough to go to slackware, Gentoo or arch (nor do I care to spend so much time to maintain my system as they seem to require), but I like to be in control of my system and have it tweaked to my liking. Debian encourages that whilst providing one of the fastest distros I have tried.

---

### Post by odiseo77 on 2007-07-28
> **elcu said:**
> Sorry for digging up an old thread.



I've been interested in moving to Debian for a while now.  I love Ubuntu, but for some weird reason I would feel better running Debian proper.  8-[

My experience with it is limited - I only started trying other distros out recently.  A few questions:

- Out of curiosity, why did you (or others who have done the same thing) move back? 
- You recommended using Lenny.  I tried a Sid install but was put off when 100MB worth of updates showed up a couple of days after I thought I just updated.   I get the impression unstable moves very fast.  Is Lenny as quick to update?

You don't necessarily have to completely move to debian; if you have enough free space on your HD you can install debian aside ubuntu, try them both out, and then you can eventually switch to debian (I've been using Debian since like a couple of years now and started using Ubuntu like one year ago, and I like them a lot, so I have them installed on my HD's (as well as many other distros :biggrin: ) and don't see the need to remove Ubuntu :D )

---

### Post by b9anders on 2007-07-28
This may be a silly question but if you are capable and willing to work with Debian, what exactly do you find Ubuntu offers that Debian doesn't to make you want to keep it?

---

### Post by bennyj on 2007-07-28
> **plb said:**
> Well after about a 5month voyage on Ubuntu, I'm back on Debian. To all those interested in trying out Debian, Lenny makes a superb desktop.

I went to the Debian web site but I am not sure what I have to do here(not the sharpest tool in the shed).Do I have to download all those cd's.Or is there just one to download. I want to use the i386 version of Lenny.Could someone make this a little clearer for me.Thanks

---

### Post by odiseo77 on 2007-07-28
> **b9anders said:**
> This may be a silly question but if you are capable and willing to work with Debian, what exactly do you find Ubuntu offers that Debian doesn't to make you want to keep it?

For me both of them are great distros, but as I said in another thread, I use Ubuntu when I get lazy and Debian when I want to get my hands working on something (and anyway, I have like 6 or 8 different distros on my machine, including gentoo, etc, so basically , I'm a linux addicted :D )

---

### Post by odiseo77 on 2007-07-28
> **bennyj said:**
> I went to the Debian web site but I am not sure what I have to do here(not the sharpest tool in the shed).Do I have to download all those cd's.Or is there just one to download. I want to use the i386 version of Lenny.Could someone make this a little clearer for me.Thanks

Hi, if you have broadband and you're not using a wireless connection, then the best method to install debian is to get the [lenny netinstall.iso]("http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-netinst.iso"), burn it to a cd and start the installation. It will start with a minimal set of packages and then fetch the remaining ones from  the debian mirrors.

Greetings.

---

### Post by b9anders on 2007-07-28
the developers are currently recommend installing etch and then upgrading to lenny as the installer for lenny is not entirely bugfree due to all the recent changes.

---

### Post by bennyj on 2007-07-29
> **odiseo77 said:**
> Hi, if you have broadband and you're not using a wireless connection, then the best method to install debian is to get the [lenny netinstall.iso]("http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-netinst.iso"), burn it to a cd and start the installation. It will start with a minimal set of packages and then fetch the remaining ones from  the debian mirrors.

Greetings.

Thanks for the info....I now have Debian up and running!So far so good.Seems to run  a little faster.I love unbutu for getting me here...I just felt like it was time to graduate.

---

### Post by rabid emu on 2007-07-31
I recently installed Etch and upgraded to Lenny.  A word of caution, the newest FGLRX (and, I hear, nvidia drivers) don't work with the newest 2.6.21 kernel because of paravirtualization in the kernel.  2.6.22 will resolve this but as of right now I don't have any graphics acceleration.

Another annoyance for me is that under Etch, I had multimedia working perfectly (I install vlc and all codecs get installed).  Upon upgrading to Lenny, I find that the "vlc" package no longer exists, and in fact I can't find vlc media player in the repos at all.  Aptitude won't do anything until it removes vlc, so I'm stuck with no media support for right now until I figure out how to get codecs installed again.

There's also packages in Kubuntu that aren't in Debian that I really like, such as Kxmame.  That's a big turn off for me as I love me some gaming.

All in all I still like kubuntu better, but I'm going to keep trying to get Debian working correctly.

---

### Post by happy-and-lost on 2007-08-01
I'm back, but only 'cos I can't be bothered to dig out my Gutsy CD so I can fix my broken gutsy.

---

### Post by b9anders on 2007-08-01
> **rabid emu said:**
> Another annoyance for me is that under Etch, I had multimedia working perfectly (I install vlc and all codecs get installed).  Upon upgrading to Lenny, I find that the "vlc" package no longer exists, and in fact I can't find vlc media player in the repos at all.  Aptitude won't do anything until it removes vlc, so I'm stuck with no media support for right now until I figure out how to get codecs installed again.

just temporarily points your sources to etch or sid and get vlc from there. don't know why it isn't in testing at the moment, but it will be again at some point.

The sid version is perfectly stable for me, btw.

---

### Post by Incense on 2007-08-03
I have always wanted to play around with Debian just because the releases are named after Toy Story characters, with Sid being the unstable development. That is just too amusing!

---

