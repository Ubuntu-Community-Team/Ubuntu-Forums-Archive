---
title: "Ubuntu vs Debian"
date: 2008-04-07
forum: Debian
---

### Post by Raccoon1400 on 2008-04-07
I am considering switching to debian.
My main reason is faster boot times.
Any suggestions?

---

### Post by SunnyRabbiera on 2008-04-07
Well by nature Debian can be much more stable and faster then Ubuntu, however its not for the beginner.
There is no real advantage using Debian over ubuntu other then stability, for ease of use you may want to use Mepis as opposed to Debian as it has a lot of stuff to make it easy...

---

### Post by Raccoon1400 on 2008-04-07
Debian does seem to be lighter.
Ubuntu takes about 256 MB ram.
Debian takes closer to 100-150 MB.

What is taking up the difference in Ubuntu?

---

### Post by Medieval_Creations on 2008-04-07
You could also try a minimal install of Ubuntu.  I use the alternate install cd and just install a command line system.  Then add packages and programs that I need.  This eliminates a lot of the overhead since there aren't any services running that you don't need / want.

You could also try a program called BUM (Boot Up Manager).  It lets you see what services are started at boot time and turn them off.

1 thing that oddly enough helped my system too, was removing "quite splash" from the grub menu.lst.

---

### Post by Raccoon1400 on 2008-04-07
I already use BUM. I like it because it lets me remove things services won't show me. I will try removing quiet splash. What does that do anyways.
If I don't switch, I will definitely try a minimal install.

---

### Post by SunnyRabbiera on 2008-04-07
> **Raccoon1400 said:**
> Debian does seem to be lighter.
Ubuntu takes about 256 MB ram.
Debian takes closer to 100-150 MB.

What is taking up the difference in Ubuntu?

well ubuntu has a lot of stuff preloaded on it, it uses certain drivers and such that debian doesnt have.
you are looking at the policy differences between the two on that one, debian is intended to be light on its feet.

---

### Post by Medieval_Creations on 2008-04-07
Off hand I don't remember what quiet does, but splash is the fancy loading screen that say Ubuntu.  So instead of the pretty you would see the kernel booting.

I prefer the minimal install, just because I get the benefits of the Ubuntu kernel but not all the bloat.  Plus you can try alternate window managers which will save a little no resources too... Example, I run SLIM as my Log-In manager & Fluxbox as my windows manager.  Which are much lighter than GDM & Gnome.

---

### Post by Raccoon1400 on 2008-04-07
I wouldn't mind not having the progress bar. Then I could actually see what it was doing.

I want to stick with gnome because it is simple and I know it.

Is a minimal ubuntu install going to be that different from debian?

---

### Post by KhaaL on 2008-04-07
correct me if I'm wrong, but dosen't debian roll out updates constantly? that is, no freezes and waiting 6 months for a new version of a program to get the latest version?

---

### Post by Medieval_Creations on 2008-04-07
> **Raccoon1400 said:**
> 
Is a minimal ubuntu install going to be that different from debian?

Not really.  If you start from a command line install, honestly it would probably be really close to the same.  Since Ubuntu is based off Debian, they really aren't that different.  Just Ubuntu has made good strides in trying to bridge the driver gap between Windows & Linux.

When I install Debian I do the same things.  Install a command line system with a netinstall cd and install all my packages from there.

The only thing I would suggest if you go with a fresh install is don't install gnome-desktop.  That will install all the other appz just like a normal install.  I forget the package off the top of my head, but when you go to install gnome, look for gnome-core, or something close to that.

---

### Post by Raccoon1400 on 2008-04-07
the splash seems to take off a few more seconds.
It is now 39 sec from power button to login.
However, it is 33 seconds from login to finished!!

---

### Post by Medieval_Creations on 2008-04-07
> **KhaaL said:**
> correct me if I'm wrong, but dosen't debian roll out updates constantly? that is, no freezes and waiting 6 months for a new version of a program to get the latest version?

I don;t know if what to call Debian's release cycle.  Their philosophy is, it's done when it's done.  Doesn't really matter how long it takes.  I'm sure they do have freezes, but it's more transparent to us, since they aren't locked into a 6 month release cycle.

---

### Post by qazwsx on 2008-04-07
> **KhaaL said:**
> correct me if I'm wrong, but dosen't debian roll out updates constantly? that is, no freezes and waiting 6 months for a new version of a program to get the latest version?
Depends. Testing and Unstable branches are rolling  releases.

For stable Debian Unstable experience I recommend sidux. Testing is more suitable for Gnome fans. KDE tends to be quite stable in Unstable (it still uses KDE 3.5 though. KDE 4 is in expermental side of Unstable branch).

---

### Post by Medieval_Creations on 2008-04-07
> **Raccoon1400 said:**
> the splash seems to take off a few more seconds.
It is now 39 sec from power button to login.
However, it is 33 seconds from login to finished!!

Never really clocked mine, plus I've installed different things that add to the boot time slightly.  Like samba, ssh, mysql & apache.

---

### Post by Raccoon1400 on 2008-04-07
I have installed xfce and kde, but don't use them. I wonder if parts of them are slowing it down.

---

### Post by visionaire on 2008-04-07
33 secs, that seems a lot to me, i'm using kubuntu, and from login to a full desktop just took a few secs

---

### Post by Medieval_Creations on 2008-04-07
> **Raccoon1400 said:**
> I have installed xfce and kde, but don't use them. I wonder if parts of them are slowing it down.

Possible, but I don't know if any of their libraries or systems would be running when you launch gnome.

---

### Post by K.Mandla on 2008-04-07
Moved to Debian discussion forum.

---

### Post by Raccoon1400 on 2008-04-07
I tested KDE. It took 17 seconds to load.
When hardy comes out, I am upgrading to 64 bit(unless I switch to debian) which requires a clean install. Maybe that will be faster, hasn't had time to accumulate junk.
It's not the machine it's self(2 GB ram, 1.6 GHz core 2 duo)

---

### Post by jdhore on 2008-04-07
> **qazwsx said:**
> Depends. Testing and Unstable branches are rolling  releases.

For stable Debian Unstable experience I recommend sidux. Testing is more suitable for Gnome fans. KDE tends to be quite stable in Unstable (it still uses KDE 3.5 though. KDE 4 is in expermental side of Unstable branch).

I wouldn't recommend Sid or Sidux for 95% of users...Sure, for 6 months, you may be surfin nicely, but one day, a "bad" update will come along and bork your system...Also, even running Sidux, you have to be careful and watch the updates.

---

### Post by Raccoon1400 on 2008-04-07
I wouldn't use unstable. If I switch, I am leaning toward testing.

---

### Post by jdhore on 2008-04-07
> **Raccoon1400 said:**
> I wouldn't use unstable. If I switch, I am leaning toward testing.

I would agree...I LOVE Testing and as of right now, it's almost (in some cases moreso) as up-to-date as Ubuntu Hardy.

---

### Post by Medieval_Creations on 2008-04-07
Ok, just for grins, since I wasn't really sure how long it took my PC to boot I tried it out when I got home.

From grub to login took about 27 seconds.  That's with quite a few extra services running as well.  (ssh, samba, mdadm, mysql, & hpoj (HP Printer Driver)).

From login to desktop took 3 seconds.  I use slim as my login manager & fluxbox as my windows manager.

---

### Post by Vorian Grey on 2008-04-08
> **Raccoon1400 said:**
> I wouldn't use unstable. If I switch, I am leaning toward testing.
I am using testing and it has been great. I'd recommend it to anyone.

---

### Post by NullHead on 2008-04-08
There is things like the policy kit that ubuntu hardy has and Debian doesn't and ubuntu has a better printer manager IMO. There are things like that witch really turn me to ubuntu. I do have 4 dvds of Debian lenny and it works good, but it lacks support for things like compiz and it also lacks drivers and flash support. 

Ubuntu has done allot of changing of the actual software they actually include in their OS where as Debian just seems to put the pieces together but doesn't seem to alter them much to make them more usable. 

I good example is; I use ubuntu hardy on my laptop and my father uses Debian stable on his. We just got a new Lexmard t632 laser printer and we have it connected as a network printer. I downloaded the .ppd for it installed it using the Ubuntu print manager and it works perfectly! My father however can't seem to print to it at all.... I even gave him the exact driver I used in Ubuntu, but with no avail. 

Also it seems to be almost impossible to make compiz work in Debian!! I got so mad when I was running Debian testing because it just doesn't seem to want to work! 

If you're looking for simple,  extreme, uber-stability than Debian is a great choice for you. I personally love Ubuntu and am very proud to be using it, witch is based off of Debian. :D

---

### Post by Medieval_Creations on 2008-04-08
Honestly, that is the main reason I'm using Ubuntu over Debian at the moment.  Canonical has made great strides in hardware/driver compatibility.

Another good example is my wireless card in my laptop (IPW2200).  Ubuntu comes with the firmware already installed and working.  In Debian I was able to get it to work, but took me some time to figure it out the first time.

Debian is still rock solid though and a great distro.  I still run it on my servers.

---

### Post by Raccoon1400 on 2008-04-08
> Also it seems to be almost impossible to make compiz work in Debian!! I got so mad when I was running Debian testing because it just doesn't seem to want to work!

I don't use compiz anyway. I have played with it from time to time, but I would rather save the space in RAM for something essential.

---

### Post by NullHead on 2008-04-08
Well it doesn't bother me loosing about 15mb of ram out of my 1.5gb. Other than that I like Debian, but it just lacks some functionality that Ubuntu offers. I also love Ubuntu's release cycle! every 6 months there is a new Ubuntu version always better than the last! (with the exception of edgy)

---

### Post by Medieval_Creations on 2008-04-08
I sometimes think the 6moht release schedule is a mixed blessing.  I like that there is a new version every six months, but as you pointed out Edgy was bug ridden and some of those could have been avoided with a longer testing phase.

I have no real complaints with Ubuntu and it has become the primary OS on my desktop & laptop.  Even got my wife to switch over to Linux.

I'm still a fan of the die-hards though.  I don't ever see me not using Debian or Slackware.

---

### Post by Vorian Grey on 2008-04-08
> **Raccoon1400 said:**
> I don't use compiz anyway.

Neither do I. I just don't see the use. I have 2 GIG of RAM, so that's not a problem. I just don't care for it. 

NullHead said...

> I also love Ubuntu's release cycle!
That's the main reason I'm not using Ubuntu at the moment. I hate it. Well, that and the fact my computer hated both 7.04 and 7.10.

---

### Post by Raccoon1400 on 2008-04-08
would building ubuntu from the base up reduce boot times, because I would only install what I need? Would it reduce ram usage significantly?

---

### Post by NullHead on 2008-04-08
Basically gnome its self take up a bunch of ram now a'days, but if you really wana save ram you can always use fluxbox (note use the command: update-menues before using flux) or xfce or something else like that. I now have a question about Ubuntu's ram usage ... how much ran does avahi use?

---

### Post by Medieval_Creations on 2008-04-08
Well by limiting the application and services install it should definatly help.  The question is how much and I really don't have an answer for that one.  Plus, performace is pretty subjective.  I could say that something flies & you could be like it's slower than anything you've seen.

---

### Post by tdrusk on 2008-04-12
Debian installs less even on its base install than Ubuntu does. Ubuntu is slightly easier to setup. If you have a brain you can use Debian, if you don't care as long as your system works you can use Ubuntu.

---

### Post by cardinals_fan on 2008-04-12
> **NullHead said:**
> I also love Ubuntu's release cycle! every 6 months there is a new Ubuntu version always better than the last! (with the exception of edgy)
Interesting.  I have never liked 6 month release cycles - rolling release makes more sense to me.  And I thought Edgy was better than Feisty and Gutsy...

---

### Post by kellemes on 2008-04-12
> **cardinals_fan said:**
> Interesting.  I have never liked 6 month release cycles - rolling release makes more sense to me.

Same here..
Rolling demands actual thinking before updating individual packages instead of blindly clicking some balloon and trust everything will be fine. That's a good thing, upgrading an os shouldn't be taken lightly.
Not being able to roll is one of the main reasons not to use Ubuntu for my main system.

---

### Post by cardinals_fan on 2008-04-12
> **kellemes said:**
> Same here..
Rolling demands actual thinking before updating individual packages instead of blindly clicking some balloon and trust everything will be fine. That's a good thing, upgrading an os shouldn't be taken lightly.
Not being able to roll is one of the main reasons not to use Ubuntu for my main system.
That's true.  I also like that a rolling release can be performed at **any time**.  When I run a dist-upgrade on Ubuntu, things will break - it isn't that the Ubuntu devs do a bad job, but the entire system is undergoing hundreds of significant changes.  With rolling release, I update my system often and never have a huge number of updates at once.  As for stability, my Zenwalk Snapshot (the* testing* wing of the repos) actually crashes less than most "stable" distros I've tried.  Go figure.

---

### Post by Vorian Grey on 2008-04-12
I've often wondered why Ubuntu doesn't have some way to have a rolling release structure. It looks to me like it would be less work on the devs as well. I don't understand the purpose of a new OS every 6 months.

---

### Post by hyper_ch on 2008-04-12
every 6 month a new release can also be used for marketing

---

### Post by NightwishFan on 2008-04-12
I still am fairly new although I can use a more advanced distro I prefer to just use Ubuntu for now, as it is simple.

---

### Post by Caraibes on 2008-04-12
> **Vorian Grey said:**
> I've often wondered why Ubuntu doesn't have some way to have a rolling release structure. It looks to me like it would be less work on the devs as well. I don't understand the purpose of a new OS every 6 months.
You sound like you are ready to use Debian Testing (I do)... It is just that... (you could also run Stable, and dist-upgrade every Stable release... this would be the reasonable choice, I do it on many boxes... but Testng is more fun !)

---

### Post by twist2b on 2008-04-13
I think Debian is alot more fun when building the OS. Its like building your own car from scratch. And you get the exact result you want.

Ubuntu is Pre-set for people less computer savvy. Though its still configurable.

Hardy Heron Is going to be a HUGE breakthrough since its actually the first Ubuntu for me that worked out of the box.
I like the 6 month life cycle aswell. Remember that there are bug fix updates and other updates that come along within that time period. And I just like how you get a huge growth instead of getting small things. Its fun to just take leaps, instead of walking.

I recommend both. But its really just what you like getting into. I find 1 is not better then the other.

---

### Post by Raccoon1400 on 2008-04-13
I installed debian testing to tri-boot along with vista and ubuntu. I plan to delete ubuntu when everything is working in debian.

---

### Post by NullHead on 2008-04-14
> **Raccoon1400 said:**
> I installed debian testing to tri-boot along with vista and ubuntu. I plan to delete ubuntu when everything is working in debian.

I hope you don't plan on using compiz .. I could never get it working. It is about the same though. You don't get the restricted drivers manager or a cool print manager either, but I look at Debian as more of an "old school" Linux distro ;)

---

### Post by Vorian Grey on 2008-04-24
In my opinion, with 8.04 Ubuntu has leaped so far beyond Debian as a desktop option that Debian is not even worth considering. 8.04 is simply amzing. Everything works out of the box for me and I think that's the first time any Linux has done that.

---

### Post by Cifra on 2008-04-24
> **Vorian Grey said:**
> In my opinion, with 8.04 Ubuntu has leaped so far beyond Debian as a desktop option that Debian is not even worth considering. 8.04 is simply amzing. Everything works out of the box for me and I think that's the first time any Linux has done that.
YOu'd be surpries in how many ways Debian surpasses Hardy.

---

### Post by Vorian Grey on 2008-04-24
> **Cifra said:**
> YOu'd be surpries in how many ways Debian surpasses Hardy.
Just not on the desktop, eh. ;)

---

### Post by notwen on 2008-04-24
Some machines have functions that I can only entrust to Debian.  They're too cautious in certain areas(ie. package stability and compatibility) and that's exactly what I'm wanting on certain boxes.  Running Etch on my file server and really don't see me changing it anytime soon, Debian Stable will always be running on my server boxes unless I discover something better to suit my specific needs.

---

### Post by jelkimantis on 2008-04-24
The primary problem with ubuntu is that it's more difficult to specifically configure.  If you have a 500mhz P3 with 512Mb RAM (like this desktop), there is no good ubuntu configuration.  You always get things which are too heavy, and trying to remove the heavy things can make the system unstable.

Building a netinst debian allows you to remove all the heavy stuff and run what you want.

I think ubuntu is great for modern equip and new users, but I think it's straying from home a little.  I understand why (they hate freedom ;-), ubuntu is filling the gap between uber geek users and newbies.  It's a nice distro, and it will make linux a reality for a lot of people.  

I think I'm done with ubuntu simply because the fiddle-factor is getting a little low.  It's too easy to mess something up on an ubuntu machine by attempting to do something silly like compile from source...

jsl

---

### Post by Vorian Grey on 2008-04-24
To be honest I think I'm fiddled out. I've been tinkering with Linux almost 2 years now and I just want something that works these days. It's been fun and all but I've realized that Gnome is Gnome no matter what distro I use. There is no perfect OS. Just use what works for you. 

My debian testing computer decided to tell me the other day that I didn't have a printer hooked up to it when I had just printed the day before. For some reason it lost my parallel port and said I didn't have one at all. Here I was in the middle of a huge report, so I had to stop and fiddle with it. I never did get it going. I finally lost my patience with it and formatted it. Ubuntu 8.04 sits on it now.

---

