---
title: "A proposal relatded to the recent XServer break."
date: 2006-08-22
forum: Desktop Environments
---

### Post by moonlite on 2006-08-22
I think adding some extra QA by adding some new (non default) repositories might be a good idea. 
These repos would get updated with fixes a few days in advance and then the main repos would get updated with those fixes automatically a few days later, except any broken fixes would be fixed before that.

EDIT: i didn't suffer from the X problems my self and understand that these things can happen, but i belive steps should be taken to minimize the risk of this happening again.

---

### Post by cstudent on 2006-08-22
I don't see how having another repo would avoid the problem. Who are you expecting to use this repo? A select group of testers? If you publicized the repo, then everyone would just add it to their sources list so they could get the updates faster.

The xserver problem is being a bit blown out of proportion. It's not pleasant, but it's been easily and quickly fixed. Not that big of a deal.

---

### Post by aysiu on 2006-08-22
> **cstudent said:**
> 
The xserver problem is being a bit blown out of proportion. It's not pleasant, but it's been easily and quickly fixed. Not that big of a deal. I disagree. It's not a big deal to people who hang out on the forums and know the fix for it, but if you're just merrily using your Ubuntu box and X breaks... it really hurts productivity a lot. I think it's a great idea to have a live CD or know how to do things from the command-line, but those things shouldn't be necessary.

---

### Post by cstudent on 2006-08-22
The fix was as simple as knowing to either roll back to the previous version of xserver or downloading the updated fixed version via command line and installing. What kills productivity is a lack of knowledge on what to do, not the fact that the buggy version broke X. 

This is sort of like someone turned the lights off and everyone started gasping for air in a panic.

---

### Post by Metacarpal on 2006-08-22
> **cstudent said:**
> The fix was as simple as knowing to either roll back to the previous version of xserver or downloading the updated fixed version via command line and installing. What kills productivity is a lack of knowledge on what to do, not the fact that the buggy version broke X. 

This is sort of like someone turned the lights off and everyone started gasping for air in a panic.

While you're right that knowing how to roll back to a previous version of xserver would fix the problem, I have to disagree with your point of view.

First, not everyone would know when the updated version with the fix was available.  What are people supposed to do, sit around and try to upgrade every ten minutes?  Sounds like a fun way to spend one's day.

Second, sure, knowing how to roll back to a previous xserver version sounds great, but I've been using Linux for two years and Ubuntu for three months, and I wouldn't have the first foggy clue how to do that unless I could get online and search for the solution.  But if the only computer I have access to is my Ubuntu box, and that's b0rked, finding the solution isn't going to be that easy.

aysiu's right - people shouldn't have to have their LiveCD right on hand for every update in case X breaks.  Especially not people whose computers don't have enough RAM to load the LiveCD.

I think Moonlight has a good idea.  A testing repo for a day or two, then to the main repos - at least for system-critical components like xserver.  Anyone who's willing to risk breakage can use those repos for updates.  Odds are, anyone that eager to get new packages knows how to roll back anyway.  And the general public gets the updates a couple of days later, none the wiser and all the less likely to scream in frustration at their b0rked Ubuntu installation.

---

### Post by aysiu on 2006-08-22
If people needed the light in order to not step on sharp spikes sticking out of the floor, then they would probably be in a panic.

Yes, this is not a life-and-death situation, but people are right to panic, especially if they use Ubuntu to get work done.

You say it's "a lack of knowledge on what to do." Well, I hate to say it, but very few people here would know what to do. I certainly wouldn't have (I don't know how to downgrade a package). Just how much knowledge should one acquire to simply use Ubuntu and apply updates?

---

### Post by randell6564 on 2006-08-22
> **cstudent said:**
> I don't see how having another repo would avoid the problem. Who are you expecting to use this repo? A select group of testers? If you publicized the repo, then everyone would just add it to their sources list so they could get the updates faster.

The xserver problem is being a bit blown out of proportion. It's not pleasant, but it's been easily and quickly fixed. Not that big of a deal.

It's been fixed?  So it's now version 10.4 correct?

---

### Post by mega on 2006-08-22
> **cstudent said:**
> 
The xserver problem is being a bit blown out of proportion. It's not pleasant, but it's been easily and quickly fixed. Not that big of a deal.

it was a HUGE deal, HUGE HUGE HUGE, all the people I have got to switch to ubuntu have absolutly no idea what "apt-get" is

all they know is they got an icon that said "updates are avalible"


thank god they dont click update very often, nobody called me, so I dont think any of them did an update yesterday


breaking X may not be a big deal to you, but it is the biggest possible breakage that can happen to a non computer litterate user, to them the computer was flat out broken and nothing tells them how to fix it, they get an ugly X error and dumped to a command prompt with no clue what to do

---

### Post by randell6564 on 2006-08-22
> **aysiu said:**
> If people needed the light in order to not step on sharp spikes sticking out of the floor, then they would probably be in a panic.

Yes, this is not a life-and-death situation, but people are right to panic, especially if they use Ubuntu to get work done.

You say it's "a lack of knowledge on what to do." Well, I hate to say it, but very few people here would know what to do. I certainly wouldn't have (I don't know how to downgrade a package). Just how much knowledge should one acquire to simply use Ubuntu and apply updates?

I completely agree!  If someone had only one PC without the vast knowledge that cstudent seems to have, they would be screwed!

---

### Post by aysiu on 2006-08-22
Does *cstudent* stand for *computer science student*? A lot of Ubuntu users do not have the kind of background you have. Even some of us who are comfortable with the command-line do not know how to downgrade a package without doing some internet research.

---

### Post by cstudent on 2006-08-22
Alright, fine, whatever, I give up. 

I don't have a vast knowledge of Ubuntu or Linux. I'm still learning too.

I believe that how much knowledge you should have is whatever it takes.

My point was, the fix was simple, not a major hack. It could have been worse.

---

### Post by aysiu on 2006-08-22
> **cstudent said:**
> 
My point was, the fix was simple, not a major hack. It could have been worse. Yes, it could have been a lot worse. That I'll agree with you on. But a fix is simple only if you know it.

---

### Post by mega on 2006-08-22
only thing that could be worse is a broken kernel

---

### Post by caserio on 2006-08-22
Hi, 

How about fixing **apt-listbugs** ? 

[https://launchpad.net/distros/ubuntu/+source/apt-listbugs/+bug/42673](https://launchpad.net/distros/ubuntu/+source/apt-listbugs/+bug/42673)
[http://jameswestby.net/weblog/debian/00-apt-listbugs-rc-buggy.html](http://jameswestby.net/weblog/debian/00-apt-listbugs-rc-buggy.html)

*Edit*

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/020199.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/020199.html)

All right, nobody cares. So this package is useless and should be removed from the repos.

---

### Post by theak on 2006-08-22
It was problems of this nature that persuaded me to switch from another distro to Ubuntu, I hope this can of issue can be prevented in the future.

---

### Post by Metacarpal on 2006-08-22
What does everyone think of Moonlight's proposal - a sort of testing pre-release of critical updates that those with the know-how could test before they're released on the main update repos?

Are there people interested in doing the update testing?  Is this something that should be suggested to the devs?

---

### Post by aysiu on 2006-08-22
I think it's up to the developers to do more testing before releasing an update like this on the general public.

---

### Post by PathSpace on 2006-08-22
It sounds to me like how Debian sets up their repositories; stable, testing, and unstable.  I don't think it's a particularly bad idea to keep the "stable" repositories actually stable...

---

### Post by erikpiper on 2006-08-22
Wouldn't a better idea be to have an "enterprise" repo- EXACTLY the same as the normal repos- but 2 days behind or so, and if something like this would happen, they wouldn't be updated until it was solved?

---

### Post by xtknight on 2006-08-22
It was a pretty big deal.  Even if I did know how to downgrade a package, how would I know what previous version I had?  And the xorg-xserver-core package...had it not been tested even once before release (it seems like it should have before even being compiled into Release mode)?  It seems to be breaking every single person's system, so it's not like just somebody with Xgl or something like that.  It's every system...!

Thankfully it was taken care of quick enough as to not lose too many.  At this point I think the package should just at least be tested twice on all possible xorg drivers.  It looks like it had not been tested even once.  That's what completely startles me.  :confused:

If
a) the developers tested the package before releasing it; and
b) packages on every repository in the world could be pulled and updated in seconds

Then I think that will drastically reduce the chances of this happening again.

Edit: well it looks like the 10.3 update was fine for some people, so maybe it had been tested.  Do we have any more details on what exactly it broke and why so many machines are breaking?

---

### Post by Smarter on 2006-08-22
xtknight: The package was working with Intel graphic cards, maybe the uploader use an Intel card?

---

### Post by statue on 2006-08-22
I think it is certainly a good idea to have some type of test rep though I wouldn't want it to be an excuse for the packages to not first be tested by the actual developers. This recent mistake was extremely easy to prevent and for someone like myself with minmal knowledge of linux, rather time consuming to rectify.

---

### Post by shat on 2006-08-22
Another view,

When I woke up this morning I clicked the shiny orange button and installed the update, and didn't actually restart my laptop for a few more hours.  When I did, and the xserver puked, I didn't remember the update or anything.  I tried to troubleshoot the error message outside of the ubuntuforums for at least 20-30 mins before I came here.  

Even if a new linux user knows exactly what messed up their system, they can at least troubleshoot with that information.  The problem is much harder to solve when this sort of thing happens to somebody and breaks them out to command line with no warning, and relatively little clue to what did it (remembering that you upgraded xorg helps :cool: )

Anyway, I do see this as a "Big Deal".  Maybe ubuntu needs to decide for itself, is it another [linux-user's] [power user's] [computer geek's] OS, or is it safe for a "normal" computer user?  If the latter is the case, some clarity may be gained by adding another repository for the normal users, to shield them from these sort of problems.  The "power users" will still use the more quickly updated repos, but then again, they are more likely able to troubleshoot and fix these types of things.

I think ubuntu is trying be as "normal user" oriented as possible, much more so than the other distro's, so these sort of failures should not happen.

My 2c:-\"

---

### Post by carontis on 2006-08-22
For what I know about updating (not in Linux) the better way is to have a pc with the entire system on it. The system must reside on the pc from the 1st day and every update must be applied before to it and only after will be possbile give it to the users. But in this case we have to ways: 1 for Intel (and sub-cpu) and the 2nd for AMD (and sub or up cpu). So in this case programmers should have 2 pc both installed with Ubuntu, but devided in 2 parts: 1 for Intel and the other for AMD. By the time they will install an update, they will see if it works or not.
To me happened the same as to other users (or many of them). I use a cpu AMD 1700+ and after seen that the upgrade was expecially for Intel, I installed it 'cause I have seen usually many updates follow the kernel. Bad for me, 'cause in the morning I had that bad surprise: after booted, it freezed and the only thing I was able to use was the terminal. Only after, I found on the forum the link to _restore_ the situation. In effect I think it culd be possible (as already told) to bypass these bad bugs, having a "restore point" as it is for windows, so in this way you can boot your system and tell it to go back to the last good boot. Thsi was what we talked about this morning (here was morning) on the forum.
Someone who can approuve it? Let know. I think it could be the best way to skip many other things. If you see the update fails or is corrupted, well you can come back to last good configuration restoring it simply with a click (or almost).

---

### Post by asplode on 2006-08-22
I mostly agree with the lead poster.

Debian does something very similar to this, and Ubuntu is a debian based linux distro.

Sid for bleeding edge updates, and Sarge for more reliable, thoroughly tested updates.  Yes, its true these are two different distros, but we must make absolutely sure that an update does not a) make people lose faith in their distro, and in linux itself, b) cause data loss, or c) hose their installation.

I know in larger organizations the updates are rolled out by the IT admin, who would mostly likely have noticed it on his machine first, and then not even been able to roll it out to his company.

But a couple of hours of being locked out of their desktop is all someone needs to panic, cry, and hole themselves back in the uncomfortable blanket of windows.  People are fickle.

---

### Post by ahaslam on 2006-08-22
Hi,

I think that a test rep would be a great idea. I also think that more time should be devoted to testing updates, they are meant to fix bugs not bork your system. 

This is the third problem that I've encountered with so called updates in as many months. Though this was the first time that I had to load up SLAX.

If Ubuntu wants to appear as a stable OS something needs to be done. What would a complete noob have done - reinstall?

Tony.

---

### Post by carontis on 2006-08-22
Well, asplode, I don't think it's a good idea to show that Linux world has some difficulties. I think that all we can do is make grow up this world in a better way (I mean for Open Source) and helping others to grow up, will it make surely better. About what you say *But a couple of hours of being locked out of their desktop is all someone needs to panic, cry, and hole themselves back in the uncomfortable blanket of windows. People are fickle* I think we all should try to understand that the distro comes FREE and it is possible it contains some errors, also for exactly what you told. So, try to understand why many were worried about the crash. The way about the admin who is the only can upload updates, for me is the first, is the better way 'cause it means someone tried it before giving it... same or almost same of what I told before.

---

### Post by moonlite on 2006-08-22
I'm not suggesting two different ubuntu-versions (there are already edgy eft for those living on the edge). What i'm suggesting is that updates tested by the ubuntu developers gets another round of testing for a day or two by the enthusiasts that wants to do so. 

To whoever said that "everyone will just turn that repo on anywat and it will be of no use": this isn't gentoo, slackware or arch (etc), ubuntus targeted audience isn't the computer geeks that know how to change and add extra repos, but for the normal computer user that just want a stable desktop for their daily work. And besides, i think that there are a lot of computer geeks out there that prefer a slightly more stable desktop instead of getting the fixes 2-3 days before.
Personally i wouldn't use my proposed testing repo (i would reap the rewards of the rest of the peoples testing instead), and i'm quite sure Joe User wouldn't either, but i'm guessing a whole lot of people on these forums would.

---

### Post by wagerrard on 2006-08-22
Perhaps the updater might be made clever enough to automatically rollback to the previous deb when the update doesn't work. In this case, it would have needed to retain control after the reboot, check for a failed X launch, and then run a script to do the rollback.

Never depend on your customers to be clever enough to fix your mistakes.

---

### Post by Scythe!? on 2006-08-22
I have this problem atm, how do I downgrade XServer back or what command do i use to upgrade to the fixed update?

---

### Post by randell6564 on 2006-08-22
It would be nice to hear from those responsible for this mishap.

Maybe an apologie or an explanation?  Although, they did provide the fix pretty quick.  But it's a little disconcerting that no one on the developer side of things has posted any thing regarding the booboo!

---

### Post by cstudent on 2006-08-22
> **Scythe!? said:**
> I have this problem atm, how do I downgrade XServer back or what command do i use to upgrade to the fixed update?

This thread can help you:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by bluenova on 2006-08-22
I just posted about this on another post, and now found that someone else has had the same thought. I think the idea of a Pre-release repository is a great idea! Those of us that know how to fix our system when it breaks can use the pre-release repository(s) and report any issues found, where as for the normal desktop user would be using the normal repositories without having to run into these issues, but just getting the updates a day later. There must be 1000's of people sitting at a command prompt today no knowing what to do about it.

Perhaps someone with the right contacts could make the suggestion?

---

### Post by randell6564 on 2006-08-22
> **Scythe!? said:**
> I have this problem atm, how do I downgrade XServer back or what command do i use to upgrade to the fixed update?

I'm not a pro, but this is what you would type at the console.

Sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10.4

Then do a sudo shutdown -r now

This will install the fix

Good luck!

---

### Post by Scythe!? on 2006-08-22
> **randell6564 said:**
> I'm not a pro, but this is what you would type at the console.

Sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10.4

Then do a sudo shutdown -r now

This will install the fix

Good luck!

Thanks but I managed to fix it. i typed
```
sudo apt-get update
```
then 
```
sudo apt-get install xserver-xorg-core
```
It detected it needed upgrading and sorted it for me :)

---

### Post by zitch on 2006-08-22
I did find this in the community help section:  [https://help.ubuntu.com/community/Debmirror?highlight=%28mirror%29](https://help.ubuntu.com/community/Debmirror?highlight=%28mirror%29)

Maybe someone would want to experiment with creating a "stable mirror"?  :D

I do like the idea of a "testing" mirror so some of the public can spot issues in the repositories before it's released to the general public in 24 or so hours, but who's willing to front the costs and time to do this? 

Anyways, I will be implementing this mirror for the intranet at work.  This way, I can have my laptop be the "test" system, while the ubuntu servers I'm running will have a "tested" repository for safety and download speed reasons.

---

### Post by Ramaddan on 2006-08-22
Hi,

Two ideas to keep in mind to better development:

1- The idea of a rollback scripts, when problems are detected,
which is similar to the previous good configuration like windows idea.
(previously posted by other members of the forum)

2- How about as Ubuntu connects to the internet at kernel level,
it receives a signal from the repository of a bad package
that the maintainer marked as broken, and so it removes that package,
and installs a previous package either from archive or redownloads
a prior version, or downloads corrected package if available?

This is just an extension of the previous idea.

NOTE: This is in addition to a testing and stable repo idea.

---

### Post by Metacarpal on 2006-08-23
> **Ramaddan said:**
> Hi,

Two ideas to keep in mind to better development:

1- The idea of a rollback scripts, when problems are detected,
which is similar to the previous good configuration like windows idea.
(previously posted by other members of the forum)

That sounds interesting.  Perhaps it could be made a part of Recovery mode?  That way it wouldn't have to load during (and slow down) every single boot.

> 2- How about as Ubuntu connects to the internet at kernel level,
it receives a signal from the repository of a bad package
that the maintainer marked as broken, and so it removes that package,
and installs a previous package either from archive or redownloads
a prior version, or downloads corrected package if available?

Well, for that to work, they'd have to get wireless working on a kernel level. :roll:  Plus, if it did an update scan (it would have to access the repos to check for broken packages) on every boot, that would slow things down, too.

How about integrating this check into the rollback script?  If X fails to load, there is a prompt to enter recovery mode.  Then a system integrity check can be run (optional, so you can still get in and do things manually if you prefer), which would check the repos for known-b0rked packages and either (a)update to a new package if a fix has been released, or (b)rollback to a previous version.  A message lets the user know what change has been made and why, then prompts to reboot.

---

### Post by asplode on 2006-08-23
> **carontis said:**
> Well, asplode, I don't think it's a good idea to show that Linux world has some difficulties. I think that all we can do is make grow up this world in a better way (I mean for Open Source) and helping others to grow up, will it make surely better. About what you say *But a couple of hours of being locked out of their desktop is all someone needs to panic, cry, and hole themselves back in the uncomfortable blanket of windows. People are fickle* I think we all should try to understand that the distro comes FREE and it is possible it contains some errors, also for exactly what you told. So, try to understand why many were worried about the crash. The way about the admin who is the only can upload updates, for me is the first, is the better way 'cause it means someone tried it before giving it... same or almost same of what I told before.

First of all, the "ask for a refund" line gets old after a while.  Yes, this distro is free.  No, its not free to develop and maintain it.  And I am not demanding anything of anyone.

Secondly, I dont think a software package exists that is 'completely error free'.  I am comfortable with that.

Thirdly, I am not speaking for myself when I say people are fickle.  If you disbelieve my statement, just take a look around in the forums at the panic this update caused.  Tell me that nobody lost any faith in their distro, that nobody became a little scared over it, and that nobody would consider going back to windows or hesitating even for a moment in switching to Ubuntu.

---

### Post by ahaslam on 2006-08-23
> **Metacarpal said:**
> That sounds interesting.  Perhaps it could be made a part of Recovery mode?  That way it wouldn't have to load during (and slow down) every single boot.
Sounds good to me. Surely it wouldn't take too much to implement?

Tony.

---

### Post by raffytaffy on 2006-08-23
from now on ill hold off on critical updates for a day or two..and see how the community reacts to them.

---

### Post by BungaMan on 2006-08-23
I agree on a few of the proposals here

- something like "sudo apt-get rollback 1" where 1 stands for how many upgrades you want to roll back.
- test repositories.  plain and simple.  add 2 weeks/a month (where's the rush) difference in releasing from test to 'production'.  Have a forum where people can report problems when using the test repositories.

These are 2 simple developments making Ubuntu a lot more stable saving all the inexperienced computer users from problems.  The regular forum will contain less postings like X broke after update Y.

---

### Post by FuriousLettuce on 2006-08-23
This update fiasco is a bigger deal than some of the more Ubuntu-savvy users would like to admit. Ubuntu's tagline is 'Linux for human beings' - the implication is that it ought to be easier for normal people to use, and they should be able to use it without an initimate knowledge of the OS. Granted, rolling back the update didn't require a great deal of knowledge of the OS, but surely it ought to be useable by people who just want to use their computers, without having to worry about how they work?

For a lot of people, this will have destroyed their faith in Ubuntu / Linux - an 'unusable' computer is something that many people will be scared of - especially if they use their computers for work / office use. 

I think the idea of a 'rollback script' to right any wrongs made by a recent update makes great sense. Each update to log what changes it had made, and where the backups were kept, so rolling back would simply be a case of choosing the update you thought broke your computer and clicking 'Fix'.

---

### Post by dumbo on 2006-08-23
The easiest solution would surely be to add an option (default 'yes') 'wait 24 hours after package availability before updating with non-security packages'? (along with a silly warning... e.g. "please do not change this setting unless you understand what this means")

For people who don't know how to fix things like this, they will either never discover the flag, or if they do discover it - hopefully leave it alone.

For 'early adopters', or people supporting others they can set it to 'yes'.

---

### Post by BungaMan on 2006-08-23
One small problem is that when X breaks, where will you 'click' on fix?

The login prompt could contain a little trouble shooting guide like "log in with your user name and password", "if your system failed to start, type at the prompt sudo apt-get rollback".  It is very likely that when some one logs on with the command line prompt that they are in trouble and could use some guidance.

---

### Post by FuriousLettuce on 2006-08-23
OK, maybe not click on 'Fix'. Perhaps, if it's an X problem, X could set a flag when it dies that triggers a script automatically on login? Something like 'We have detected a problem with an update or recent configuration change, press 1) to rollback or 2) to edit the file yourself'? Then the script could have a GUI if it was a package other than X that broke?

---

### Post by christian.convey on 2006-08-23
Does anyone notice that we're starting to advocate a release system like Debian's, albeit with perhaps a compressed timeframe?

This new "testing" repository is like Debian's "testing" repository.  And the main Dapper repositories would be treated like Debian's "stable" repository.  And that makes Edgy be equivalent to Debian's "unstable" repository.


I've heard that all new Linux users try various distros, and end up settling on Debian.  It never occurred to me that all new Linux distros try their own release policy, and then end up settling on Debian's policy ;)

---

### Post by Lunar_Lamp on 2006-08-23
I think that until we know precisely what went wrong it's a little premature to be suggesting changes to avoid it in the future.  We know that the end result was fairly significant, but we don't know how the sitution arose.  For all we know a developer may have accidently uploaded a patch to the main update server rather than their own private testing server (possible but probably not true) - this kind of human error would be hard to avoid with most methods suggested.  The vast majority of updates that have been sent out do not have such catastropic effects (this is the first I am aware of), so perhaps we should give the dev team a chance to explain what happened, and if any measures are being implemented to avoid a recurrence before we get embroiled in a debate about how they could stop it from occuring again.

Having said this, a rollback system would be a very worth addition to Ubuntu.  Not just for when updates go wrong, but I'm always messing around with settings and the safety-net of a roll-back option would be comforting.

---

### Post by christian.convey on 2006-08-23
I'm not recommending a particular way forward.  I was just pointing out that the way-forward recommendations made by other people are sounding a lot like the Debian process.

---

### Post by lazerradial2003 on 2006-08-23
Slighty offtopic but several people have mentioned that for many ubuntu users, it would have been a huge deal because unless they use the forum regularly, they may well not think to look here. 

I think it would be worth considering some sort of integration of the ubuntuforums website and the OS itself, since arguabley one of the big advantages of Ubuntu is that it has such a thriving community here and pretty much any problem posted, will, if worded correctly get a reply solving it within a few hours if not a few minutes. Nothing obtrusive obviously but something to make people aware of just how big this community is (not like some computer forums where u post a message and wait a week for a reply written entirely in hex...)

---

### Post by lazerradial2003 on 2006-08-23
Slighty offtopic but several people have mentioned that for many ubuntu users, it would have been a huge deal because unless they use the forum regularly, they may well not think to look here. 

I think it would be worth considering some sort of integration of the ubuntuforums website and the OS itself, since arguabley one of the big advantages of Ubuntu is that it has such a thriving community here and pretty much any problem posted, will, if worded correctly get a reply solving it within a few hours if not a few minutes. Nothing obtrusive obviously but something to make people aware of just how big this community is (not like some computer forums where u post a message and wait a week for a reply written entirely in hex...)

---

### Post by mister_p_1998 on 2006-08-23
> **cstudent said:**
> The fix was as simple as knowing to either roll back to the previous version of xserver or downloading the updated fixed version via command line and installing. What kills productivity is a lack of knowledge on what to do, not the fact that the buggy version broke X. 

This is sort of like someone turned the lights off and everyone started gasping for air in a panic.

Ive worked in IT for 12 years, dabbled in Linux for around six, and used Dapper for 5 months, I didnt know how to roll back...
it might be very useful if Apt-Get had a "uninstall last update" option, Comments guys?
Steve

---

### Post by peabody on 2006-08-23
I'm not saying I'm against this, but I was under the assumption that THIS WAS ALREADY THE WAY THINGS WERE.  Dapper is a "stable" release.  Updates to it should already be going through some kind of testing, perhaps similar to what people have been proposing, internally at Canonical with the Ubuntu devs.  The fact that this is apparently not the case, is highly disconcerting.

---

### Post by bluenova on 2006-08-23
> **christian.convey said:**
> I'm not recommending a particular way forward.  I was just pointing out that the way-forward recommendations made by other people are sounding a lot like the Debian process.
Not really. I was thinking that the normal reps would get the update just a day later giving it to the pre-release repo first. So the scale is not quite the same.

---

### Post by bluenova on 2006-08-23
> **peabody said:**
> I'm not saying I'm against this, but I was under the assumption that THIS WAS ALREADY THE WAY THINGS WERE.  Dapper is a "stable" release.  Updates to it should already be going through some kind of testing, perhaps similar to what people have been proposing, internally at Canonical with the Ubuntu devs.  The fact that this is apparently not the case, is highly disconcerting.
I think that is the case, but it would be a very small number of people compared to having a pre-release repo which would mean there would be many more types of hardware and software configurations testing the new update.

---

### Post by christian.convey on 2006-08-23
Agreed.  I didn't fully quote it, but my original posting included, "albeit with perhaps a compressed timeframe"

---

### Post by randell6564 on 2006-08-23
> **mister_p_1998 said:**
> Ive worked in IT for 12 years, dabbled in Linux for around six, and used Dapper for 5 months, I didnt know how to roll back...
it might be very useful if Apt-Get had a "uninstall last update" option, Comments guys?
Steve

That is EXACTLY what I was thinking!  Something that makes it easy to just uninstall what was installed (including all the dep's and stuff that came with it!)

---

### Post by Chemroydal Tissue on 2006-08-23
> **mister_p_1998 said:**
> Ive worked in IT for 12 years, dabbled in Linux for around six, and used Dapper for 5 months, I didnt know how to roll back...
it might be very useful if Apt-Get had a "uninstall last update" option, Comments guys?
Steve

By the gods yes! Something like:

```
sudo apt-get rollback *<app>*
```

perhaps?

---

### Post by bluenova on 2006-08-24
Reading the dev mailing list it seems that some of the things suggested in this thread already exist but they were not used. The pre-release repo already exists its:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-proposed main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-proposed main restricted universe multiverse

And there is already plans to create a Xserver Failover:
[https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover](https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover)

:EDIT: to add, The 'dapper-proposed' only partly exists which is why it is not in use. Perhaps it's time to fully implement it.

---

### Post by carontis on 2006-08-24
Surely it would be a big help and the second help could be done to a simple roll-back of entire last good configuration as it is for windows, so you can go back to last good boot without problem and can erase the damaged package. I look too for that possible roll-back, but till today I haven't seen one in the distro. It should be really helpful for all of us! I think we should "vote" for it.

---

### Post by toasted on 2006-08-26
If they would keep the general public release stable there would be  no need for a roll back feature. If it aint broke you dont need to fix it!

Following Debians structure is the best I think... let those who want to do the testing and when its ready, it becomes stable. If the testers break their box, well they are ready willing and able to fix it.

---

### Post by Metacarpal on 2006-08-26
> **toasted said:**
> If they would keep the general public release stable there would be  no need for a roll back feature. If it aint broke you dont need to fix it!

Following Debians structure is the best I think... let those who want to do the testing and when its ready, it becomes stable. If the testers break their box, well they are ready willing and able to fix it.

The problem with that idea is that the devs and testers can't be expected to test each update on every possible configuration of hardware that exists.  They'd never get anything out the door.

So there are inevitably going to be computer setups that they can't be sure it will work on.  So sometimes something will get through that worked great on all of the dev's test systems, but will b0rk about 1000 people's computers.  It's likely that a good many of those 1000 won't be able to get to the forums and figure out how to fix it.

A rollback utility would give a simple, efficient way of restoring functionality in those cases.  I know I'd like to have it in case an update glitch specific to P3 Toshia Tecra laptops ever comes around...

---

### Post by lavigne on 2006-08-27
The message from Ubuntu was giving the instruction for what to do. It was saying you had to be connected to the internet but in my case I did not known how to connect to the internet via the command line. Does anyone know how or where to get the information.

---

### Post by aysiu on 2006-08-27
> **lavigne said:**
> The message from Ubuntu was giving the instruction for what to do. It was saying you had to be connected to the internet but in my case I did not known how to connect to the internet via the command line. Does anyone know how or where to get the information.
```
sudo aptitude update
sudo aptitude install lynx
lynx
```

---

### Post by toasted on 2006-08-27
> **Metacarpal said:**
> The problem with that idea is that the devs and testers can't be expected to test each update on every possible configuration of hardware that exists.  They'd never get anything out the door.

I didnt mean that the devs would be involved in testing, just testers. After all, they are testers, no? Increase the testers count if need be. A post on the forum would surely result in more testers than needed. A few hundred people would be nice! You would have volunteers that are aware that there could be bugs, and also give them an avenue to get info to repair them, report them, and whatever else was needed... a tester forum or the like. 

It could be programmed so that a tester received automatic update notices that an update were available and update just like we do now only with the pre release stuff...

Let the Devs do the dev thing and have testers do the testing thing. 

Once the release had been in the testers environment for a given period of time it becomes 'stable' and gets released to general population. 

> **Metacarpal said:**
> 
A rollback utility would give a simple, efficient way of restoring functionality in those cases.  I know I'd like to have it in case an update glitch specific to P3 Toshia Tecra laptops ever comes around...
That is a good idea too though, both would be very nice to have. This could be equated to XP's System Restore feature and since we have no worry about virus... that part is moot  :D

---

### Post by randell6564 on 2006-08-27
> **lavigne said:**
> The message from Ubuntu was giving the instruction for what to do. It was saying you had to be connected to the internet but in my case I did not known how to connect to the internet via the command line. Does anyone know how or where to get the information.

Not sure that i am understanding you.  Did your X break from the 10.3 xserver update?  How did you get that update if you are not connected to the internet?

If you ARE indeed connected, then there is nothing that you need to do at the command prompt but 
                   sudo apt-get update
                   sudo apt-get install xserver-xorg-core=1:1.2.0-0ubuntu10.4
                   sudo shutdown -r now

---

