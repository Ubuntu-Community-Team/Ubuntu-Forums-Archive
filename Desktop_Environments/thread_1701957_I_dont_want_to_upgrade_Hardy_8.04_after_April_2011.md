---
title: "I dont want to upgrade Hardy 8.04 after April 2011"
date: 2011-03-07
forum: Desktop Environments
---

### Post by mister_p_1998 on 2011-03-07
I dont want to upgrade my Hardy installation when it expires in April this year, what are my options? are there (or will there be) Repo mirrors after the expiry date that I can use after April? I have this set up just right and dont want the hassle of upgrading, but would like to maintain active repos.
Steve

---

### Post by nomko on 2011-03-07
Well, first of all, it is your own choice to stick with 8.04. But be reminded that 8.04 LTS is a little bit outdated compared to 11.04 or even compared to 10.04 LTS. The normal support span is 3 years for LTS versions. After 3 years there will be no further support given. Keeping that in mind it must be clear that, if you continue to use 8.04, you will end up with a version that a) is no longer supported, b) will miss some vital updates and c) due to a and b will be very outdated. Even support for latest hardware won't be out-of-the-box, manually installing and compiling source files will be neccesary to maintain your version and keep it a little bit up-to-date. My advice: update from 8.04 LTS to 10.04 LTS.
 
Maybe some else here has another opinion about this...

---

### Post by Frogs Hair on 2011-03-07
Use what you like , but your window to upgrade at all is closing . At some point you may have to do a clean installation.

---

### Post by mcduck on 2011-03-07
> **mister_p_1998 said:**
> I dont want to upgrade my Hardy installation when it expires in April this year, what are my options? are there (or will there be) Repo mirrors after the expiry date that I can use after April? I have this set up just right and dont want the hassle of upgrading, but would like to maintain active repos.
Steve

The repositories for old releases are maintained at oldreleases.ubuntu.com, but keep in mind that they are not updated or supported after the releases has reached end of it's life.

This means no new software, and more importantly, *no security updates*. Which is rather important point to consider if your computer is connected to Internet....

I would really recommend upgrading, go for the next LTS version if you don't want to upgrade too often. That at least allows you to keep your system secure.

---

### Post by mister_p_1998 on 2011-03-07
I always do a fresh install anyway.
Couldnt find a list of repos at old-releases.ubuntu.com, can you point me in the right direction? My machine is behind a router, so not too bothered about security issues. Its just sitting there downloading stuff 18 hours a day.

---

### Post by Bucky Ball on 2011-03-07
I would upgrade to 10.04 LTS, the current long term support release, using update manager ASAP. Many of your settings will be kept. I have three machines that only run LTS releases that I upgraded from 8.04 LTS to 10.04 LTS and all is sweet as it was, but better. All my settings are pretty much the same (shortcut keys, tweaks, etc). 

I'm happy for the next three years. I wish I could be running 10.04 LTS on this laptop also but it only seems to like 10.10. My wife and I are both at uni so we need all machines rock solid (as can be) so LTS it is where possible. Good luck. ;)

---

### Post by Kirboosy on 2011-03-07
10.04 is solid. I think your computer would be compatible (reading your signature). Also 10.04 has a wicked fast startup time. :D

---

### Post by mister_p_1998 on 2011-03-07
Yeah, I run it at work, just cant be bothered will all the agro... never had an upgrade go right yet...

---

### Post by mcduck on 2011-03-07
> **mister_p_1998 said:**
> I always do a fresh install anyway.
Couldnt find a list of repos at old-releases.ubuntu.com, can you point me in the right direction? My machine is behind a router, so not too bothered about security issues. Its just sitting there downloading stuff 18 hours a day.

It's not there yet, only after the release is out of support.

Once that happens the following repositories should become available:
```
deb http://old-releases.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
```
(but like I said, they will simply contain whatever was in the hardy's repositories when it's support ended, the packages will not be updated or maintained in any way.)

Also installing security updates is definitely a wise way to go if the machine is connected to the Internet, regardless of if it's behind a router or not (although I agree that a router does make things at least a little bit safer).

---

### Post by tyleruk on 2011-03-07
I stuck with 8.04 for ages and refused to upgrade, then my Hard Drive failed (Nothing to do with 8.04 just a cheap HDD) so I installed 10.04 and I&#8217;m so glad I did it&#8217;s much faster and better looking.

I know it&#8217;s annoying upgrading but 10.04 is defiantly worth it, you won&#8217;t regret it.

---

### Post by Kirboosy on 2011-03-07
> **mister_p_1998 said:**
> Yeah, I run it at work, just cant be bothered will all the agro... never had an upgrade go right yet...

In your case I would fresh install. With upgrades (from my understanding) you have to patch every version in between. So you would have to go 8.10, 9.04, 9.10, and 10.04. 

Fresh installing would allow you to start over with a clean system and take less time. :)

I guess if you were just jumping from like 8.04 to 8.10 upgrading would be fine but in your case fresh installing seems better

---

### Post by TroN-0074 on 2011-03-07
> **mister_p_1998 said:**
> I dont want to upgrade my Hardy installation when it expires in April this year, what are my options? are there (or will there be) Repo mirrors after the expiry date that I can use after April? I have this set up just right and dont want the hassle of upgrading, but would like to maintain active repos.
Steve

It is pretty much up to you, however if you do the upgrade all your settings remains. If you do a fresh install then you will have to set it up the way you like.

---

### Post by qamelian on 2011-03-07
> **Caboose885 said:**
> In your case I would fresh install. With upgrades (from my understanding) you have to patch every version in between. So you would have to go 8.10, 9.04, 9.10, and 10.04. 
This only applies to regular releases. LTS releases support upgrading directly to the next LTS release without hitting all the intermediate releases.

---

### Post by Bucky Ball on 2011-03-07
Upgrading difficult? I hit the 'Upgrade to 10.04 LTS' button in update manager, wandered off and did some things, three hours later I was ready to roll. Nothing involved from my end except one click and a three hour wait. Simple. Settings remain.

And yes, LTS release upgrades to the next LTS release simply. That is the point (especially if you are running production machines which can't afford to be down for long). 

Good luck whatever you decide. ;)

---

### Post by Kirboosy on 2011-03-08
> **qamelian said:**
> This only applies to regular releases. LTS releases support upgrading directly to the next LTS release without hitting all the intermediate releases.

Oh ok. I didn't know that. Thanks for the information :)

---

### Post by Wim Sturkenboom on 2011-03-08
> **Bucky Ball said:**
> Upgrading difficult? I hit the 'Upgrade to 10.04 LTS' button in update manager, wandered off and did some things, three hours later I was ready to roll. Nothing involved from my end except one click and a three hour wait. Simple. Settings remain.
So did I :D But it popped up messages all over the show so it was a bit longer than 3 hours and at the end it stated that I might have ended with an unstable system.

They were wrong, it was not unstable as it did not even want to boot into Ubuntu :( A very stable terminal screen after selecting Ubuntu from the Grub menu.

Was a good reason to upgrade to 64 bit :D

---

### Post by mister_p_1998 on 2011-03-14
Yeah, I'm gonna use the archive repos after April, I cant even remember the last time I installed a new program on my Hardy install. Its running so sweet I don't want to change a thing. I tried doing an app export from Package manager on my Hardy laptop, installing Lucid, then re-importing the package markings. It came up with a huge list of programs to be removed if I installed my marked apps (Including Ubuntu-Desktop and Grub2!) So I didn't want to install the marked apps! It might be better if the marked OS and apps separately so you don't muck up the system when installing marked apps. I did this from Dapper to Hardy & it worked fine, but I guess Dapper & Hardy are more similar that Hardy & Lucid. I really don't need the latest version - it does exactly what I want as it is. I think I ran Gutsy about two years after it expired - no problems.
Maybe I should start an expired distro User Group!
Steve

---

### Post by Bucky Ball on 2011-03-16
Lucid is not the latest. Maverick is. Soon Natty Narwhal will be. Lucid 10.04 LTS *is* the latest long term support release.

Yea, if it works for you why not. The latest is not always the greatest, especially if you are after stability. ;)

---

### Post by mister_p_1998 on 2011-03-17
> **Bucky Ball said:**
> Lucid is not the latest. Maverick is. Soon Natty Narwhal will be. Lucid 10.04 LTS *is* the latest long term support release.

Yea, if it works for you why not. The latest is not always the greatest, especially if you are after stability. ;)

Finally! someone who gets what Im talking about!

If it aint broke, dont fix it!
Its on 20 hours a day minimum, downloading, recording Radio shows, running a stack of Cron jobs, I dont need all the whizziest apps, every single one on my system run exactly how I want it  to.
):P

---

### Post by mcduck on 2011-03-17
I suppose for most people the reason why out-of support release is out of the question is not because it doesn't have the latest program versions, but because it's insecure due to lack of security updates.

I personally couldn't care less about which versions of programs I'm running as long as they do what I need them to do, but *still* wouldn't ever consider using a non-supported release apart from machines that are in no way connected to the Internet (thus excluding any computer used for normal desktop purposes).

---

### Post by johnny_fly on 2011-10-07
My English is bad [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] but ....
8.04 is good
we yet have a old pc
so ... I am sad

---

