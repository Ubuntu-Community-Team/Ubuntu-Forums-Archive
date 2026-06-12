---
title: "ubuntu 9.04 screwed my system"
date: 2009-04-23
forum: General Help
---

### Post by mysoogal on 2009-04-23
this is just a little advice for users running ACER 5315 laptop 

please understand, that this version of ubuntu ubuntu 9.04 will break your setup conf files, compiz will not function right, if you have Lamp server installed that also will be little broken with mysql something about contoleruser.

i wish i read more, it seems also some drivers are black listed with the version ubuntu 9.04 so compiz wont be able to start, another issue is reinstalling compiz will really screw you with a black screen. 

this update has really screwed up even my xorg.conf every help page i read on this forum is about ATI, i checked into my laptop it says Intel based drivers, nothing i found on here help'd me fix issue in ubuntu 9.04. so i really do hope users with acer 5315 laptop don't make the mistake of upgrading to ubuntu 9.04. it's really not worth it. so since i'm using wubi installer i will install my fav ubuntu 8.10. again 

just like to note that everything worked so fine on 8.10, but this ubuntu 9.04 really sucks.

good luck and i hope you understand.:popcorn:

---

### Post by lisati on 2009-04-23
<sarcasm>So the many successful installations I've read about are a figment of my psychosis?</sarcasm>

Yes, we can all appreciate the frustration that happens when an installation doesn't go as smoothly as hoped. One of the things these forums are here for is to exchange advice and ideas when facing technical challenges: feel free to ask questions about your difficulties.

---

### Post by stwschool on 2009-04-23
The thread title is unfortunate but the replies are unnecessarily rude I think.

I'll take a guess you're using ATI drivers? ATI took their time producing drivers that were compatible with the latest version of x.org.

All I can say here is learn from this. My usual procedure with any major surgery such as this (and upgrading a distro is major surgery):

1. Back everything up to an external hard drive.
2. Install.

Simple really. Been doing that with Windows and Linux since the year dot. I've had installs go wrong of course, plenty of times on windows and quite a few times in my early linux days (I'm still not exactly a veteran but I've got most of the silly mistakes out the way) but never lost any data, and always got my system back how it was before. Easy if you know how.

---

### Post by mysoogal on 2009-04-23
> **lisati said:**
> <sarcasm>So the many successful installations I've read about are a figment of my psychosis?</sarcasm>

Yes, we can all appreciate the frustration that happens when an installation doesn't go as smoothly as hoped. One of the things these forums are here for is to exchange advice and ideas when facing technical challenges: feel free to ask questions about your difficulties.

the installation was successful, the issue was after that, 

compiz stop working !
monitor graphics blurry
Lamp server mysql php messed up
flash problem playing in fullscreen , probably beacuse driver was blacklisted ? no idea

it felt very bloated, 

so i installed compiz and bingo black screen every boot. 


so it was removed and i posted my findings here !

---

### Post by mysoogal on 2009-04-23
> **stwschool said:**
> The thread title is unfortunate but the replies are unnecessarily rude I think.

I'll take a guess you're using ATI drivers? ATI took their time producing drivers that were compatible with the latest version of x.org.

All I can say here is learn from this. My usual procedure with any major surgery such as this (and upgrading a distro is major surgery):

1. Back everything up to an external hard drive.
2. Install.

Simple really. Been doing that with Windows and Linux since the year dot. I've had installs go wrong of course, plenty of times on windows and quite a few times in my early linux days (I'm still not exactly a veteran but I've got most of the silly mistakes out the way) but never lost any data, and always got my system back how it was before. Easy if you know how.

yeah i would've done that from the start i have dual boot using Wubi could just backed up the ubuntu directory, but that was 13 gb big :O , my drivers are all  Intel i believe, i don't have ATI, that was one of the problems here on these forums, they always talk about ATI drivers xorg.conf etc, but i just wanted to know how to fix my monitor with drivers from Intel.

anyways i deleted ubuntu 9.04 wasn't that good in my opion, so I'm reinstalling ubuntu 8.10

---

### Post by mysoogal on 2009-04-23
> **LateNiteTV said:**
> ubuntu 9.04 sucks because you didnt read enough about it and your system didnt agree with it...? lmaooooooooooooooooooo sounds like you suck at preparing for an upgrade.
 
dont expect everything to *just work*.



preparing for an upgrade ? you mean by clicking upgrade to ubuntu 9.04 ? on the update manager ? that's what i did :confused:

---

### Post by LateNiteTV on 2009-04-23
making sure nothing has regressed, making sure the proper drivers are available etc etc.

---

### Post by dabl on 2009-04-23
> **mysoogal said:**
> preparing for an upgrade ? you mean by clicking upgrade to ubuntu 9.04 ? on the update manager ? that's what i did :confused:

Since 9.04 Alpha was available, there has been a thread in the Development forum here at Ubuntu forums (closed today BTW, but still available for viewing) and on that forum there were a lot of reports and discussion of problems with Intel graphics chips and the intel driver.  Being an Nvidia user, it didn't affect me, but it would have been very helpful to you to have reviewed how the testing users were doing, before pulling the trigger on your upgrade.

As I recall "UXA" and "EXA" are useful options for folks running the intel video driver in 9.04.  ;)

---

### Post by prssn on 2009-04-23
I have similar problems! Somebody please read my thread and help!

---

### Post by ACMiller on 2009-04-23
I have an intel graphics card that was hit hard by the new drivers in Jaunty when I upgraded. I had the same kind of graphics problems as mysoogal and prssn, fortunately after a bit of reading and some digging I found this page on downgrading to the previous intel drivers which worked perfectly (my compiz and flash are now smoother than ever!) 
I never fiddled with UXA or downloading the new kernel, but you may have to, just search these forums for what others have done. I guess I was just fortunate. Anyway, give it a try. Here's the link:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by prssn on 2009-04-23
Okay, I'm a totalt newbie to ubuntu. How do i open my sources.list? And do I just add those lines at the end or what?

---

### Post by paradigm2 on 2009-04-23
Well I put in Jaunty (when it was in beta) around early April on an Aspire 5100 series laptop.  I had some issues with it at first too.

-Sound caused a crash 30% of the time on startup.
-The ATI Xpress 200M card had a fps rate of ~250 fps.

It took some tweaking to get things better.

I ended up installing new versions of alsa, pulseaudio from PPAs.
Then I also ended up manually upgrading my kernel to 2.6.30rc3 (which also fixed my webcam).
Then I had to manually recompile and patch a mesa driver r300 to improve my video performance.

The above are all unofficial unsupported things but they are what it took to get it to work.

I think little problems like this are fairly common, but usually if you are willing to work a bit and take a chance on using later less supported versions, things can be fixed.

In my case my 9.04 main system works very well now.

---

### Post by paradigm2 on 2009-04-23
> **prssn said:**
> Okay, I'm a totalt newbie to ubuntu. How do i open my sources.list? And do I just add those lines at the end or what?

Well most people will tell you how to do it by command line but It think using Synaptic is better.

Go to System -> Administration -> Synaptic Package Manager.

Click Settings -> Repositories.

Click the "Third-party Software" tab.

This is where you will usually be adding repositories when someone tells you to on the forum.

You click add and then enter in the line which starts with deb <blah blah> whatever here>

Read this to learn Synaptic (Time well spent for a newbie!) :

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Also read:

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by prssn on 2009-04-23
Oh god, seriously... I need professional help. I followed the instructions [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) 
And now that I run sudo apt-get update it says
W: GPG error: http:ppa.launchpad.net jaunty Release: Following signatures could not be verified because the open key isn't available: NO_PUBKEY CE90D8 983E731F79

All i friggin' want is to get my Intel driver working!

---

### Post by SgtPepperKSU on 2009-04-23
> **prssn said:**
> Oh god, seriously... I need professional help. I followed the instructions [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) 
And now that I run sudo apt-get update it says
W: GPG error: http:ppa.launchpad.net jaunty Release: Following signatures could not be verified because the open key isn't available: NO_PUBKEY CE90D8 983E731F79

All i friggin' want is to get my Intel driver working!

I'm guessing you didn't follow the link in those instructions about adding GPG keys for the repository?

---

### Post by ubu-for on 2009-04-23
> **dabl said:**
> Since 9.04 Alpha was available, there has been a thread in the Development forum here at Ubuntu forums (closed today BTW, but still available for viewing) and on that forum there were a lot of reports and discussion of problems with Intel graphics chips and the intel driver.

This one?

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by mysoogal on 2009-04-23
> **prssn said:**
> Oh god, seriously... I need professional help. I followed the instructions [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) 
And now that I run sudo apt-get update it says
W: GPG error: http:ppa.launchpad.net jaunty Release: Following signatures could not be verified because the open key isn't available: NO_PUBKEY CE90D8 983E731F79

All i friggin' want is to get my Intel driver working!

i believe the problem is located here, 

[IMG]http://i40.tinypic.com/2lto6jb.png[/IMG]

you need to import key I believe, but it doesn't seem like its provided with that tutorial ?

---

### Post by mysoogal on 2009-04-23
ops you should read this [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

answer to your problem with adding key:KS

---

### Post by prssn on 2009-04-23
I'm to new to ubuntu to understand what you're saying unless you really explain straight through what you want me to do!

---

### Post by SgtPepperKSU on 2009-04-23
> **prssn said:**
> I'm to new to ubuntu to understand what you're saying unless you really explain straight through what you want me to do!

Open a terminal and type```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com a3351fa81504b601b2c196fcce90d8983e731f79
```
per the instructions linked to in the howto you provided.

---

### Post by Slim Odds on 2009-04-23
> **stwschool said:**
> The thread title is unfortunate but the replies are unnecessarily rude I think.

Funny that you would use the word "replies" to describe the **singular reply** prior to your own.

Titles like this one beg for some sort of rude reply. Saying that the new release "screwed my system" clearly implies that it's the releases fault.

How about just "my system is messed up after I tried to upgrade" or something like that? Don't make your frustration rub off on others. We come here on our own time and try to help.

---

### Post by mysoogal on 2009-04-24
> **Slim Odds said:**
> Funny that you would use the word "replies" to describe the **singular reply** prior to your own.

Titles like this one beg for some sort of rude reply. Saying that the new release "screwed my system" clearly implies that it's the releases fault.

How about just "my system is messed up after I tried to upgrade" or something like that? Don't make your frustration rub off on others. We come here on our own time and try to help.


hey, I waited nearly 1 hour to upgrade to this ubuntu 9.04 version after that it screwed up and wasted my time, and yes I believe it's the releases fault ! this new version seem to be working only fine on ATI type of computers with high end hardware.

---

### Post by Slim Odds on 2009-04-24
> **mysoogal said:**
> hey, I waited nearly 1 hour to upgrade to this ubuntu 9.04 version.....

That's not unusual, it does take a while...

> ...after that it screwed up and wasted my time, and yes I believe it's the releases fault ! this new version seem to be working only fine on ATI type of computers with high end hardware.I updated my nvidia based system with no issues.... it's possible that what seems to you might be incorrect.

Everyones case has the possibility of being different, but I have done many, many upgrades through the history of Ubuntu and I have to say that they do a fabulous job of making upgrades work. It's not a simple task and most OS's don't do any better.

---

### Post by ACMiller on 2009-04-24
> **prssn said:**
> I'm to new to ubuntu to understand what you're saying unless you really explain straight through what you want me to do!

OK, sorry I linked to that page earlier without giving any further advice on what to do. I hope this hasn't come too late. Alright, it sounds like you've already added the repository, but you just need to add the PPA key. To do this open a terminal (click applications > accessories > terminal) and type:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3E731F79
```

This adds the key for the repository you need. Then:

```
sudo apt-get update
```

And finally:

```
sudo apt-get install xserver-xorg-video-intel-2.4
```

This should downgrade you to the old intel drivers that seem to be working well for many intel users. You will need to restart X so log out and log back in and your new 'old' drivers should be ready to go. I hope this helps you. Cheers

---

### Post by mysoogal on 2009-04-26
hipp hippp hoooraaa i'm back to 8.10, ! been back to version 8.10 few days now and everything running back to normal !

is there a way to disable that upgrade to ubuntu 9 ? from update panal :O it's just i really dont want some of my friends to click there by  mistake ! or family members when i'm not around :O

---

### Post by ACMiller on 2009-04-27
You could go to your software sources (system > administration > software sources) and under the udates tab there is a section on release upgrades, if you set this to never it should keep it from notifying you of the new release. 
Glad you got yourself back up and working, cheers

---

### Post by ndefontenay on 2009-04-27
An upgrade to a new release is not a small job. Imagine upgrading from Xp to Vista lol. They don't even consider the option.

Personally I like a fresh install. I make sure to backup my system first and files (i got backups on external HDs anyway) and then I do the jump.

So far upgrades has always failed for me... I swear only by fresh install.

---

### Post by bacardiandwatermelon on 2009-04-27
Initially when I did an upgrade I did have a few graphics issues, but these were mainly aesthetic. After backing up my home directory and performing a clean install it fixed everything. Could be worth giving it a try.

---

### Post by Tom Mann on 2009-04-27
Please try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure your xorg to a default setting, which should (in theory) emulate a clean install.

:KS

NB: No need to fight, let's just solve this :)

---

### Post by Slim Odds on 2009-04-27
> **mysoogal said:**
> is there a way to disable that upgrade to ubuntu 9 ? from update panal :O it's just i really dont want some of my friends to click there by  mistake ! or family members when i'm not around :O

Why? Did you give them the password required to install stuff. If so, that's the problem.

Don't do that. Create a separate account for them.

---

### Post by aaronwinborn on 2009-04-27
> **Tom Mann said:**
> Please try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure your xorg to a default setting, which should (in theory) emulate a clean install.

:KS

NB: No need to fight, let's just solve this :)

So I've had the dreaded black screen after upgrading 8.10 to 9.04. Running this command solves the black screen, but now I no longer have a KDE desktop -- it drops straight to a command line prompt.

How can I get KDE back?

Thanks,
Aaron

---

### Post by mysoogal on 2009-05-01
after reading more about ubuntu 9.04 it seems, in this version the Intel integrated graphics card chip etc is black listed in ubuntu 9.04 the developers said something as not fully supported or open, funny my thoughts it runs well on ubuntu 8.10, i assume the developers are only thinking about specific hardware support which are not based on integrated graphics chips. maybe this is why things gone pretty pants with this version. :confused:.

anyway my thought is if things run well on ubuntu 8.10, things should run much better on ubuntu 9.04. but I'm not that disappointed 1 more year i believe of upgrades for ubuntu 8.10 ? :P until 

, reply to some other members here, my ubuntu set to auto login with password. i really hate it when i need to keep typing the same password so many times. even using the log out you need to type it again.:confused:

yes, i don't need to disable that upgraded to ubuntu 9.04 button, anymore it seems it only shows when the system needs to be updated so i set it to weekly. with manual download enabled :KS


well thats my experience with ubuntu 3 weeks since i started using it something like that.

you won't believe this, but i got my mothers Eee laptop running with ubuntu 8.10, I'm teaching my mum how to use it hahah :lolflag: so far she knows how to mirror screen to big hd tv lolz through VGA cable.

had to change her OS to ubuntu she was getting to many virus from those ugly pop-up sites. its been nearly 2 weeks she likes it now ! my mum is 52 years old lolz

---

### Post by mysoogal on 2009-05-02
> **aaronwinborn said:**
> So I've had the dreaded black screen after upgrading 8.10 to 9.04. Running this command solves the black screen, but now I no longer have a KDE desktop -- it drops straight to a command line prompt.

How can I get KDE back?

Thanks,
Aaron


i believe you need to reinstall ubuntu desktop


something like this sudo apt-get install ubuntu-desktop :KS

---

