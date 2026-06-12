---
title: "Feisty better than Gutsy?"
date: 2007-11-03
forum: Desktop Environments
---

### Post by eugenio_vb on 2007-11-03
I've tested Ubuntu 7.04 (Feisty) and Ubuntu 7.10 (Gutsy) and I have to say that Feisty is too many times better than Gutsy in a lot of aspects. I know Gutsy is newer and its packages are in the last version; however, I think and feel that Gutsy is not already finished or maybe fixed, the reason could be that Ubuntu Staff were too stressed because of the release date.

I have found the following bugs in Gutsy that makes it worse (Some users have not experienced this, but too many others have, including me):

1.- The login process is the main problem, it can take a lot of time to login, on the other hand, Fesity is faster. The problem has been identified as a mixture of problems like compiz enabled, DNS Ipv6, DHCP looping.

2.- Configuration files become corrupted randomly, for example, sometimes when GNOME is loading it doesn't apply the icon,text,theme configuration because it says that error has happened, then you restart and everything is ok. Moreover sometimes DBUS or HAL fail to initiliaze without reason.

3.- Internet speed is toooo slowwwwwwwwwwwww, the reason is linked with IPv6, but even disabling IPv6, internet is slower than feisty.

4.- Ugly background. When you start Gutsy there is an ugly brown/camel background, even if you change it with the desktop properties, the brown bg is still there. If you want to change it you have to do it modifying manually the config file.

5.- Compiz is more unstable, randomly compiz freezes without reason and tends to be slower and laggy, specially using built-in restricted drivers.

6.- The NVIDIA restricted driver (built-in in Gutsy) is a mess and a headache, if you enable it using the restricted driver manager, xorg.conf and kernel modules will be messed up for sure. To solve this you have to disable nvidia_legacy module and do a "sudo depmod". THIS IS NOT A FRIENDLY WAY TO DO IT IF YOU'RE A NEWBIE. In feisty you don't have to do that.

7.- JAVA slow, and don't have more words for this, simply java apps are slower.

There also more bugs reported, but these ones are the errors I've experienced AND THE MOST COMMONLY ERRORS THAT UBUNTU USERS ARE REPORTING. Sincerely, I am disappointed about Gutsy, I hoped something better.

IN MY CASE I'M USING FEISTY (WITH 2.6.23.1 KERNEL) ,AFTER THE SAD EXPERIENCE OF GUTSY. BEING OBJECTIVE, THE ONLY VISIBLE NEW FEATURE OF GUTSY IS GNOME 2.20, ALL THE OTHER FEATURES CAN BE EASILY ENABLED ON FEISTY, REMEMBER LINUX IS FLEXIBLE.

This is only what I feel, I'd like to know your opinions.

---

### Post by mrvertigo on 2007-11-03
it sounds like quite a bit of this is more personal prefrence and hardware limitation than bugs, if feisty works better on YOUR hardware then use that, if Gutsy is better for your tastes, then use that, thats the great thing about linux VS. proprietary you use what you feel is better for you!

enjoy your choice my friend, its a freedom only enjoyed when you contemplate not haviong it

---

### Post by rsambuca on 2007-11-03
I have been using Ubuntu since Dapper, and for me, without question the best release has been Gutsy.  I think it really is hardware dependent.

---

### Post by eugenio_vb on 2007-11-03
I respect preferences, and I don't have a hardware limitation:

Dell Insipiron 9400
Intel Core 2 DUO 2.0 GHZ
2 GB RAM
Nvidia Geforce 7900 GS GO
SATA HDD 120 GB 7200RPM
HDA Audio Intel
Intel 3945ABG Wifi.....

I've to say that is not just a personal preference, the problems I posted are the problems  that too many users are reporting in this forum, if you don't believe me check it by yourself.

---

### Post by OoooMatron on 2007-11-03
Weird, I do not have any of the problems you mention above at all. I've been testing gutsy since tribe 3 and have been mostly satisfied with it.

I did my clean install last week and it's defintely an improvement for me over feisty.

---

### Post by blueglue on 2007-11-03
Alot of the "advancements" in Gutsy & Feisty are quiet poncified aimed at windoze refugees and are more of a headache than they are worth. If it ain't broke don't fix it. Or use windoze.

---

### Post by mrvertigo on 2007-11-03
> **blueglue said:**
> Alot of the "advancements" in Gutsy & Feisty are quiet poncified aimed at windoze refugees and are more of a headache than they are worth. If it ain't broke don't fix it. Or use windoze.

This is the wrong way to approach this...... come on and get real, how exactly do we expect to attract new users and development money if we go around insulting the users we need to be nurturing?

---

### Post by ubukool on 2007-11-03
I've got a clean install of Gutsy and the one feature I think is really great improvement over Feisty is the ability to change the screen resolution.  On the other hand, I've got an Intel HDA soundcard and sound has been a problem.  I can't get sound with Skype or my virtual XP machine installed under VirtualBox.  This worked very well with Feisty, no problems at all.  I'm surprised eugenio hasn't had these problems, good luck to him!  The sound problems have had me thinking about going back to Feisty but hopefully I will find a solution if I keep looking - you've got to move forward.

---

### Post by cuby on 2007-11-03
Man... Linux is a work in progress, everybody has issues here and there.
Some of the things you say are true, namely some instability in compiz, bugy  nvidia drivers (The memory leak while running compiz is legendary) and trakerd is giving some pain in the ***.
BUT,
In my case, gutsy corrected several problems with my new hardware... Having  a new chipset under linux can be a pain.
I made the upgrade while in beta and it was painless.

This is without a doubt a better release. We get a lot of new cutting edge functionalities that can be really fine tuned for the next release with the cooperation of everyone... You know, it will be an LTS.

---

### Post by Gideon147 on 2007-11-03
Well I do have hardware limitations as it appears. Gutsy was a nightmare for me. 

The actual environment, however, I have little complaints to offer. The problem was in the Cube/Wobble compiz fiasco. Since M$'s Vista catastrophe I decided it was time to try and break free of their monopoly. I had been slowly converted over the years by Windows being everywhere I worked and played. So now I'm back. First install was a copy of Feisty I downloaded months back. Loved it. Now to sell my wife on it so I don't endure slow torture every time she touches the computer.

What sold her was the Cube/Wobble. She loved it. When I saw it was time to upgrade, I blindly did so. (M$ convert - remember). Bye bye cube/wobble. Bad things happened between Feisty and Gutsy that took it away.

While I employed fixes to get it back, they ended up breaking my system even further to the point where it was practically unusable. So I reinstalled a fresh full Ubunto Gutsy 7.10 from a Live CD. Same problem that I started with. I ended up just scrapping Gutsy altogether and going back to Feisty.

Gutsy may work for many, and for me, but it doesn't do what my wife wants it to. Which is a very important consideration. It's a problem that may be fixed in the future, or not. But I will be waiting in the midst with a fully functional Feisty in the meantime.

And coming from a M$ convert...the best way to compete with M$ is with driver support, compatibility, and definitely eye candy. Nobody wins a race by being good. They win only because they were better than the competition. People want to sit down at a computer and feel excited and and comfortable with their system. Anything that slows the process or in any way makes the computing experience uncomfortable will be a tragic blow. 

When many of you sit down at your Linux box you relate to the security, agility, and overall ability of the engine under the hood. Many people only see the hood and don't want to look underneath. They want to trust that the engine will run smoothly and that the OS will take them where they want to go, as fast as they want to get there. I'm using a car metaphor because it's JUST like designing a new vehicle. Those that care about the engine are not a majority group. Give it style.

---

### Post by reset3x on 2007-11-03
> **eugenio_vb said:**
> I've tested Ubuntu 7.04 (Feisty) and Ubuntu 7.10 (Gutsy) and I have to say that Feisty is too many times better than Gutsy in a lot of aspects. I know Gutsy is newer and its packages are in the last version; however, I think and feel that Gutsy is not already finished or maybe fixed, the reason could be that Ubuntu Staff were too stressed because of the release date.

I have found the following bugs in Gutsy that makes it worse (Some users have not experienced this, but too many others have, including me):

1.- The login process is the main problem, it can take a lot of time to login, on the other hand, Fesity is faster. The problem has been identified as a mixture of problems like compiz enabled, DNS Ipv6, DHCP looping.

2.- Configuration files become corrupted randomly, for example, sometimes when GNOME is loading it doesn't apply the icon,text,theme configuration because it says that error has happened, then you restart and everything is ok. Moreover sometimes DBUS or HAL fail to initiliaze without reason.

3.- Internet speed is toooo slowwwwwwwwwwwww, the reason is linked with IPv6, but even disabling IPv6, internet is slower than feisty.


4.- Ugly background. When you start Gutsy there is an ugly brown/camel background, even if you change it with the desktop properties, the brown bg is still there. If you want to change it you have to do it modifying manually the config file.

5.- Compiz is more unstable, randomly compiz freezes without reason and tends to be slower and laggy, specially using built-in restricted drivers.

6.- The NVIDIA restricted driver (built-in in Gutsy) is a mess and a headache, if you enable it using the restricted driver manager, xorg.conf and kernel modules will be messed up for sure. To solve this you have to disable nvidia_legacy module and do a "sudo depmod". THIS IS NOT A FRIENDLY WAY TO DO IT IF YOU'RE A NEWBIE. In feisty you don't have to do that.

7.- JAVA slow, and don't have more words for this, simply java apps are slower.

There also more bugs reported, but these ones are the errors I've experienced AND THE MOST COMMONLY ERRORS THAT UBUNTU USERS ARE REPORTING. Sincerely, I am disappointed about Gutsy, I hoped something better.

IN MY CASE I'M USING FEISTY (WITH 2.6.23.1 KERNEL) ,AFTER THE SAD EXPERIENCE OF GUTSY. BEING OBJECTIVE, THE ONLY VISIBLE NEW FEATURE OF GUTSY IS GNOME 2.20, ALL THE OTHER FEATURES CAN BE EASILY ENABLED ON FEISTY, REMEMBER LINUX IS FLEXIBLE.

This is only what I feel, I'd like to know your opinions.

Re-burn. Check CD for errors. re-install...

---

### Post by eugenio_vb on 2007-11-03
> **reset3x said:**
> Re-burn. Check CD for errors. re-install...

In fact, I've done that, the problem is still there, so it's a problem with the distribution, not with the cd.

---

### Post by arthpix on 2007-11-03
> **eugenio_vb said:**
> In fact, I've done that, the problem is still there, so it's a problem with the distribution, not with the cd.
Agree, i've Upgraded Xubuntu and didn't go, then downloaded and burned ubuntu... mdsum was right, also checked cd for errors, everything was fine. But Gutsy simply hanged my system with no reason every few minutes and filled my hardrive with crap. got foolish myself looking for a clue in all the system logs, but everything seemed ok. All I could do was send many automated crash reports.

Wonder why in this poll both "upgrade/install -got many problems that i wasn't able to solve" options almost double the amount of the "worked flawlessy" ones?
[http://ubuntuforums.org/showthread.php?t=580852]("http://ubuntuforums.org/showthread.php?t=580852")

Im a happy ubuntu user since Hoary, now i'm back to Feisty and everything goes great, as always. I did solved many issues before, even when i was a newbie...

Really hope things goes better, Our beloved Ubuntu deserves it.

---

### Post by Knyven on 2007-11-03
We should help with the Beta testing in the next version.

I will test it with my 3 pc and 1 laptop. The last time i did was on Dapper.

---

### Post by spier on 2007-11-03
> **arthpix said:**
> 

Im a happy ubuntu user since Hoary, now i'm back to Feisty and everything goes great, as always. I did solved many issues before, even when i was a newbie...

Really hope things goes better, Our beloved Ubuntu deserves it.



I'm going to follow you. Using ubuntu since breezy, almost everything worked like a charm,even   thru upgrades,  until gutsy. Then, I first lost hibernate ability. Now, maybe due a hard try to get the hibernate back, I lost my sound. Weird.  Maybe  I have to use a more stable distro, maybe Feisty!?

---

### Post by rsambuca on 2007-11-03
> **arthpix said:**
> Wonder why in this poll both "upgrade/install -got many problems that i wasn't able to solve" options almost double the amount of the "worked flawlessy" ones?
[http://ubuntuforums.org/showthread.php?t=580852]("http://ubuntuforums.org/showthread.php?t=580852")


You have to take any polls in the forums with a grain of salt.  The reality is that other than a few weirdos like myself, the majority of people coming to the forums are trying to solve problems.  Therefore, naturally these people are more likely to be 'having problems' of some sort.  It is a skewed audience viewing the poll in the first place.

The bottom line is that linux drivers are always going to be an issue, until vendors open-source the drivers.

---

### Post by HowlingAtTheMoon on 2007-11-03
I am pretty new to Linux, less than a week, but don't see myself as a "windoze refugee".
I am enjoying the experience, and learning a hell of a lot about my computer, and about Linux.
Gutsy is friendlier than any windows OS, and I haven't experienced any of the problems reported in the forums.
All the problems I have had have either been self-created, created by an exuberant toddler, or not knowing what questions to ask in response to a problem.

---

### Post by qamelian on 2007-11-03
> **rsambuca said:**
> I have been using Ubuntu since Dapper, and for me, without question the best release has been Gutsy.  I think it really is hardware dependent.

I agree. On my gear, Gutsy has been the best, most trouble-free release since Breezy.

---

### Post by madsmeg on 2007-11-03
Yes i have lost some eye candy (compiz cube etc) but am not having any problems with this distro, it installed flawlessly and had many more convenient options than feisty. i have had less problems with compatibility with gutsy than i had with feisty.

And welcome to the forums Howling :) 

Teh Smeg

---

### Post by tech0007 on 2007-11-03
I disagree.  It's hardware-dependent.I was on Feisty and it 'just worked.'  Gutsy is the BEST release ever.  Thanks to the Gutsy developers!

---

### Post by arthpix on 2007-11-03
> **rsambuca said:**
> You have to take any polls in the forums with a grain of salt.  The reality is that other than a few weirdos like myself, the majority of people coming to the forums are trying to solve problems.  Therefore, naturally these people are more likely to be 'having problems' of some sort.  It is a skewed audience viewing the poll in the first place.

The bottom line is that linux drivers are always going to be an issue, until vendors open-source the drivers.

I have to agree with you about that, I didn't see that point before.

Also Knyven, you are right too, even I always done my best to promote Ubuntu with my friends and every people Ikow here in my city, never have involved enough in testing. Will take care of that for Hardy.

My brother, who doesn't know aniything about computers did the upgrade without even noticed and everything worked like a chram! :confused:

I have to say i was about to try Gentoo,:oops: but better spend my time trying to solve issues with gutsy in another partition rather than learning Portage wich is a total strange to me.

---

### Post by jatoo on 2007-11-07
Unfortunately I have to say that I too am disappointed with Gutsy. Feisty was my first experience with Ubuntu, and I was so pleased with the way it started up so quickly, installed so easily and everything that worked, 'just worked' (there were things that didn't work however.)
On the other hand, gutsy has really been worse in all of these regards. I simply could not get the upgrade to work so eventually downloaded the CD and did a fresh install, which was enough trouble in itself. I have been having many problems, including things like hibernating, but it is also just a lot slower. Takes quite a while to start up, just like Windows...

Honestly I think Gutsy has a lot less reasons to use over windows, than feisty did.

On the other hand, what features will I be missing out on if I switch back to Feisty? There hasn't been anything I've noticed so far, but I'm worried there could be important things that I may need in the future.

---

### Post by TeaSwigger on 2007-11-07
I like the name *Feisty Fawn* more :)

---

### Post by TeaSwigger on 2007-11-07
> **jatoo said:**
> Unfortunately I have to say that I too am disappointed with Gutsy. Feisty was my first experience with Ubuntu, and I was so pleased with the way it started up so quickly, installed so easily and everything that worked, 'just worked' (there were things that didn't work however.)
On the other hand, gutsy has really been worse in all of these regards. I simply could not get the upgrade to work so eventually downloaded the CD and did a fresh install, which was enough trouble in itself. I have been having many problems, including things like hibernating, but it is also just a lot slower. Takes quite a while to start up, just like Windows...

Honestly I think Gutsy has a lot less reasons to use over windows, than feisty did.

On the other hand, what features will I be missing out on if I switch back to Feisty? There hasn't been anything I've noticed so far, but I'm worried there could be important things that I may need in the future.

It isn't so much features as the underlying chains of dependencies which would limit what you can build / install on it in future. It's not a factor to me for the time being; I could probably be happy waiting for the Heron. But eventually it can become limiting if you have an old overall system underneath and want new apps and/or new versions of apps.

What sort of ram do you have? It seems as if Gutsy requires more. I don't think the boot time of a full linux distro like ubuntu vs. windows is any advantage, rather it's in needing to reboot less. ;) Have you profiled the boot? That does tend to speed subsequent boots.

---

### Post by jatoo on 2007-11-07
I think I'm gonna dual boot anyway when I get round to it. Theres a bunch of programs I use for uni that I just cant get in Ubuntu unfortunately, (like Matlab, AVR studio etc.)

You are right though, I reboot far less in Ubuntu than Windows. But I do think Feisty was better in that regard too.

As for RAM, I'm using a 1yo laptop, and its got 494.4MB according to system monitor. 

What exactly is boot profiling?

---

### Post by TeaSwigger on 2007-11-07
Oh I understand. Right now I dual boot 'cause of the scanner.

That's a good amount of ram - perhaps ~512mb minus the memory shared with an integrated graphics card? An integrated graphics card can be a limitation, in that if your Gutsy setup is using fancier / more memory intensive graphics anywhere than your Feisty setup was, you may notice a slowdown even though you have enough ram otherwise. Just a thought.

Boot profiling in this case basically collects stuff accessed during boot into a cache and uses that, thus taking less time to read it all. How to do it:

- At the GRUB screen, select the main ubuntu kernel line you'd normally boot.
- Press the 'e' button (for Edit).
- At the end of that ubuntu kernel line, you'll probably have 'quiet splash' there, add on the word profile. That'll just add it this once.
- Press enter to accept.
- Press the 'b' button (for Boot).

That's it. This boot will take longer as it gathers the info. The next times you boot up it'll boot a bit faster or at worst won't make much difference (does no harm). You don't have to repeat this until, optionally if you want to keep any speed advantage, there's a major update like a new kernel update. Then just repeat once as above and it'll redo it. :)

---

### Post by Jouke74 on 2007-11-08
(rant on)
I have to agree with the topic starter, it seems that Gutsy Gibbon was rushed out on time and as compared to Feisty it has more small flaws / bugs in configs etc. These things are often simple to corect once you know where they are, but are a pain in the *** to track down.

1. GDM camel color is caused by the fact that the gdmserver authentication fails. The option -a needs to be added behind the server start lines to avoid it. Or the nasty way, change the background color of the part that shows the error (current camel). File = etc/gdm/Sessions/Default

2. Mousecursor cannot be changed under Xubuntu using the menus. Someone appearantly forgot to put root usage rights in front of the script that adjusts the config. Through the terminal using sudo to change the Xserver theme goes fine.

3. Many problems with restricted drivers and the splash screen of ubuntu resulting in black screens.
This should have been checked, especially if you are working on X-server autoconfig. By removing the splash from your Grub boot line I can save more than 30 seconds of boot time, why?????

4. Wireless is again different to set-up. With 3 different distributions it required 3 different methods.

5. Compiz still is alpha software, hence bug-prone. Memory leaks, XGL issues for ATI owners using the Ubuntu fglrx driver etc. Why make this standard for all people out of the box? Desktop effects are nice yes, but are eating many resources and cause a lot of problems, also to other programs. If you have to install this yourself, at least you know what you are getting yourself into :-) (I hope).

6. If I exit Gutsy Xubuntu my computer sometimes hangs. I still don't know why. 

7. Speed issues. Xubuntu never was so slow. Tracker anyone?

8.... Many more which I can't remember now. Includng themes that fails, icons that are not loaded, VLC player movie distortion. 

Not all changes are improvements, simply. 

If Hardy Heron is working good, I will still upgrade to this verion. Afterwards I wont upgrade anymore. It takes too much time to get everything the way it was before the upgrade.

On the good side: printer was straight supported, wireless was actually easier to setup, the buggy xfce-process manager was dropped for the gnome system manager (thank you) and small other improvements as well (e.a. Kompozer in the repro's).

My suggestion is to move the release candidate to three weeks earlier. Many bugs are reported after the release of the candidate, and even a no-IT-expert can see that these cannot be solved before the release date of the "final" version.
(rant off)

---

### Post by Nonno Bassotto on 2007-11-08
Feisty better than Gutsy? You can bet it!

---

### Post by eugenio_vb on 2007-11-11
> **Jouke74 said:**
> (rant on)
1. GDM camel color is caused by the fact that the gdmserver authentication fails. The option -a needs to be added behind the server start lines to avoid it.
(rant off)

What do you mean with that solution? Could you explain more about it?

---

### Post by santiagoward2000 on 2007-11-11
> **Nonno Bassotto said:**
> Feisty better than Gutsy? You can bet it!

Well, I wouldn't bet it... I have had no problem at all with my Gusty (Xubuntu), and I love all the new features.

---

### Post by Jouke74 on 2007-11-12
@santiagoward2000 somehow I have the feeling that your problems are there but you haven't really noticed them. They are not show stoppers for sure. Anyway, be happy, I am as well. There are also improvements for sure. But I really think that Gutsy is more experimental and definitely not "LTS material."

@eugenio_vb


Color only fix GDM:
=================
The way I did it, instead of using the zip file that is attached is to :

vim /etc/gdm/PreSession/Default

Scroll all the way to the bottom and find this little block of code :

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"
fi

I already changed mine, #000000 is black, the ugly tan has a d in the hex value.

It seems like it fails to grab the color from the gdm theme, not sure if it is a "bug" or just something you have to change if you really hate tan.


Real fix (authentication):
================

First fix was only working when already authenticated (gdmflexiserver): the following fix should work for EVERYONE :-)

Affected File (in gutsy):
/etc/gdm/PreSession/Default

Reason:
Authentication missing

Fix:
replace every "gdmflexiserver" whith "gdmflexiserver -a"

Comment:
This could be a problem in other places besides this file also (leading possibly to other bugs).

---

### Post by zippy028 on 2007-11-12
I am quite happy with Gutsy. I didn't use Feisty very much so not much comparison. I installed Feisty and had a lot of freezes and did not research for a cause/solution just went back to Breezy. I have had to remove the latest Nvidia driver and un-installed the restricted driver manager and manually installed an older version of Nvidia driver and I have compiz running with tons of special effects and I have no problems. I am actually getting kind of bored of Gutsy "just working."

---

### Post by santiagoward2000 on 2007-11-12
@Jouke74: Well maybe I should just be thankful, but I haven't had a single problem with Gusty (exept something with Pidgin, but I tried my Feisty LiveCD and got the same problem).

---

### Post by Don9307 on 2007-11-12
> **eugenio_vb said:**
> I've tested Ubuntu 7.04 (Feisty) and Ubuntu 7.10 (Gutsy) and I have to say that Feisty is too many times better than Gutsy in a lot of aspects. I know Gutsy is newer and its packages are in the last version; however, I think and feel that Gutsy is not already finished or maybe fixed, the reason could be that Ubuntu Staff were too stressed because of the release date.

I have found the following bugs in Gutsy that makes it worse (Some users have not experienced this, but too many others have, including me):

1.- The login process is the main problem, it can take a lot of time to login, on the other hand, Fesity is faster. The problem has been identified as a mixture of problems like compiz enabled, DNS Ipv6, DHCP looping.

2.- Configuration files become corrupted randomly, for example, sometimes when GNOME is loading it doesn't apply the icon,text,theme configuration because it says that error has happened, then you restart and everything is ok. Moreover sometimes DBUS or HAL fail to initiliaze without reason.

3.- Internet speed is toooo slowwwwwwwwwwwww, the reason is linked with IPv6, but even disabling IPv6, internet is slower than feisty.

4.- Ugly background. When you start Gutsy there is an ugly brown/camel background, even if you change it with the desktop properties, the brown bg is still there. If you want to change it you have to do it modifying manually the config file.

5.- Compiz is more unstable, randomly compiz freezes without reason and tends to be slower and laggy, specially using built-in restricted drivers.

6.- The NVIDIA restricted driver (built-in in Gutsy) is a mess and a headache, if you enable it using the restricted driver manager, xorg.conf and kernel modules will be messed up for sure. To solve this you have to disable nvidia_legacy module and do a "sudo depmod". THIS IS NOT A FRIENDLY WAY TO DO IT IF YOU'RE A NEWBIE. In feisty you don't have to do that.

7.- JAVA slow, and don't have more words for this, simply java apps are slower.

There also more bugs reported, but these ones are the errors I've experienced AND THE MOST COMMONLY ERRORS THAT UBUNTU USERS ARE REPORTING. Sincerely, I am disappointed about Gutsy, I hoped something better.

IN MY CASE I'M USING FEISTY (WITH 2.6.23.1 KERNEL) ,AFTER THE SAD EXPERIENCE OF GUTSY. BEING OBJECTIVE, THE ONLY VISIBLE NEW FEATURE OF GUTSY IS GNOME 2.20, ALL THE OTHER FEATURES CAN BE EASILY ENABLED ON FEISTY, REMEMBER LINUX IS FLEXIBLE.

This is only what I feel, I'd like to know your opinions.

I've used Feisty and Gusty now on my Presario V5000 laptop and I can't agree with you.  I've had no problems as you have described.  Boot-up and the internet couldn't be faster.  Sorry.

---

### Post by qamelian on 2007-11-12
> **santiagoward2000 said:**
> Well, I wouldn't bet it... I have had no problem at all with my Gusty (Xubuntu), and I love all the new features.

I agree. In fact, Gustsy is the first time sound has worked 100% right on my laptop since Breezy. It's also the first time hibernate has worked correctly for me as well.

---

### Post by brodiepearce on 2007-11-12
I can't agree more... so far I've spent an entire day trying to get Gutsy running, only to have to repeatedly reinstall over the top.  Even from the beginning the grubs menu options are pointing to the wrong HDD, and my services don't start.

I know quite a few people who decided to try Ubuntu for the first time when Gutsy came out and were sorely disappointed.

---

### Post by Goronok on 2007-11-12
> **qamelian said:**
> I agree. In fact, Gustsy is the first time sound has worked 100% right on my laptop since Breezy. It's also the first time hibernate has worked correctly for me as well.

I'm with you,  Gutsy has been the first release i've been able to get my sound to work as it should.  I personally love Gutsy and find it runs much better than any other release with my hardware.

---

### Post by Goronok on 2007-11-12
> **brodiepearce said:**
> I know quite a few people who decided to try Ubuntu for the first time when Gutsy came out and were sorely disappointed.

Gutsy isn't all that far different than Feisty, to be completely honest.  No MAJOR updates,  no major changes in my opinion.  If they didn't like Gutsy, they wouldn't have liked Feisty either.

---

### Post by seachnasaigh on 2007-11-12
I've used ubuntu for a while ... Breezy, Dapper, Feisty, now Gutsy ... I have to say I haven't seen any major problems with Gutsy apart from not working with a liveCD in persistent mode the way Dapper did. Sound didn't work initially (laugh if you wish) because I had the sound turned off from the manufacturer's keyboard shortcut. I felt like an idiot BUT was impressed that Gutsy respected the hw mfgr settings so well. I'm a sysadmin, not a desktop enthusiast, so I can't comment well on various folks' problems with compiz not working quite right. I rely on a nice clean desktop, a solid crossover connexion to my switches and routers, and trustworthy tools like vim and wireshark and helix to solve problems. I like them to work and under Gutsy, they do, and flawlessly. 

I don't use a high end machine ... specs follow. It is, however, not the standard desktop replacement or road warrior laptop, and Gutsy has handled its hardware far better than Breezy did, and marginally better than Dapper did. I don't notice a whole lot of difference between Feisty and Gutsy. My USB Palm Pilot works better now, which is a blessing.

Panasonic Toughbook W-2 standard Intel chipset, Intel graphics, 1.2MHz Pentium-M, 1 GB RAM 40 GB HD.

---

### Post by revolutio on 2007-11-12
Xubuntu user weighing in here.

I first started using Xubuntu with Feisty (it was my first time trying a complete shift to Linux).  I had the usual array of problems for someone new to an operating system and many things flat out didn't work.  I was gradually working through these when Gutsy came out.  Now I can't even count the number of issues I have.  Heck I've already shrunk my Xubuntu partition and am exploring other operating systems since this is unusable.  I was going to start posting about all the problems that cropped up but I wouldn't even know where to start.

I will give a fresh install of Feisty a shot since I didn't have much experience with it to compare.

---

### Post by Jouke74 on 2007-11-13
> **Goronok said:**
> Gutsy isn't all that far different than Feisty, to be completely honest.  No MAJOR updates,  no major changes in my opinion.  If they didn't like Gutsy, they wouldn't have liked Feisty either.

That is not true. Many packages have had updates. Gaim = Pidgin for example, Gimp, Gnome etc. 
Also the "monitor tool" that they introduced changes xorg.con. I assume the reason for many Nvidia and ATI driver issues for people that have more exotic hardware.

Anyway, like I said, there are no Gutsy problems that are really big issues. Just small bugs. Xubuntu Gutsy is running fine on my machine now, but it required some tinkering here and there. The same was true for Feisty by the way.

---

### Post by webdr on 2007-11-13
**IMHO**
Canonical's aggressive release schedule has been a significant factor in rapidly preparing Linux for the typical user desktop environment. Remember Microsoft has had >two decades of dictating to hardware companies how hardware should function and those same hardware companies have not always played nicely with the Linux community.

The Ubuntu development team and open source developers everywhere deserve a salute of respect for bringing to fruition an operating system and extensive scope of applications which allow us end users TRUE freedom of choice.

:popcorn:

Gutsy is the first one to just plain work with my laptop's video card, as well as the atheros wireless seems to be working much better. Whilst there are some bugs that carried over from feisty (the cypress_m8 module still doesn't work properly with the Delorme LT-120 w/o being modified and recompiled) the beauty is what is being achieved.

I wish that I had jumped over to the Linux side of computing in the late 90's when I first discovered it. So far though, I have to say that Gutsy is the choice distro for myself.

-Mark Williams

---

### Post by modestmelody on 2007-11-13
Gutsy actually fixed some random problems that had developed over time in my Feisty install.

It was a great release from my stand point.  I just was smart, waited a week, saw what conficts people were running into (i.e. not uninstalling all of Compiz, which seems obvious to me, before upgrading), etc.

---

### Post by Ifrgtmyname on 2007-11-13
i have noticed that java apps and internet are running slower but im no sure whether that is related to my bandwidth usage. One thing that has annoyed me a bit is that my previously beryl, now compiz bug with blank screens have returned and i honestly can't find the time to search for the solution. I like the dual monitor support plan to get that working too when i find time :roll:...

---

### Post by seachnasaigh on 2007-11-14
Having read through the thread a little more closely, I'd be really interested to see how many of the problems associated with Gutsy are fresh installs, and how many are upgrades. Over the years I've had mixed results upgrading Linux from one distro to another, even different versions within the same distro. Typically I do installs from scratch every time I upgrade, and have found this to be superior to following an upgrade path. Thoughts?

---

### Post by dave61430 on 2007-11-14
The car analogy is not a good one. The wife, kids and the dog are easily transferred to the new vehicle. I can't be sure what wine might do for me since I have to install a larger hd, but so far nothing I've tried in wine works. There are some windows apps I don't want to give up, so it's dual boot. Actually, dual boot is not nearly as inconvenient as it sounds.

I'm having trouble with anything but 6.06.1 which is installed. Normally, 7.04 or 7.10 live cd will run for some time then re-boot, can't even keep running long enough to install.

Having said that, this post is using Gutsy live cd and it's been up for about an hour. When I get new hd, I'll be able to play with both and get a better handle on what's happening. I've also got another 512mb to install when I get hd. But I have 512mb now with shared video so I would have thought ram shouldn't be the problem. Gutsy prints a more accurate test page than 6.06.1 (get's top and bottom margins better from test page).
Dave Cohen

---

### Post by dave61430 on 2007-11-14
My post is appearing in wrong place. Belongs I believe at end of page 1. Sorry about that.
Dave Cohen

---

### Post by kshane on 2007-11-14
Hi All!

Gotta throw my two cents in here. I started using Feisty in June this year.  Never used ANY Linux distro before.  I HAVE used Linux through the terminal over the net in my stint doing HTML development.  Due to that, I was rather turned off on Linux in general.  But, being one of the first *IDIOTS* to buy** Vista**, I was so disgusted that I went looking and found Ubuntu after some rather exhaustive research.  I have to say I LOVE Ubuntu!  

Feisty was good.  Had no problems so long as I didn't try to get fancy, but when I tried to run Compiz (have an ATI X1650) it was a serious drag.  But, after upgrading (I upgraded to Gutsy - not a clean install) to Gutsy and installing the new ATI driver (8.42.3) I was FINALLY able to run Compiz!  It does slow my system down somewhat, but it works and is such a nice enhancement that I have kept Compiz running and am used to the slight sluggishness and the occasional glitch (very occasional).  

All in all, I am very happy with Gutsy.  I see it as a vast improvement over Feisty and a phenomenal replacement for Vista.  It is rather intuitive, stable, eye-catching and fun!  In fact, I have a hard time just getting up  and away from my 'puter!

I am trully surprised at the original post.  I have been helping a lot of new users with their problems and am very aware that there are some issues with Gutsy, but most are easily rectified and, quite honestly, many are self induced.  There are some driver issues (not Ubuntu's fault) and other chronic problems, but the developer4s deserve a hardy round of serious applause for their accomplishments!  This is an astounding piece of work!  I for one will never leave Ubuntu.  I tested other distros, such as Gentoo, Suse, Sabayon, Elive, Mint, Slackware, Mepis and others.  Gutsy just works the best for me.  Maybe some of the others would have worked as well had I put more time into them, but Ubuntu/Gutsy just works well.

<stepping off the soap box>

Kevin

---

### Post by jmslouie on 2007-11-15
Hi to all,

I am having problems also in gutsy which i haven't experience yet in feisty. to be honest i still can't make my gutsy installed laptop to work properly. But i think i will stick in using gutsy because there would be a wide support for it and there would be fixes to my problems. I think the problems that i encountered are due to my hardware capability. I really enjoyed using Feisty, but i think Gutsy will be much better, just waiting for the bug fixes. 


Here are the problems that encountered in gutsy:
  - sounds after showing the login infinitely repeats, happens most of the time but not always
  - playback of video shows only gray stripes but sound is good, maybe because of my ATI graphic card
  - flickering of screen
  - sometimes when i boot up my laptop, it doesn't load ubuntu, it requires me to force reboot

something that i am looking for gutsy
  - i don't know if they really remove the loading ubuntu in boot, i personally need that because what i see is just a black screen for about 40 sec, i don't have the idea if ubuntu is still loading or not


I will wait for the Gutsy fixes to these bugs. but if you know some fixes to these bugs, i will really appreciate your help

Best wishes to all

---

### Post by Newbie1978 on 2007-11-15
I'm still thinking about going over board with this new version but some of the comments are not the best to say the least, I'm currently running on dual boot vista/Ubuntu ultimate 1.4 (feisty fawn Ubuntu version 7.4) and for the most part works good, some problems here and there but nothing mayor, I always like to have the latest but with Gusty... well I'm not sure yet, I think I will give it a go before dismissed it completely since I'm already downloading it, if someone have similar specs as mine I will appreciate your insides and opinions. Thanks

---

### Post by seachnasaigh on 2007-11-15
jmslouie:

What sort of hardware are you running? What you describe sound like driver issues to me, and installing the universe and metaverse packages in synaptic and getting the right drivers might just overcome them. However <caveat> in order to take a swing at the problem at all one would need to know your hardware setup </caveat>

ckr

---

### Post by Mevsthevoices on 2007-11-18
Feisty is better, lets you have control of more of your desktop. The drivers worked flawlessly, and it was less glitchy

---

### Post by eatberrys on 2007-11-18
I installed gutsy with out any problems ever thing works  so far. Gutsy finaly spports my wireless card with out me having to do stuf in termnial  just clicked enable driver and i was all good. Gutsy best reless yet ... 4 me any way.

---

### Post by Bob_Mendon on 2007-11-18
I got a kick out of reading some of these comments. Sure there might be some issues with "instability in compiz, bugy nvidia drivers" but when wasn't there in any build of Ubuntu? At least I can get reasonable desktop effects in Gutsy without a cocktail or witches brew of compiz-beryl and emerald that sometimes required days of tweaking to produce the desired effects. Then again, the tweaking is sometimes half the fun of Ubuntu. When you think about it MickeySoft doesn't let you tweak all that much and if you have to tweak it its broke! I enjoy the challenges of a new release and have fun putting the successive changes through their paces. 

As far as I am concerned, Ubuntu in any form is satisfying.

---

### Post by argosreality on 2007-11-18
I've used every release of Ubuntu since it came about and other than standard user issues (me not paying attention and clicking yes to the wrong question) the only issues that have come up with Gutsy is Miro not launching at all (stupid Java) and some initial difficulties installing DVD/mp3/DIVX,etc. support (why has it actually gotten more difficult? Or atleast seems to have)

The strange thing is I've pretty much always used hardware thats not truely "supported" but its worked well. Any issues I did have were pretty easy to track down and take care of (and I'm no hardcore kernel hacker). 

eugenio_vb: have you tried installing another distro with similar kernel/gnome revision to see if the issues come back?

---

### Post by ugm6hr on 2007-11-19
> **seachnasaigh said:**
> Having read through the thread a little more closely, I'd be really interested to see how many of the problems associated with Gutsy are fresh installs, and how many are upgrades. Over the years I've had mixed results upgrading Linux from one distro to another, even different versions within the same distro. Typically I do installs from scratch every time I upgrade, and have found this to be superior to following an upgrade path. Thoughts?

I've just installed Ubuntu7.10 fresh from LiveCD (previous Xubuntu7.04), and think it's great.

Everything just worked, except for the splash bootup screen - which needed a 10 second fix (as per another thread), which I'd already seen in this forum before installing - so took about 10 seconds to find it again when I found I had the problem too.

Other than that - on my Acer5051 laptop - wifi works 100% (without needing Wicd), Compiz is great (can't wait to show my OSX friends who looked down on my plain XFCE - and some of the functions are really useful, so stayed enabled after I got bored of wobbly windows), suspend works without a fix (haven't tried hibernate - I don't), and Gutsy tells me to install the correct media codecs / flash when necessary (a la Windows).  Feisty didn't manage any of these.  

So I would say 4:1 to Gutsy on my hardware.

Because of the hardware issues, I think it is important for people who are not au fait with Linux (i.e. me) just screen through the forum from the initial release to keep an eye out for known early bugs (like my splash issue), so that it's not frustrating when you encounter them.  Hence I waited almost a month before installing Gutsy.  And the install was dead easy.

Glad I did though :)

---

### Post by jryanitpro on 2008-01-01
I am shocked at all the "Gutsy is the best I'm not sure what you're talking about". I am also shocked that the powers that be are fairly silent on this dud also. I have worked through numerous Gutsy bugs only to get mixed results and to ultimately switch back to Feisty. I feel that giving Gutsy almost three months to work out the major kinks is more then fair.

The main issue I'm shocked about is the nonfree-flashplugin that still seems to be lingering. I'm positive that Ubuntu and Feisty had the flash issue flawlessly handled only to be broken in Gutsy, The threads for fixes sort of lead to fixes but as I said they were always with mixed results. The latest result I had was the plugin would finally install but didn't have any sound. Is it me or does going backwards seem to hinder Ubuntu's standing as a commercially viable choice. This bug seems to have been abandoned with a "maybe it will be better in the next release". I mean, get real!

The next bug for me was the frame buffer vga resolution which had several work arounds. But again, this was another non-issue until Gutsy for ma at least. So to dismiss everyone as "just the hardware" is wrong to say the least.

I have been running Ubuntu for a few years on and off and never had this level of unexpected functionality. I have install many releases of Ubuntu on three or four different laptops, four different fairly high end workstations with no problem.

I really until Gutsy believed that Ubuntu had really delivered on the promise of opensource but to me it makes no sense why things that seemed to be put to bed rear their ugly heads. We need to be getting better, more dependable not opening up more cans of worms that break already functioning components.

Before Ubuntu makes a serious run at the Enterprise desktop this can not be the case. Maybe it isn't ready as Mark Shuttleworth seemed to be sayong until Dell agreed to sell their boxes with Ubuntu pre-installed then suddenly the tune changed. I would have been more inclined to be a believer until "Gutsy" showed up.

Thanks

---

### Post by jordilin on 2008-01-01
> **rsambuca said:**
> I have been using Ubuntu since Dapper, and for me, without question the best release has been Gutsy.  I think it really is hardware dependent.

I complete second that. I could not install Feisty in my laptop, and now I have it with Gutsy. It is sth related to Hardware. Ubuntu used to have software with annoying bugs, but it gets better and better with time.

---

### Post by jryanitpro on 2008-01-01
> **jordilin said:**
> I complete second that. I could not install Feisty in my laptop, and now I have it with Gutsy. It is sth related to Hardware. Ubuntu used to have software with annoying bugs, but it gets better and better with time.

I appreciate the fact that you believe "it is the hardware". But if you listen many people are having issues with the same hardware that was running Feisty brilliantly. So much so that caused many people to believe that because evrything ran so well that Ubuntu (Linux) was reaching a very good place as far as reliability is concerned.

Let me ask you a question. If your hardware works now and did not work well with Feisty and now Gutsy breaks my hardware, should I be wrong about Gutsy's problems and you be right?

It still has to maintain functionality! Not break things that were already working superbly! And I'm not talking about maintaining compatibility with ancient hardware. My laptop is less then a year old and my desktop is newer then that. Not to mention many of the issues have nothing to do with hardware. (ie browser plugins) 

It seems to me that features and updates were added and not made to be compatible before the bits were released. Maybe it was the GNOME upgrade or something else major but please don't act as if anyone having these issues need to look to someone else because nothing was overlooked in the software and operating system.

Just a bit frustrating, sorry!

---

### Post by rsambuca on 2008-01-01
Just to set the record straight, Flash did work perfectly when Gutsy was released.  It is only after Adobe changed their version that things have went a bit haywire.  Hardly the Ubuntu developers' fault on trying to keep working with proprietary plugin changes.

Your VGA issues I haven't looked into, but my Gutsy installation has been much better than Feisty as well.

---

### Post by linuxer101 on 2008-01-02
i agree with the topic creator. if you guys claim its his hardware limitations. thats a shame because gutsy should be everything feisty is and better. not be less compatible with his hardware limitations. if feisty supported his hardware fine i dont see why gutsy cant. in point i agree with the TC. this shouldnt be a problem at all. hardware compatibility and testing methods need to be improved. quality control needs to be improved.

---

### Post by ginbuntu on 2008-01-02
I also have a nvidia card here. But everything works perfect out of the box. Only had to install the restricted driver for my gfx card after installation.

---

### Post by snakeeyes on 2008-01-02
There r ways u can improve Fiesty even if u continue wanting to use it. Install the latest version of OpenOffice. Your multimedia applications r fine, firefox must be up to date as well. You can even install the latest version of firefox which is in Beta if u want. Instead of Gaim, if u want Pidgin, just download the latest source code and install that. Compiz Fusion can be installed on Fiesty as well. 

An easier way other then compiling from source is that u can add a Gutsy repository to get the latest version of a specific program and then remove that repository after installing that program. The latest Nvidia drivers can also be installed in Fiesty if u use Envy.

You can even install the Gutsy kernel or Hardy kernel in Fiesty to improve hardware support so if ur suspend to ram or disk didn't work in Fiesty then it will work using the Gutsy or Hardy kernel. I don't have any problems with Gutsy, but its kernel was unstable for me so I upgraded to Hardy's development kernel which works great except Virtualbox doesn't have any modules for the latest kernel yet, this problem will be solved shortly.

The thing is that in Linux u can modify anything u like. You can have Fiesty's stability and be using Gutsy's or Hardy's kernel for better hardware support at the same time.

If anyone needs help on upgrading their kernel then ask me. There r threads around in the forums to help u do this.

---

### Post by LukeCarrier on 2008-01-02
In my opinion, Gutsy is far superior to Feisty. Sure, it isn't perfect, but what OS is? The desktop effects and graphics drivers are easier to configure, and it runs great on 64-bit, providing outstanding compatibility with 32-bit applications. Overall, Gutsy is great.

There are a few points I've made that would make the system better, and some I haven't. A few ways the OS could be improved would be:
> add a media centre
> update some of the pre-installed games to some more...complex ones
> remove the 3 menus in the top panel and replace them with a complete menu, a bit like Mandriva

I like gutsy, the system works out of the box and has massively improved networking. Two of the computers in my house run the OS, both had to use NDIS wrapper with the Windows drivers because Ubuntu just didn't have any drivers for them. When I finally decided to upgrade to 7.10, they both worked out the box. The networking utility is much easier to use.

---

### Post by Maupertus on 2008-01-02
(text removed by poster)

---

### Post by Em-Buntu on 2008-01-02
I agree with the thread's initiator. Feisty is much faster and more stable then Gutsy.
I run a very standard PC comprised of consistent hardware.

I've also installed Feisty and Gutsy on 10s of computers consisting of various low, med, and high end motherboards. Feisty has run better all-around on them all relative to Gutsy.

I've upgraded from Feisty, which ran like a top on my machine out-of-the box, to Gutsy which runs slower and has far more ISSUES then Feisty, primarily in the areas you've documented.

I agree, the main issues seem to center around Compiz, IP6, and DNS.

Internet browsing definitely runs much slower in Gutsy, and this has nothing to do with preferences or hardware as some mistakenly suggest.

Hopefully, Hoary won't come out of the box with such deminished performance, and we'll see a vast improvement in Compiz development.

---

### Post by jordilin on 2008-01-02
> **jryanitpro said:**
> I appreciate the fact that you believe "it is the hardware". But if you listen many people are having issues with the same hardware that was running Feisty brilliantly. So much so that caused many people to believe that because evrything ran so well that Ubuntu (Linux) was reaching a very good place as far as reliability is concerned.

Let me ask you a question. If your hardware works now and did not work well with Feisty and now Gutsy breaks my hardware, should I be wrong about Gutsy's problems and you be right?

It still has to maintain functionality! Not break things that were already working superbly! And I'm not talking about maintaining compatibility with ancient hardware. My laptop is less then a year old and my desktop is newer then that. Not to mention many of the issues have nothing to do with hardware. (ie browser plugins) 

It seems to me that features and updates were added and not made to be compatible before the bits were released. Maybe it was the GNOME upgrade or something else major but please don't act as if anyone having these issues need to look to someone else because nothing was overlooked in the software and operating system.

Just a bit frustrating, sorry!
Ubuntu is free and opensource, so you have to abide by these rules. Linux has always been this way. I remember those days that you had to configure manually nearly everything. This is what makes Linux different and that's why we have this awesome community. If you have some hardware that does not work, learn and try to work around the problem by asking google or asking here or post a bug in Ubuntu. 
As for Software bugs like browser plugins, I doubt if Ubuntu has sth to do with this.

---

### Post by jryanitpro on 2008-01-02
> **jordilin said:**
> Ubuntu is free and opensource, so you have to abide by these rules. Linux has always been this way. I remember those days that you had to configure manually nearly everything. This is what makes Linux different and that's why we have this awesome community. If you have some hardware that does not work, learn and try to work around the problem by asking google or asking here or post a bug in Ubuntu. 
As for Software bugs like browser plugins, I doubt if Ubuntu has sth to do with this.

Just an FYI if the flash issue wasn't an ubuntu bug we would know by now. The issue you are referring to about the version number isn't  the only bug.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/151849](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/151849)

Sometimes it seems no one actually reads posts before commenting. I know what Linux is about and the rules are not as you state.

Tell all the new PC purchasers and the Enterprise companies business Ubuntu is hoping for, "that they should Google and deal with it." (I paraphrased your answer)

It is all good I'm not losing any sleep I just thought that it was a good time to speak up since it seems many seem afraid of not towing the line.

---

### Post by High_Yield on 2008-01-02
I applaud what the initial poster said - bugs are bugs and should be stated - state away my friend.

Seems that MrVertigo has used "Feisty Fawn", "Gutsy Gibbon", and "Arrogant AHole" by saying this:
"enjoy your choice my friend, its a freedom only enjoyed when you contemplate not haviong it".  That followed up by some snippity quote from Linus - nice.

The initial poster is simply trying to improve things by being honest and not a "blind fan".  No reason to turn it into some kind of "morality" issue.  Go have a whisky and get a life - talk with other humans directly - you may like it.

BTW - I have had problems w/ gutsy, some hardware and some software, but I will still use it going forwards over Vista.

- B

---

### Post by Michl on 2008-01-29
> **reset3x said:**
> Re-burn. Check CD for errors. re-install...

YOu're shooting from the hip.

---

### Post by james_xxx on 2008-01-31
I guess for my 2 cents worth, I must also say that I believe Feisty to have been much, much better than Gutsy. 

The issues I have had have been mostly hardware related. My laptop has a Ralink wireless card, which worked perfectly in Feisty, but almost not at all in Gutsy. Why did the Gutsy devs go with the new beta rt25xx driver, instead of the older, more stable driver? Maybe there is a good reason, but come on... why use a driver that does not work? I finally had to compile the older driver myself. Though it still does not work perfectly, it is good enough.

Why do external USB drives no longer mount automatically in Kubuntu Gutsy? I have tried fiddling with settings, but have not yet been able to rectify this.

A friend was over a few weeks ago, and had an external hard drive that would not mount on my Kubuntu Gutsy laptop, or my Kubuntu Gutsy desktop... but mounted with ease on my Fedora 8 desktop. 

I have an Olympus C-5500 camera. It worked fine in Feisty, does not work at all in Gutsy, but works great in Fedora 8.

Maybe I should have changed distros (on my laptop, at least).

One question I have, is that when a new version of *ubuntu comes out, and for some reason some hardware does not work correctly (rt25xx, for example), why can't there be an upgrade to fix this? Why must one wait for the next version to be released? :confused:

One would think that major issues with hardware compatibility would somehow be fixed several weeks after a new stable release. Maybe I just don't understand.

---

### Post by tiredoldman on 2008-01-31
I have many versions of Ubuntu running on my 12 different rigs.
From 6.04 to 7.10. I do not like 7.10. Too many things have to be "Fixed", internet connections,printers,vid drivers,just too much hassle.
What has worked on all the others mostly,has failed on 7.10 completely. I do have 2 6320's that do run 7.10,but,can only use them for F@H. they don't play well with any other functions.
I have the following types of rigs:
2.. Q6600
3..E6320
1..E6300
5..3800+ duos
1..pent. duo 340
I just use what works for them each, thats why I went to Ubuntu rather than stay with Windows. And the cost.
All of these are on the same network and used mostly for F@H,But, also used to expose friends and family to the world of Ubuntu.
It has resulted in 9 people switching over to Unbuntu on their rigs !
9 out of 15,,not too shabby ! 
Have a great day.

---

### Post by Jay Jay on 2008-02-04
Amazing how many people on here assume that just because Gutsy works well for them, anybody else who has problems must be doing something wrong.

I upgraded from Kubuntu Feisty to Xubuntu Gutsy and encountered endless woes: at first there was no sound and every so often I would have to unmute the audio from Terminal to restore it. The instability was a nightmare - In the space of 24 hours my laptop froze up about 30 times, usually in the midst of some important work - I spent more time booting, powering down and rebooting than using the OS. If I didn't have other gear to fall back on I would've been sunk. All manner of random glitches would occur: at least once I had to wait 10 mins for a program to open. Firefox crashed regularly, the solution was to use Swiftweasel instead. Icons would not stay in the top panel and one day the Applications panel just vanished, for good!

Last week I conceded defeat and "downgraded" to Xubuntu Feisty, a whole different story in terms of performance and stability. 7.04 is far from perfect and I can see where advances and improvements have been made in Gutsy over the predecessor but (for me) the problems outweigh the benefits of 7.10 at the moment.

---

### Post by Ripfox on 2008-03-31
After extensive testing, I must agree with the OP. Gutsy has just plain been a letdown over here. But, ah well thats the way it goes, Hardy looks and feels very,very good.

---

