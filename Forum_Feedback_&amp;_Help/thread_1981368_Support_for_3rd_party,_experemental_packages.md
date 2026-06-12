---
title: "Support for 3rd party, experemental packages"
date: 2012-05-16
forum: Forum Feedback &amp; Help
---

### Post by niop on 2012-05-16
> **bodhi.zazen said:**
> Define "Best video Experience" - the emgd driver is slower. I do not think Internet speed is any different with the drivers. "office jobs" are faster with gma500_gfx as it provides faster graphics.

The general consensus is people should start with the gma500_gfx driver as it works by default, gives better performance, requires the least effort to maintain, and makes the least changes to the system.

Rather then advising people install the emgd, just list what it is needed for, which is a short list.

Be sure to include the disadvantages in that the emgd is inconsistent with xorg 1.10 (although it may work for well for you, it certainly does not work for everyone) and often people need to downgrade xorg and use custom ppa.


Well, I agree with you for one thing, it's safer to downgrade to the xorg from ppa, appart that :

With this few things :
 - Optimized Kernel
 - Right Grub command line
 - Optimized 10-emgd.conf 

I'm able to browse internet while compiling a newer kernel, or viewing the latest tv show in 576p or 720p while playing a little game card next to it.
And all of that with transparence ( xcompmgr ), and a 
~350 point with glxgears.

So for this little netbook it's way up what i expected, and far from windows xp experience as well.

A little note for a early post : i'm with libva 1.15 that works well with emgd 1.10 and mplayer-vaapi ( 201202 )

Resume of the story :
No, Emgd is not "slow", it needs more adjustments to do it's job, that's all. It's the reason i made a little forum to share my experience and findings.

Best Regards,
Niop

---

### Post by bodhi.zazen on 2012-05-16
> **niop said:**
> Well, I agree with you for one thing, it's safer to downgrade to the xorg from ppa, appart that :

With this few things :
 - Optimized Kernel
 - Right Grub command line
 - Optimized 10-emgd.conf 

I'm able to browse internet while compiling a newer kernel, or viewing the latest tv show in 576p or 720p while playing a little game card next to it.
And all of that with transparence ( xcompmgr ), and a 
~350 point with glxgears.

So for this little netbook it's way up what i expected, and far from windows xp experience as well.

A little note for a early post : i'm with libva 1.15 that works well with emgd 1.10 and mplayer-vaapi ( 201202 )

Resume of the story :
No, Emgd is not "slow", it needs more adjustments to do it's job, that's all. It's the reason i made a little forum to share my experience and findings.

Best Regards,
Niop

I have referred this matter for staff review. I do not think we should allow your activity here. We support Ubuntu.

You are sort of comparing apples to oranges. I can compile custom kernels as well.

What is at issue is you are pushing a personal project, from custom kernels to custom iso, and such support is not really necessary for the gma500.

You will probably be asked to move your 3rd party kernels / iso to your personal web site and on the forums support what is in either the ubuntu repositories or the gma500 ppa.

The packages in the gma500 ppa are marked as experimental, so I do not think you should be advising experimental drivers to the masses.

---

### Post by bodhi.zazen on 2012-05-16
I think with 12.04 we should only support what is in the repositories or the gma500 team ppa, and ask those using third party packages, unreviewed iso / kernels, etc to provide support elsewhere.

In addition, the open driver keeps getting better. The 3.3.4 kernel , available in 12.10, is even better. Installing the 3.3.4 (or higher) kernel from the kernel team's archive is a far better solution then the emgd.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by bodhi.zazen on 2012-05-17
The consensus of the staff is:

For preferred driver for Ubuntu 12.04 is the gma500_gfx / psb_gfx. The reasoning is:

[list][*]This is the driver in the Ubuntu repositories.
[*]The driver works out of the box with minimal configuration.
[/list]

If you have a problem with this driver , the proper thing to do is to file a bug report (rather then advise an experimental driver).


We do not mind if you wish to work on experimental drivers, in this case the emgd, but only with proper documentation and appropriate warnings.

We strongly prefer if you were to:

1. Work with the gma500 team

[https://launchpad.net/~gma500](https://launchpad.net/~gma500)

This allows coordination of effort and peer review.

2. Provide appropriate documentation. "Works for me" is insufficient. Please update the [wiki page](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) with specific instructions.

3. Do not advise this driver to new users.

4. Do not advise this driver as a panacea. The default driver, gma500_gfx, provides adequate functionality and works with Unity, KDE, XFCE, and LXDE, including transparency. The only potential advantages of the emgd is 3d graphics and video acceleration.

[list]
[*]3d graphics are sort of icing on the cake. You can obtain 3d effects on kde, xfce, and even gnome-shell without the EMGD driver. 3d graphics support is NOT REQUIRED to have a functional desktop.
[*]The video acceleration is spotty at best with the emgd. Many users can not get video acceleration working, which defeats the advantage of the driver.
[/list]

5. Be sure to give proper warnings. Using the emgd driver is not clean and easy. It requires custom kernels and significant changes to the system. These changes are not supported in Ubuntu. I made an initial list of warnings:

[list][*]Requires compilation of a custom kernel.
[*]Requires compilation of the EMGD driver.
[*]Requires a custom /etc/X11/xorg.conf
[*]The driver is experimental and although it works for some, it does not work for everyone.
[*]The 3d video drivers are particularly problematic. many people can get the basic driver working, but without the 3d video.
[*]There is no official support from Ubuntu for either custom kernels or the EMGD driver.
[*]There is currently no documentation on how to compile and use the EMGD 1.14 driver.
[*]The EMGD 1.14 driver officially supports Fedora 14 (outdated), kernel 2.6, and xorg 1.9, all of which are very much out of date for Ubuntu 12.04. To use the driver you will need to downgrade all these packages, which means pinning packages from 11.10 or 11.04. Pinning packages from previous releases is not advised for new users, may cause problems or breakage, and is unsupported. 
[/list]

Last, **[COLOR="DarkRed"]we have a problem with 3rd party packages or kernels outside of the gma500 team / ppa[/COLOR]**. If you are going to provide such packages our first choice is that you work with the gma500 team. Second choice would be to **[COLOR="DarkRed"]use a reputable location for your code/iso[/COLOR]** such as a ppa, sourceforge, etc. The continued use of unknown repositories, links to virus infested download pages, and packages / iso not subject to peer review is going to be strongly discouraged/ jailed.

---

### Post by lucazade on 2012-05-17
Do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... anyone agree?

---

### Post by ingcorra on 2012-05-17
> **lucazade said:**
> do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... Anyone agree?

+1

---

### Post by prince_of_death on 2012-05-17
> **lucazade said:**
> Do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... anyone agree?

+1
I second this. This forum is getting way too out of hand.

---

### Post by Anaesthisia on 2012-05-17
> **lucazade said:**
> Do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... anyone agree?
I think the reasonable solution, at the moment, for people who need hardware accelerated video is to go with any of the previous distributions that are documented to work reasonably well.

I don't see any point in suggesting to new users to try experimental configurations, until such time as there is a proven concept for EMGD in 12.04 - that is if that time ever comes.

***A***

---

### Post by bodhi.zazen on 2012-05-17
> **lucazade said:**
> Do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... anyone agree?

That is what the staff suggested. emgd thread would need to be supported by gma500 team, give advice on when and when not to use emgd, and have ***appropriate warnings***.

It is not a "holy war" to caution new users about custom kernels, experimental drivers, pinning old repositories. Until the gma500 team has a working .deb (repository), supporting the emgd is not for the feint of heart or new users.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> Building and using a custom kernel will make it very difficult to get support for your system.

While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation).

If you have a commercial support contract with Ubuntu/Canonical, this will void such support.

Same with compiling, pinning, writing custom xorg.conf, etc.

Tossing out the emgd driver as if it is trivial to install and advising it to new users is not appropriate.

We fully support the gma500 team if they want to develop the driver, test drive it, **document** it's use, give appropriate warnings, etc but the *advising new or inexperienced users to use experimental drivers, the use of shady 3rd party repositories, unreviewed code, custom iso from just anyone*, that has to go.

New users should be advised to stay with the driver in the repository *unless they express a specific need only supported by the emgd, and only advise the emgd if you are willing to support a new user compiling the code, having X fail, etc*.

Otherwise you are advising experimental code to inexperienced users and leaning of staff or others to clean up if a user has a non-functional desktop (yes, I have personally fixed several "broken" Ubuntu 12.04 installs on my blog and on IRC).

The "drive by advice" to use experimental drivers, without documentation and support, is inappropriate. Please stop referring to the issue as a "holy war", it does not help. It is not a holy war , it is *safety first*. If the gma500 team wants to develop and advise an experimental driver, you need to **support it properly**.

---

### Post by bodhi.zazen on 2012-05-17
Posts moved to the discussion thread. Please use this thread for discussion.

If you want to start separate threads, have the gma500 team update the wiki and start a thread with the appropriate cautions. Staff has outlined what we expect if you want to use / advise experimental drivers.

Please stop all the "holy war" ranting and start proper documentation and warnings.

---

### Post by CharlesA on 2012-05-17
> **bodhi.zazen said:**
> 
Please stop all the "holy war" ranting and start proper documentation and warnings.

+1. Experimental drivers and 3rd party downloads generally aren't all that good for a newbie. It is even worse when there is very little documentation.

---

### Post by s.fox on 2012-05-17
I would not encourage supporting the 3rd party driver, especially as the GMA500 team does not offer support for it.

I don't mind threads existing on the subject, but the advice they offer should be used with plenty of warnings.

I don't think advising new ubuntu users to use it is appropriate.

---

### Post by prince_of_death on 2012-05-17
Wasn't the point of this thread being posted was to help user get the best performance from the gma 500???? Hence the name [SIZE="4"]**[all variants] Guide to Get the Best Performace from the GMA 500**[/SIZE] note the words **[all variants]**

where alone the line did the "Admin Staff" decide that it was best to take this thread and turn it into one that forces the use of PSB-GFX/gma500_gfx driver? If we want to talk about how to obtain a custom kernel with the EMGD driver which possibly gives better performance than the gma500_gfx for some users then isn't that our choice? Is it wrong or illegal to share tips with each other on how to get better performance from our graphic card? 
I understand that we should note that the EMGD driver is experimental and not 100 % functional but neither is the gma500_gfx  driver and the way i see it, the EMGD offers some hardware acceleration while the gma500_gfx offers none which kinda makes it better in a way for SOME users depending on their needs. 

I know my post will probably be deleted just like my ones before by some "admins" and i'll probably receive another "harsh worded" private message like i did a while back from these "admins"
I guess i'm not allowed to speak my mind. I'll probably need to become a admin for this site before i can talk anyway i feel to other users. Oh well, i guess i should go find a open source community forum to share my views... oh wait a minute.....

---

### Post by thermatk on 2012-05-17
**bodhi.zazen**, please can you share your ideas on how to get youtube working with gma500_gfx on asus t91mt? My best result was a nice slideshow for 240p. That's really not the way... I can't find any external video accelerator as crystal hd needs mini-pcie and it's unreal
What's your opinion? That's why I still try to use EMGD in any case there is a hope this driver works. If not, I revert to gma500_gfx waiting for vaapi by Alan Cox. I am sure that once it will be done but when this happens might be that I will have another netbook.
So, please express your opinion or stop deleting useful posts. I love free software and I will never buy another PowerVR in my life. ATM I need it to work as a presentation tablet but not to fight for freedom.

---

### Post by bodhi.zazen on 2012-05-17
You can use what you wish on your own personal machine and on your own personal blog.

If you wish to promote the emgd driver here on the forums you will have to step up with the documentation and gma500 team.

No one is telling you you can not use the emgd or that you can not promote it here, just that you need to promote it more appropriately.

---

### Post by bodhi.zazen on 2012-05-17
> **thermatk said:**
> **bodhi.zazen**, please can you share your ideas on how to get youtube working with gma500_gfx on asus t91mt? My best result was a nice slideshow for 240p. That's really not the way... I can't find any external video accelerator as crystal hd needs mini-pcie and it's unreal
What's your opinion? That's why I still try to use EMGD in any case there is a hope this driver works. If not, I revert to gma500_gfx waiting for vaapi by Alan Cox. I am sure that once it will be done but when this happens might be that I will have another netbook.
So, please express your opinion or stop deleting useful posts. I love free software and I will never buy another PowerVR in my life. ATM I need it to work as a presentation tablet but not to fight for freedom.

1. Write an open source solution and share it with us.

2. Complain to intel about their lack of support.

3. Buy Linux compatible hardware, sell your gma500.

Most important - If you wish to promote the emgd driver - **Join the  gma500 team and provide appropriate documentation**.

---

### Post by bodhi.zazen on 2012-05-17
> **thermatk said:**
> **bodhi.zazen**, please can you share your ideas on how to get youtube working with gma500_gfx on asus t91mt? My best result was a nice slideshow for 240p. That's really not the way... I can't find any external video accelerator as crystal hd needs mini-pcie and it's unreal
What's your opinion? That's why I still try to use EMGD in any case there is a hope this driver works. If not, I revert to gma500_gfx waiting for vaapi by Alan Cox. I am sure that once it will be done but when this happens might be that I will have another netbook.
So, please express your opinion or stop deleting useful posts. I love free software and I will never buy another PowerVR in my life. ATM I need it to work as a presentation tablet but not to fight for freedom.

Have you even tried the open source drivers ?

> 12.04 installed on its own partition plays Youtube videos much better than 11.10 with EMGD does. 360p doesn't work smoothly, but 240p is almost perfect. With 11.10, it was almost impossible to play anything.
[http://ubuntuforums.org/showpost.php?p=11892830&postcount=5369](http://ubuntuforums.org/showpost.php?p=11892830&postcount=5369)

Others seem to find it quite adequate, better then the emdg on 11.10, not to mention that the emgd is not working on 12.04.

"It works ..., almost ..., well actually ..." [http://ubuntuforums.org/showpost.php?p=11923790&postcount=5396](http://ubuntuforums.org/showpost.php?p=11923790&postcount=5396)

Not to mention that all the video acceleration you are demanding is not working either

> Currently **mplayer-vaapi is not working well with emgd1.10**, waiting for mplayer and emgd upgrades....

[http://ubuntuforums.org/showpost.php?p=11918490&postcount=5391](http://ubuntuforums.org/showpost.php?p=11918490&postcount=5391)

The old gma500 thread is full of responses from people who prefer the gma500_gfx on 12.04, perhaps you should try it.

Again, you need to ask the gma500 team to step up and provide documentation and support.

---

### Post by godfazr on 2012-05-17
Okay, we all know that you don't like emgd and now we know that you don't trust sites where deb packages with custom kernels with emgd stored.
Will you allow links to PPA's with custom kernels for 12.04 that are using emgd? It may not help all users, but if it will help at least some of them - it will be much better than advising them to live with opensource driver only and pray to get at least Xv working or forcing them to look for information on other web resources, not as trusted as official Ubuntu forums.

---

### Post by bodhi.zazen on 2012-05-17
> **godfazr said:**
> Okay, we all know that you don't like emgd and now we know that you don't trust sites where deb packages with custom kernels with emgd stored.
Will you allow links to PPA's with custom kernels for 12.04 that are using emgd? It may not help all users, but if it will help at least some of them - it will be much better than advising them to live with opensource driver only and pray to get at least Xv working or forcing them to look for information on other web resources, not as trusted as official Ubuntu forums.

Comments such as "we all know that you don't like emgd" are counter productive. The emgd is not working on 12.04 and people are advocating a broken, depreciated driver without providing adequate support. If you want proof, read the last 200 or so posts in the gma500 thread, emgd has mixed results at best.

> Currently **mplayer-vaapi is not working well with emgd1.10**, waiting for mplayer and emgd upgrades....

My advice is for you to work with the gma500 team

[https://launchpad.net/~gma500](https://launchpad.net/~gma500)

They are a great group and working together allows peer review, sharing of code and solutions, and sharing the responsibilities of support (if the emgd driver breaks) and documentation.

Again, the point is, if you want to advocate the emgd driver here, please improve the quality of support. As it stands now, support is substandard as there are no (peer reviewed) 12.04 packages in the gma500 ppa, mixed results getting the driver working in 12.04, and no documentation on the wiki page.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

So if you are wanting to advocate the emgd driver here, get to work (with the gma500 team) to provide documentation, support, and working packages.

---

### Post by lisati on 2012-05-17
> **godfazr said:**
> Okay, we all know that you don't like emgd and now we know that you don't trust sites where deb packages with custom kernels with emgd stored.
Will you allow links to PPA's with custom kernels for 12.04 that are using emgd? It may not help all users, but if it will help at least some of them - it will be much better than advising them to live with opensource driver only and pray to get at least Xv working or forcing them to look for information on other web resources, not as trusted as official Ubuntu forums.

It's not so much about "liking" or "disliking" the packages in question, but (a) working out what level of support we can offer here in the forum, and (b) encouraging our forum members to help improve the experience of those using them by working with the developers.

---

### Post by godfazr on 2012-05-17
> **lucazade said:**
> Do we want to close this thread and split into two separate (emgd and gma500_gfx)?
This thread looks like a holy war and rather difficult to follow... anyone agree?
agree.

> **bodhi.zazen said:**
> Comments such as "we all know that you don't like emgd" are counter productive. The emgd is not working on 12.04 and people are advocating a broken, depreciated driver without providing adequate support. 
Come on, there was a post with links to custom kernel for 12.04 with working emgd at least for some systems, but you didn't give the chance to even try it by removing that post. You don't trust the site and saying about the viruses? Viruses that will works under Linux? Okay, even if they will - I'd like to try that kernel, on my own risk. But you forcing me to search for this link via google, or whatever search system you like, and find it on even more untrusted sites.

> **lisati said:**
> It's not so much about "liking" or "disliking" the packages in question, but (a) working out what level of support we can offer here in the forum, and (b) encouraging our forum members to help improve the experience of those using them by working with the developers.
a) I'm not developer, I don't want to "dance with tambourine". So I accept any level of support that will make my damn Acer work as I need.
b) When someone removes posts with solution that may work for at least some of users, it forcing those who wants to help in any way to give up proposing their solutions.
There's no even promises for working Xv for psb_gfx. And also, EMGD is not experimental driver - it's an official driver, no matter if you like it or not. It doesn't support Ubuntu 12.04, but we all know that Ubuntu is far ahead from even Debian which it is based on and in fact it's Debian unstable. So please do not call driver that is officially not finished and officially not declared to be finished ever as better solution than outdated, but still working with some modifications, complete driver from hardware vendor. At least until it will become significantly better.

---

### Post by bodhi.zazen on 2012-05-17
> **godfazr said:**
> Come on, there was a post with links to custom kernel for 12.04 with working emgd at least for some systems, but you didn't give the chance to even try it by removing that post. You don't trust the site and saying about the viruses? Viruses that will works under Linux? Okay, even if they will - I'd like to try that kernel, on my own risk. But you forcing me to search for this link via google, or whatever search system you like, and find it on even more untrusted sites.


We do not support 3rd party repositories. As far at the EMGD goes it is the official Ubuntu repositories or the gma500 team ppa.

> a) I'm not developer, I don't want to "dance with tambourine". So I accept any level of support that will make my damn Acer work as I need.

OK, use the gma500_gfx. 


> b) When someone removes posts with solution that may work for at least some of users, it forcing those who wants to help in any way to give up proposing their solutions.

Now you are just distorting the facts. The only posts that were removed were to 3rd party repos.

> There's no even promises for working Xv for psb_gfx.

No one has Xv working on the emgd. Now you are just making demands for things that do not exist.

> And also, EMGD is not experimental driver - it's an official driver, no matter if you like it or not.

I think you missed the release notes on the EMGD 1.14. Intel supports Fedora 14, kernel 2.6, and xorg 1.9 , none of that applies to Ubuntu 12.04.

As Ubuntu 12.04 is not officially supported, the emgd driver is either depreciated or experimental, your choice.

No matter if you like it or not, Ubuntu 12.04 is not officially supported. Your claim to the contrary is simply a misrepresentation of what Intel supports. A fantasy.


> It doesn't support Ubuntu 12.04, but we all know that Ubuntu is far ahead from even Debian which it is based on and in fact it's Debian unstable. So please do not call driver that is officially not finished and officially not declared to be finished ever as better solution than outdated, but still working with some modifications, complete driver from hardware vendor. At least until it will become significantly better.

Again, you are posting / ranting in the wrong place. EMGD is not maintained by Debian, Ubuntu, or Canonical.

EMGD is maintained and supported by INTEL.

You are simply demanding things that do not exist and looking for support in the wrong places. When you do not find the answers you think exist somewhere you are displacing your frustration onto me. Please direct your frustration at Intel.

At this point your options are:

1. Become a developer and reverse engineer the emgd yourself.

2. Ask Intel for support for the emgd driver on Ubuntu 12.04.

3. Use the gma500_gfx.

4. If you have a problem with the gma500_gfx, file a bug report. The bug may not be with the gma500_gfx, it may be with Xv.

5. Purchase hardware that has the capabilities you desire and is compatible with Linux. You can get hardware with the capabilities you stipulate for $20.

Sorry you do not like the options, but it is frankly immature and inappropriate for you to take your frustration out on me.

As of the time of this post, there is no pre-packaged EMGD for you to use with Ubuntu 12.04, neither intel nor the gma500 team has provided one.

---

### Post by mikewhatever on 2012-05-18
> **godfazr said:**
> ...

Will you allow links to PPA's with custom kernels for 12.04 that are using emgd? It may not help all users, but if it will help at least some of them - it will be much better than advising them to live with opensource driver only and pray to get at least Xv working or forcing them to look for information on other web resources, not as trusted as official Ubuntu forums.

Ubuntuforums is a trusted and reputable resource, and I'd like it to stay that way. I don't want it to become a collection of custom ISO links from just anyone and everyone, in which case, it would be neither trusted nor reputable. It's about time the forum staff took action, and I fully support the measures.

I am sure you'll manage to contact noip and get the links that were removed.

---

### Post by Perfect Storm on 2012-05-18
Not much I can say that haven't been said by my fellow admins. I agree with them.

---

### Post by prince_of_death on 2012-05-18
It amazing how these "Admins" dislike any comments and post that has to do with the EMGD driver but just wouldn't stop talking about the gma500_gfx driver as if its the solution. In case you haven't notices gma500_gfx is just as "experimental" as the EMGD as they clam. We all know EMGD is not available for Ubuntu **12.04** so what? Just because some "Admins" want to use 12.04 doesn't mean we all do. Some of us are very happy with 11.10 and EMGD impaired to 12.04 with gma500_gfx thats only HALF WAY working. 
Yes i have tried gma500_gfx on Ubuntu 12.04 for a week and went running back to 11.10 with EMGD.

How in the world can some of these "Admins" promote a half working driver with NO 3D (and probably might never have) as if its the solution to everything GMA500.

We all get that some "admins' here hate the EMGD driver so maybe they should take their own advice and go open their own thread or personal site where they can try to force the gma500_gfx on everyone. 
I prefer to my right to choice with driver to use on my personal pc without these "admins" trying to erase every record of EMGD from this forum and replace it with their so called better driver gma500_gfx

---

### Post by bodhi.zazen on 2012-05-18
> **prince_of_death said:**
> It amazing how these "Admins" dislike any comments and post that has to do with the EMGD driver but just wouldn't stop talking about the gma500_gfx driver as if its the solution. In case you haven't notices gma500_gfx is just as "experimental" as the EMGD as they clam. We all know EMGD is not available for Ubuntu **12.04** so what? Just because some "Admins" want to use 12.04 doesn't mean we all do. Some of us are very happy with 11.10 and EMGD impaired to 12.04 with gma500_gfx thats only HALF WAY working. 
Yes i have tried gma500_gfx on Ubuntu 12.04 for a week and went running back to 11.10 with EMGD.

How in the world can some of these "Admins" promote a half working driver with NO 3D (and probably might never have) as if its the solution to everything GMA500.

We all get that some "admins' here hate the EMGD driver so maybe they should take their own advice and go open their own thread or personal site where they can try to force the gma500_gfx on everyone. 
I prefer to my right to choice with driver to use on my personal pc without these "admins" trying to erase every record of EMGD from this forum and replace it with their so called better driver gma500_gfx

Because the gma500_gfx is an official Ubuntu package, so it is supported here.

No one is stopping you from promoting the EMGD, show us the documentation , show us the packages.

Rather then ranting here your time is better spent with the gma500 team.

---

### Post by s.fox on 2012-05-18
I have seen enough.  You have been given the same advice several times. Take it.

Thread Closed.

---

### Post by bodhi.zazen on 2012-05-18
> **s.fox said:**
> I have seen enough.  You have been given the same advice several times. Take it.

Thread Closed.

Just to bring the discussion to closure :

FWIW - Staff sort of has had enough of the emgd and "holy wars" , and I have had enough of fixing broken emgd systems.

Last stable release from the gma500 team was Maverick , Ubuntu 10.10

[https://launchpad.net/~gma500/+archive/ppa](https://launchpad.net/~gma500/+archive/ppa)

gma500 team labels the driver as "Experimental" or "Development" for ubuntu 11.04 and 11.10. There are no packages for 12.04.

Posts outside of the gma500 team are considered off topic and are no longer supported here.

If you disagree with this decision, you are free to add it to the FC agenda.

Please don't kill the messenger ;)

---

