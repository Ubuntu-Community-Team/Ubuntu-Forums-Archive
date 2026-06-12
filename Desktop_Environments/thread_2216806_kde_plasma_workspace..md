---
title: "kde plasma workspace."
date: 2014-04-14
forum: Desktop Environments
---

### Post by Twilk73 on 2014-04-14
Does kde plasma workspace come as a default option in ubuntu 13.10? when I go to log in it shows it as an option and I have no idea how it got there or if it was there from the start.

Anyway I am finding it extremely difficult to remove this option. I am not a fan of KDE and i just want to remove it. I have been searching the internet for almost 2 hours trying to find out how to remove it but i am coming up empty handed. The weird thing is I removed this option on another one of my laptops but I never saved the link describing how so I am lost. 

It seems as though I removed some of the files because a few things disappeared from the apps list. However, i still have the option to log on under the kde desktop. I am tired and frustrated at this point and also very confused as to why I cant figure this out but somehow I managed to figure it out on another laptop and I dont recall it being this difficult. 

As always thanks in advance.

---

### Post by 23dornot23d on 2014-04-14
It should just be 

**sudo apt-get remove kde-full **

But watch carefully for what it is going to remove ...........

personally - if its in the system then make sure you have fully understood why

its in your system as kdm could get removed too - which is the login manager

often this needs replacing with lightdm nowadays - if its not already setup

**sudo apt-get install lightdm**

if you think something might be being removed that you need - please post back

and see if anyone can help you further - before rebooting.

But thinking on - that if you have done it once already - you will know what to expect.

If the commands above were similar to what you used last time.

---

### Post by Twilk73 on 2014-04-14
I tried kde-full, kde-plasma-workspace, kde-workspace 

Nothing works yet. Thanks, for the tips though.

Iv managed to get back the ubuntu log on screen and remove a few kde items. However on the log on screen it still shows kde plasma workspace. On the other laptop I never even tried getting back the ubuntu screen I only tried removing kde. I recall the process being simple at most but my search is getting me no where and making a full out of me.

I am experimenting on this laptop for now if something gets messed up its not a big deal. Ill either reboot back to square one from USB or ill revert back to a save.

---

### Post by 23dornot23d on 2014-04-14
It probably depends on how it was installed in the first place - but

**sudo apt-get remove kde-minimal**

or use synaptic and search against kde

see if you can see what is installed there ......... maybe give us a screen shot to show what is there

but if you are experimenting and have a backup then maybe its not too much of a problem - what

I often do - is to ensure that the desktop that I do use is  reinstalled and the desktop manager is reinstalled

before rebooting .......... then I check as much as I can out before a reboot ........

But again depends on what you know and how well you can use the terminal / console should things not

come back as you wanted them to .

---

### Post by buzzingrobot on 2014-04-14
> **Twilk73 said:**
> Does kde plasma workspace come as a default option in ubuntu 13.10?.

KDE is not a default option installed in Ubuntu Unity.

If you installed a KDE package, especially a major KDE package, it is possible enough dependencies were pulled into trigger the addition of KDE as a login option.

Packages with names like "kde-full", etc., are meta-packages that map to many, often hundreds, of individual pacakges. They are intended as conveniences.  E.g. if you install kde-full, it installs the complete KDE system, about a gig's worth.

---

### Post by Twilk73 on 2014-04-14
I searched kde in synaptic and there are way to many files to not have things in the system be depended on kde. I am not sure if thats a result of something I installed or not. I am going to draw the white flag for the time being seeing as the system is running so dang smooth. 

Here is my issue maybe you guys can help. Basically I am optimizing the system to my liking and my liking is bare bones and fast as hell without loosing stability. Bare bones is probably not the correct term. Its more like bare bones system wise but ill still add in things I like, like cpufreq, unity tweak and so forth. 

Guys I havnt had windows on my home laptops in over a year. Even if I didnt like to tinker with everything Ubuntu is easy enough that I could have picked it up no problem. Anyway I am beyond happy I made the switch and am starting to learn the new language. I appreciate all the help you guys give on this forum.

---

### Post by su:bhatta on 2014-04-15
> **Twilk73 said:**
> Does kde plasma workspace come as a default option in ubuntu 13.10? when I go to log in it shows it as an option and I have no idea how it got there or if it was there from the start.


As pointed out by buzzingrobot, KDE packages are not installed by default.

Please try to remember if you installed any program that could have lead to the situation wherein it installed any of the 'Plasma-workspace/KDE-desktop' etc package.
Simply removing any of those metapackages will not help and you will get the KDE option in log-in screen.

If all KDE packages were installed in a single session then you can find out what all packages were installed using:

```
grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log
```

and remove them.

---

