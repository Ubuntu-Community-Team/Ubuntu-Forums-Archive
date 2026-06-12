---
title: "Blocked updates??? What is going on here?!"
date: 2009-06-19
forum: General Help
---

### Post by The Toxic Mite on 2009-06-19
Hi all!

I got a notification earlier this morning (06:14 GMT) about some updates.

But when I opened the update thing, I saw that there was "blocked updates"...

They all seem important for my computer, so I don't know why they are blocked.

I only have the default repositories enabled, I have added nothing else to the sources.

-TTM-

---

### Post by Chronon on 2009-06-19
I had the same problem earlier.  I found the solution by searching.  
I followed the instructions in this post: [http://ubuntuforums.org/showpost.php?p=7230931&postcount=9](http://ubuntuforums.org/showpost.php?p=7230931&postcount=9)

```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by bumanie on 2009-06-19
Try > sudo apt-get update && sudo apt-get upgrade in terminal. If they are still blocked, may be there is something wrong with the repo's server you are connecting to. You could try another server also.

---

### Post by The Toxic Mite on 2009-06-19
```
calvinps@InterCity-125:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_GB                                                            
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_GB                                                      
Hit http://gb.archive.ubuntu.com jaunty Release.gpg                             
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                  
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB            
Hit http://security.ubuntu.com jaunty-security Release.gpg                      
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB           
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB     
Hit http://archive.ubuntu.com jaunty Release.gpg                                
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB       
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB     
Hit http://security.ubuntu.com jaunty-security Release                          
Hit http://archive.ubuntu.com jaunty Release                                    
Hit http://gb.archive.ubuntu.com jaunty Release                                 
Hit http://gb.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/main Packages
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
[B]The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic[/B]
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
calvinps@InterCity-125:~$
```I have no idea why they have been blocked. :confused:

---

### Post by bumanie on 2009-06-19
I just looked up launchpad and found that there are various entries there with this error in the past. Seemingly this is a bug that appears occasionally - may be you should put in a bug report to launchpad. I think the 'kept back' updates, have unmet dependencies. Unless someone else comes up with a fix, a bug report to launchpad would be best. Sorry can't help.

---

### Post by Chronon on 2009-06-19
I think this might be the one I followed, actually: [http://ubuntuforums.org/showpost.php?p=7436695&postcount=11](http://ubuntuforums.org/showpost.php?p=7436695&postcount=11)

```
 sudo apt-get dist-upgrade
```

---

### Post by smithers888 on 2009-06-20
I had exactly the same problem, and found (as Toxic Mite did) that
```
apt-get update
apt-get upgrade
```did nothing to help. However following Chronon's first suggestion, I used
```
aptitude full-upgrade
```which worked. I noticed that it also *uninstalled* two old packages. Perhaps the requirement to uninstall these was causing the block?

---

### Post by marciovinicius on 2009-06-20
I have the same problem here. The blocked packages here are "linux-readers-generic", "linux-restricted-modules-generic", "linux-generic" and "linux-image-generic". As you see, all of them related to Linux's kernel (2.6.28.11.15).

I don't want to install them now. Before I do it, I have to know the answer for some questions:

What is a blocked update?
Why are there blocked updates?
If they are blocked, is it safe to install them anyway?
And finally (the most annoying question), why notifier notifies me about an update I can't install?

It may happen because there's a bug, but the fact is that Kpackagekit can block some updates and before we can tell it is a bug we need to know why kpackagekit blocks updates (I don't know why, and nobody here answered it untill now). Kpackagekit may have a good reason to do it.

P.S.: BTW I'm new in kubuntu (I used to use ubuntu), I've been loving it, but the worst part of KDE is the packages manegement software (Kpackagekit simply sucks).

---

### Post by Sxeptomaniac on 2009-06-22
I just put in *sudo apt-get dist-upgrade*, which is installing the blocked updates.  I wish they would provide an easy way for kpackage to tell you how to fix the blocked updates problem.  I would install Synaptic, but for some reason dependencies want me to install the entire Gnome desktop system these days, but it never did that in the past.  Anyone know why that is?

---

### Post by Therion on 2009-06-22
I'm going to stick my neck out a little and say that *usually* blocked packages are due to dependency issues.  What I do know from experience that simply chilling out on the situation for a day or two resolves the error.  In my experience it's not a "problem" at all; the packages have been put into Limbo for a reason.

I hesitate to recommend other methods of "pushing through" the install if your chosen package manager is holding them back.  I'm not saying "don't do it" - hey, it's your system - I'm just saying it's nothing to freaking come unglued about.  Give it a day or two and see if it doesn't resolve itself.

---

### Post by Bachstelze on 2009-06-22
This is totally normal.

The reason you have some packages "kept back", is because the new version either depends on a package that is not installed on your system currently, or conflicts with one that is. So in order to upgrade that package, Apt would have to either install new packages on your system, or remove packages from it. [font="monospace"]apt-get upgrade[/font] *never* installs or remove packages. It just upgrades them, which is why if an upgrade requires installing or removing packages, it will just skip it and report the packages that couldn't be upgraded as "kept back". If you want to upgrade all your packages, which will require installing additional packages or removing some packages you have on your system, use [font="monospace"]apt-get dist-upgrade[/font].

In your case, the additional packages that need to be install in order to upgrade the [font="monospace"]linux-generic[/font] metapackage are simple the ones that contain the new version of the kernel.

---

### Post by Therion on 2009-06-22
> **HymnToLife said:**
> ... Enlightening Post ...
Thank you for your detailed explanation; it certainly filled in some of the gaps for me!  I'm glad to see I wasn't too far off.

How's the weather today in Bordeaux, by the way?

---

### Post by marciovinicius on 2009-06-22
> **Sxeptomaniac said:**
> I just put in sudo apt-get dist-upgrade, which is installing the blocked updates. I wish they would provide an easy way for kpackage to tell you how to fix the blocked updates problem. Telling me why they were blocked would be a good start for kpackagekit.

> **Therion said:**
> I hesitate to recommend other methods of "pushing through" the install if your chosen package manager is holding them back. That's my doubt. Specially because others package manager don't do this. BTW, that's not "my chosen package manager" it simply was already there, I thought it was good. And if I have to install entire Gnome (or only all its libraries) just to have a package manager, I'll leave KDE and go back to Gnome.

> **HymnToLife said:**
> [FONT=monospace]apt-get upgrade[/FONT] *never* installs or remove packages. It just upgrades them, which is why if an upgrade requires installing or removing packages, it will just skip it and report the packages that couldn't be upgraded as "kept back". If you want to upgrade all your packages, which will require installing additional packages or removing some packages you have on your system, use [FONT=monospace]apt-get dist-upgrade[/FONT].

That's the most reliable information I got 'till now. Although I still don't know what to do. 

I think I'll wait. The worst part is that I have no update notifier anymore since the one I have keep saying that I have a update I can't install. I'll never know when kpackagekit really mean it, now i have only manual updates.

Thank you all.

---

### Post by Bachstelze on 2009-06-22
Do a [font="monospace"]dist-upgrade[/font]. As I said, it will just install the new kernel.

---

### Post by marciovinicius on 2009-06-22
> **HymnToLife said:**
> Do a [FONT=monospace]dist-upgrade[/FONT]. As I said, it will just install the new kernel.Ok, i'll try. Thanks! ;) If i don't post anything else here, it's because everything went right.

---

### Post by galvao on 2009-06-23
Greetings. I'm having the exact same question as marciovinicius. I even posted another thread about the exact same thing (sorry about that). Can someone help?

---

### Post by galvao on 2009-06-23
OK, OK, finally got it, ran a distro-upgrade and everything is fine, but mannnn the whole damn thing was sooo confusing:

- When I've hovered the mouse over the control module icon in systray it said "You have **eight** upgrades"
- When I've opened the control module it said "You have **four** blocked updates"
- When I've expanded that it showed 2.6.28-**11** as the kernel version, but I've knew that the correct newer version was 2.6.28-**13**

C'mon, KDE guys... You can do a lot better than that!

---

### Post by automaton26 on 2009-06-23
If you install this kernel upgrade, don't you have to reinstall any proprietary graphics drivers afterwards ?
If so, I'll probably hold off from installing this for a few months, until there's a later ATI Catalyst driver that I can install, _at the same time_.

[if it ain't broke, don't fix I.T.]

---

### Post by Bachstelze on 2009-06-23
> **automaton26 said:**
> If you install this kernel upgrade, don't you have to reinstall any proprietary graphics drivers afterwards ?
If so, I'll probably hold off from installing this for a few months, until there's a later ATI Catalyst driver that I can install, _at the same time_.

Please don't spread FUD. If the ATi drivers worked with the old kernel, they **will** work with the new one, if configured properly.

---

### Post by automaton26 on 2009-06-23
> Please don't spread FUD

I'm sorry, but that first sentence was a genuine question - I was simply asking for advice.

So, thank you for confirming that doing a "dist-upgrade" will not affect my proprietary driver installation - I'll give it a try.

---

### Post by Bachstelze on 2009-06-23
> **automaton26 said:**
> I'm sorry, but that first sentence was a genuine question - I was simply asking for advice.

So, thank you for confirming that doing a "dist-upgrade" will not affect my proprietary driver installation - I'll give it a try.

Haha, sorry, not enough sleep last night I guess -_-

Anyway, yes, after a version of Ubuntu is released, the kernel updates are minor, so they shouldn't affect driver compatibility.

---

### Post by automaton26 on 2009-06-23
HymnToLife,

I use the proprietary ATI Catalyst graphics drivers, and after doing a "sudo apt-get dist-upgrade" I found that my machine would **not** boot when using that new kernel version. I had to boot into recovery mode and uninstall the ATI drivers by doing:

```
cd /usr/share/ati
sh ./fglrx-uninstall.sh

```

Finally, I had to install the latest ATI drivers again.

So, I was justified in asking for confirmation about proprietary graphics drivers, before trying a kernel version upgrade.

---

### Post by Sxeptomaniac on 2009-06-24
> **Therion said:**
> I'm going to stick my neck out a little and say that *usually* blocked packages are due to dependency issues.  What I do know from experience that simply chilling out on the situation for a day or two resolves the error.  In my experience it's not a "problem" at all; the packages have been put into Limbo for a reason.

I hesitate to recommend other methods of "pushing through" the install if your chosen package manager is holding them back.  I'm not saying "don't do it" - hey, it's your system - I'm just saying it's nothing to freaking come unglued about.  Give it a day or two and see if it doesn't resolve itself.

Actually, I already left the blocked updates sitting for several days, but got tired of that little icon sitting in the taskbar.  In the end, the upgrade did not make changes to any packages other than to "install" the new kernel-related ones.  Everything else was untouched.  I'm guessing that it considered this install the problem, but I don't see why, since adept and synaptic never gave me any trouble with kernel updates.

---

### Post by bigbencg on 2009-06-25
The aptitude code that Chronon did the trick for me.  Thank You!

Ben

---

### Post by stevedundee on 2009-06-28
sudo apt-get dist-upgrade worked for me. But very odd because this is a clean install of 9.04 (my attempt to upgrade from 8.10 having failed for reasons that were probably my fault...)

---

### Post by Chronon on 2009-06-28
> **bigbencg said:**
> The aptitude code that Chronon did the trick for me.  Thank You!

Ben

Heh.  You're welcome.  ):P

Just sharing the results of my own search.

---

### Post by mikerduffy on 2009-06-30
> **HymnToLife said:**
> This is totally normal.

The reason you have some packages "kept back", is because the new version either depends on a package that is not installed on your system currently, or conflicts with one that is. So in order to upgrade that package, Apt would have to either install new packages on your system, or remove packages from it. [font="monospace"]apt-get upgrade[/font] *never* installs or remove packages. It just upgrades them, which is why if an upgrade requires installing or removing packages, it will just skip it and report the packages that couldn't be upgraded as "kept back". If you want to upgrade all your packages, which will require installing additional packages or removing some packages you have on your system, use [font="monospace"]apt-get dist-upgrade[/font].

In your case, the additional packages that need to be install in order to upgrade the [font="monospace"]linux-generic[/font] metapackage are simple the ones that contain the new version of the kernel.

Thank you for this information.  I put off fixing this problem for about ten days, but this advice worked like a charm:

**[font="monospace"]sudo apt-get dist-upgrade[/font]**

---

### Post by malangaman on 2009-07-04
Worked for me too.
Thank You!

---

### Post by jimbog on 2009-07-07
I have the same problem with blocked updates, but when I tried the suggested dist-upgrade command, I got this message:

> The following packages cannot be authenticated:
libraw1394-11 libavc1394-0 libiec61883-0 libffado0 libfreebob0 libdc1394-22 libdc1394-22-utils

I then have the option to continue without verification.

Is this normal? I've tried waiting patiently for the blocked updates to become unblocked, but it's been over two weeks now and that update icon is starting to annoy me!

---

### Post by jimbog on 2009-07-08
Anyone?

---

### Post by jimbog on 2009-07-09
Oh well, looks like I'm stuck with the update icon in my taskbar for the foreseeable future then.

---

### Post by ColJep on 2009-07-12
I just came across the problem after trying Kubuntu yet again. I use Ubuntu as my main machine but regularly try Kubuntu. I was beginning to like Kubuntu at about KDE 3.5 but then came 4.x

I have not had a permanent Kubuntu system since then.

My latest attempt was with a clean install of 9.04 on a 2.6 GHz Athlon XP on a K600 motherboard and NVidia graphics card (no previous linux problems apart from not liking Kubuntu).

I got the four blocked updates and 116 normal ones as mentioned and therefore could not activate the NVidia driver.

Sudu apt-get dist-upgrade seemed to fix things but after the required reboot I can still not activate the NVidia driver.

UPDATE: I finally managed to get a request for my password to activate the NVidia driver. About sixth try. There was  no other way to enter Admin mode which does not seem correct.

Still not ready for general use in my opinion.

I could do it all through a terminal I suppose but then I would not be using Ubuntu/Kubuntu would I?

---

### Post by Chronon on 2009-07-12
> **jimbog said:**
> I have the same problem with blocked updates, but when I tried the suggested dist-upgrade command, I got this message:



I then have the option to continue without verification.

Is this normal? I've tried waiting patiently for the blocked updates to become unblocked, but it's been over two weeks now and that update icon is starting to annoy me!

Lack of verification points to keyring issues.  I googled for "the following packages cannot be authenticated" and found a [helpful page](http://changelog.complete.org/archives/496-how-to-solve-the-following-packages-cannot-be-authenticated).

The instructions there are for Debian, so I don't know that the exact suggestion there also applies here but it seems to point in the right direction anyway.

---

### Post by schnelle on 2009-07-12
Install synaptic package manager and click "mark all upgrades" and then "apply" and let him do the work.

---

### Post by rayclev on 2009-07-18
> **HymnToLife said:**
> This is totally normal.

The reason you have some packages "kept back", is because the new version either depends on a package that is not installed on your system currently, or conflicts with one that is. So in order to upgrade that package, Apt would have to either install new packages on your system, or remove packages from it. [font="monospace"]apt-get upgrade[/font] *never* installs or remove packages. It just upgrades them, which is why if an upgrade requires installing or removing packages, it will just skip it and report the packages that couldn't be upgraded as "kept back". If you want to upgrade all your packages, which will require installing additional packages or removing some packages you have on your system, use [font="monospace"]apt-get dist-upgrade[/font].

In your case, the additional packages that need to be install in order to upgrade the [font="monospace"]linux-generic[/font] metapackage are simple the ones that contain the new version of the kernel.
Thanks. That did the trick. 
Cheers. Ray

---

### Post by warb on 2009-07-27
> **smithers888 said:**
> I had exactly the same problem, and found (as Toxic Mite did) that
```
apt-get update
apt-get upgrade
```did nothing to help. However following Chronon's first suggestion, I used
```
aptitude full-upgrade
```which worked. I noticed that it also *uninstalled* two old packages. Perhaps the requirement to uninstall these was causing the block?


Great! worked for me.

---

