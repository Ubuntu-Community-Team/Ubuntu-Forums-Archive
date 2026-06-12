---
title: "Debian definitely much easier &amp; working than Ubuntu  ?"
date: 2007-01-13
forum: Debian
---

### Post by patrick295767 on 2007-01-13
Hi, 

I have this experience with Debian.
Just apt-get install and everythg works very very well, not buggy applications, no loose of time. 
That Debian is an huge rock that is more more easier than Ubuntu since all applications are just needing simple: 
```
apt-cache search
apt-get install 
```
No need of looking into wiki or ubuntu forum to make sthg or any program working
  
  
That 's my experience from moving from Ubuntu to Debian. 
 
Long life to Ubuntu too !! Long life to Linux machines !

---

### Post by mips on 2007-01-13
Well it is Debian. As you mentioned it gives you no shite.

---

### Post by AgenT on 2007-01-13
What release of Debian are you using? What distrib? Are you using Testing, Unstable, Stable or a combination?

Debian is known for stability and also for having many different options. 

As an example, GNOME 2.6 is standard on Ubuntu Edgy which means it is considered "stable". That same exact version of GNOME and more than likely the same exact packages in Debian are considered "experimental" with a big warning. It is not even unstable!

Debian distrib layout is: oldstable -> stable -> testing -> unstable -> experimental

Any Debian user is more than welcome to install experimental packages if they so choose.

One thing to note: Ubuntu is based on Debian and uses apt-get just like Debian. The difference is that Ubuntu developers add a few extra packages and automatically re-package most Debian ones. It so automated that packages made only for Debian are in Ubuntu. Packages that are useless in Ubuntu. Also a number of Debian packages do not make it into Ubuntu until a release or so after.

---

### Post by Rodneyck on 2007-01-13
So, to sum up, you are saying Debian has more cutting-edge packages, and as a result is less stable?  Sorry, just confused by your statements.  :)

---

### Post by AgenT on 2007-01-13
> **Rodneyck said:**
> So, to sum up, you are saying Debian has more cutting-edge packages, and as a result is less stable?  Sorry, just confused by your statements.  :)No.

If you really want to sum up, here it is:
 Debian is known for stability as well as for having many different options.

Ubuntu just has "stable" where Ubuntu's "stable" does not count as "stable" in Debian. My point with GNOME 2.6 can be summed up like this: Ubuntu and Debian have different definitions of what stable is and also what can and cannot be considered stable. What Ubuntu considers stable can sometimes be considered unstable or even experimental in Debian. The same exact package will be considered stable in Ubuntu and unstable in Debian.

Ubuntu also has two types of release classification: stable (or release) and unstable (pre-release). For example, right now, Edgy is stable because it is a release (the current one in fact) and Feisty is unstable because it is a pre-release.

However, Ubuntu does not distinguish stable and unstable on a per-package basis but as a whole distribution.

Debian, like Ubuntu, distinguishes on a release basis, but it also distinguishes on a per-package basis. This means that every package must meet certain guidelines before it is allowed to move on in the system. 

Debian has four types of inter-release classification (oldstable does not count): stable, testing, unstable and experimental. Ubuntu has none. This is why Debian has more options. You can have a system using a testing repository but install that bleeding edge program from experimental. This cannot be done in Ubuntu because inter-release classifications do not exist. 

Ubuntu, like Debian, has release classifications. Installing Feisty packages on Edgy is asking for disaster. This is similar to how Debian's stable releases work. Installing an Etch package in Sarge is not a good idea. This is why both Ubuntu and Debian have backports.

---

### Post by xabbott on 2007-01-14
> **patrick295767 said:**
> Hi, 

I have this experience with Debian.
Just apt-get install and everythg works very very well, not buggy applications, no loose of time. 
That Debian is an huge rock that is more more easier than Ubuntu since all applications are just needing simple: 
```
apt-cache search
apt-get install 
```
No need of looking into wiki or ubuntu forum to make sthg or any program working
  
  
That 's my experience from moving from Ubuntu to Debian. 
 
Long life to Ubuntu too !! Long life to Linux machines !

Wow, that sounds **exactly** like the experience an Ubuntu user will have without 3rd party repos. *gasp*

I use [Archlinux]("http://archlinux.org") but have used Debian a lot. I can easily say the difference between Debian Etch and Ubuntu is small.

If you don't know much about Linux and want to have the latest software in Linux, Ubuntu's release cycle makes that easy. Also it's popularity and bleeding edge seems to have made it easier to get Ubuntu debs for many projects. In Debian we just use Sid (unstable) repos if we want that.

If you have stability issues with Ubuntu or Debian, it's probably from software outside of the repos.

---

### Post by AgenT on 2007-01-14
> **xabbott said:**
> If you don't know much about Linux and want to have the latest software in Linux, Ubuntu's release cycle makes that easy. This is true, but not always. The release cycle actually prohibits new software from being used for a 6month period. Thus if someone needs a new (it happens sometimes) piece of software, if that person uses Ubuntu chances are they are out of luck because that new piece of software will usually go into Debian first, then pre-release Ubuntu and then, once the pre-release Ubuntu is no longer pre-release, into the newest Ubuntu release. Mixing pre-release Ubuntu packages with release Ubuntu should not be done and backports only start after the pre-release becomes a normal release.

> **xabbott said:**
> If you have stability issues with Ubuntu or Debian, it's probably from software outside of the repos.You are correct about this and probably is the key word. The software in Ubuntu is sometimes bug filled because Ubuntu sometimes takes bleeding edge packages from Debian, which can result in packages tagged "experimental". Not always, just sometimes. But problems with official repository software can and do happen because of this.

Right now, Ubuntu is riding a wave of hype or popularity. To add to xabbott's comment, Ubuntu is just a distribution not much better or worse than any other. It works for some people, while another distribution works for others. That is what makes GNU/Linux great: freedom.

---

### Post by patrickfromspain on 2007-01-14
I have switched to debian... One thing missing: this community :D

---

### Post by Rodneyck on 2007-01-15
I am tinkering around with Debian on my second hard drive and I must say, out of the box, there is a lot of work to be done by the usr to set up programs, drivers, sound (did not detect mine), etc.

I do not mind, because I like the tinkering part, but I now have a new found appreciation for Automatrix2 which sets up the codecs, browsers with plugins, extra fonts and all the other proprietary junk.  All this has to be down via finding the right guides and doing by hand in Debian.

---

### Post by jdhore on 2007-01-15
Yeah, i've used both Ubuntu and Debian and i gotta say...while Debian doesn't come pre-installed with **** and it's faster and more stable, Ubuntu's slightly easier because you don't need to install/configure everything...

---

### Post by neoflight on 2007-01-15
why do they have 22 cd images!!! ..which one do i need if i want to install the testing !

---

### Post by jdhore on 2007-01-15
> **neoflight said:**
> why do they have 22 cd images!!! ..which one do i need if i want to install the testing !

if you want to install ANY version of Debian, i HIGHLY recommend doing a netinstall...it's a 120MB CD ISO and it installs a base system and then goes to the repos and downloads all the other "necessary" packages and installs them...including your GUI and everything else...now that i think of it, i wish Ubuntu had the option to do a netinstall

---

### Post by mips on 2007-01-15
> **jdhore said:**
> if you want to install ANY version of Debian, i HIGHLY recommend doing a netinstall...it's a 120MB CD ISO and it installs a base system and then goes to the repos and downloads all the other "necessary" packages and installs them...including your GUI and everything else...now that i think of it, i wish Ubuntu had the option to do a netinstall

I'll second that. I recently did the same with OpenBSD & done it with debian as well.

---

### Post by jdhore on 2007-01-15
> **mips said:**
> I'll second that. I recently did the same with OpenBSD & done it with debian as well.

i didn't know OpenBSD had a netinstall...sweet...

---

### Post by Rodneyck on 2007-01-15
> **mips said:**
> I'll second that. I recently did the same with OpenBSD & done it with debian as well.

I third that notion.  Kudos to the net install.

However, if I did not have a fast internet connection, there would be lots of profanity slung about for sure.  :-D

---

### Post by mips on 2007-01-16
> **jdhore said:**
> i didn't know OpenBSD had a netinstall...sweet...

Depending on the arch go to [ftp://ftp.openbsd.org/pub/OpenBSD/4.0/i386](ftp://ftp.openbsd.org/pub/OpenBSD/4.0/i386) and download **cd40.iso**.

It's very small but it's all you will need. you could even do it off floppy but I prefer the cd.

---

### Post by Canis familiaris on 2007-01-16
One can use apt-get, aptitude, an deb packages in Ubuntu as easy if not easier than in Debian.
Alternatively Synaptic Package Manager makes it a breeze to install apps.

---

### Post by jdhore on 2007-01-16
> **Anurag_panda said:**
> One can use apt-get, aptitude, an deb packages in Ubuntu as easy if not easier than in Debian.
Alternatively Synaptic Package Manager makes it a breeze to install apps.

umm...the way to install packages between Ubuntu and Debian is almost EXACTLY the same except in Debian, there's no add/remove apps thing in the applications menu

---

### Post by AgenT on 2007-01-16
> **jdhore said:**
> umm...the way to install packages between Ubuntu and Debian is almost EXACTLY the same except in Debian, there's no add/remove apps thing in the applications menu
You are correct. How can aptitude and apt-get be easier to use on Ubuntu than Debian is beyond me. They are the same program on Debian and Ubuntu, except being more up-to-date on Debian since both of them are Debian programs.

In fact, Debian provides more programs and functions than Ubuntu when it comes to aptitude, dpkg and apt-get. The reason is that some programs/functions where made to only work with Debian. Ubuntu does include the extra packages due to the  automation of Ubuntu deb building but they serve no purpose except to increase the Ubuntu package count. One quick example is the ability to view all opened bugs pertaining to the applications you are about to install.

---

### Post by jdhore on 2007-01-16
> **AgenT said:**
> You are correct. How can aptitude and apt-get be easier to use on Ubuntu than Debian is beyond me. They are the same program on Debian and Ubuntu, except being more up-to-date on Debian since both of them are Debian programs.

In fact, Debian provides more programs and functions than Ubuntu when it comes to aptitude, dpkg and apt-get. The reason is that some programs/functions where made to only work with Debian. Ubuntu does include the extra packages due to the  automation of Ubuntu deb building but they serve no purpose except to increase the Ubuntu package count. One quick example is the ability to view all opened bugs pertaining to the applications you are about to install.

true...the only difference between apt on Ubuntu and apt on Debian Stable is that apt on Ubuntu requires you to use signed packages...

---

### Post by tturrisi on 2007-01-18
re debian "satble" and ubuntu "stable".
The term "stable" ONLY applies to debian.  There is no such thing as ubuntu "stable".
NO ubuntu release was ever a "stable" release, there have only ever been ubuntu releases that were no longer beta releases.  But all ubuntu releases are experimental releases.  There is nothing stable about ubuntu except for the fact that there are regular new releases built out of a combination of debian packages.  The only distro that reliably uses the term "stable" is debian. Ubuntu has betas & final releases, that's all.

This is not to say that ubuntu is unstable or undependable, it definitely is more workable than most debian based distros, but new ubuntu releases are not dependable as production machines nor should new releases be counted upon for stable-regular-dependable workstation use in a business environment.  Ubuntu is a "play toy" for we geeks and wanabe geeks while older ubuntu versions may suffice as somewhat dependable office workstations.

These support forums are not bussling with activity because we all lack people to talk to, it is busy here because there are so many issues and problems that arise in different systems we have.  Such issues can be expected when  a disto uses debian experimental and unstable packages.

---

### Post by AgenT on 2007-01-18
> **tturrisi said:**
> re debian "satble" and ubuntu "stable".
The term "stable" ONLY applies to debian.  There is no such thing as ubuntu "stable".
NO ubuntu release was ever a "stable" release, there have only ever been ubuntu releases that were no longer beta releases.  But all ubuntu releases are experimental releases.  There is nothing stable about ubuntu except for the fact that there are regular new releases built out of a combination of debian packages.  The only distro that reliably uses the term "stable" is debian. Ubuntu has betas & final releases, that's all.

This is not to say that ubuntu is unstable or undependable, it definitely is more workable than most debian based distros, but new ubuntu releases are not dependable as production machines nor should new releases be counted upon for stable-regular-dependable workstation use in a business environment.  Ubuntu is a "play toy" for we geeks and wanabe geeks while older ubuntu versions may suffice as somewhat dependable office workstations.

These support forums are not bussling with activity because we all lack people to talk to, it is busy here because there are so many issues and problems that arise in different systems we have.  Such issues can be expected when  a disto uses debian experimental and unstable packages.You are correct, no Ubuntu release was really stable in the Debian sense of stable. That was already covered in a previous post. 

Ubuntu stable release is not even close to being stable in the Debian sense. In fact, it is not even testing quality, especially Edgy. Ubuntu stable releases are more akin to Debian unstable. Ubuntu stable releases are more or less Debian unstable + Debian experimental + some extra Ubuntu specific packages + some patches. Not exactly that, but close. That does not make Ubuntu a bad distribution, but it surely makes it different. Some people like it, some people do not.

And yes, Ubuntu does have stable releases. See the official [Ubuntu Release]("https://wiki.ubuntu.com/Releases") wiki page. Here is a quote:
> **Stable**[LIST]
[*] [EdgyEft]("https://wiki.ubuntu.com/EdgyEft") (6.10; Released October 26, 2006)
[*] [DapperDrake]("https://wiki.ubuntu.com/DapperDrake") - (6.06 LTS; Released June 1, 2006)
[*] [BreezyBadger]("https://wiki.ubuntu.com/BreezyBadger") (5.10; Released October 13, 2005)[/LIST]Stable is a word that different people and organizations use differently to define their releases. For example, I could take Debian experimental, freeze the packages, add my own Distro X packages and release it as Distro X Stable Edition with my pre-release packages being called pre-release or unstable.

---

### Post by xabbott on 2007-01-18
In Debian "stable" == packages from 3 years ago. Yea....

---

### Post by tturrisi on 2007-01-19
> **xabbott said:**
> In Debian "stable" == packages from 3 years ago. Yea....
Not quite that old entirely, however that is no different than any other operating system on the market today.  XP is almost 7 years old and for all intents and purposes was not considered "stable" until service pack 2 was released.  Same w/ all earlier MS systems since win95.  Vista will be released shortly to broad public but will be far from "stable" per a debian sense of the word.

---

### Post by r4ik on 2007-01-19
It is so freakin stable that it does not recognize my HD
Did not even bother to figure it out.

---

### Post by cunawarit on 2007-01-20
> **xabbott said:**
> In Debian "stable" == packages from 3 years ago. Yea....

That's a slight exaggeration, and it really depends what you want to do with the OS anyway.

If you really want the latest software then you wouldn't use Debian stable. You'd choose Debian testing, or a spin off distro like Ubuntu.

Also yes Debian moves slowly, but so do some other OSs. Windows XP is aincient, and service packs don't exactly come out every 6 months. 

At home I am perfectly happy with XP Service Pack two, and Debian Etch.

---

### Post by AgenT on 2007-01-21
> **r4ik said:**
> It is so freakin stable that it does not recognize my HD
Did not even bother to figure it out.Debian Stable is about 1 year 6 months old (not 3 years as some misinformed poster above mentioned). This means the kernel in stable is a little over 1 and 6 months old (in features, not security). The difference is that Debian has a much larger scope than Ubuntu and you may have chosen the wrong kernel, wrong install option, etc. Debian Testing has a newer kernel than Ubuntu Edgy and therefore has at least as good, if not better, hardware support. I do not follow kernel changes so it may be that the newer kernel does not offer new hardware support, only bug fixes for non-hardware releated issues.

It is probably not advisable to use Debian Stable on a desktop. And the new Stable is already frozen and awaiting last minute bug fixes before release. It should be released in a few weeks, but as appropriate for any truly stable system, it will be called stable only after it really becomes stable, not because some release date mandates the title. In other words, "when it's done".

Testing is good enough for a desktop and still more stable than Ubuntu "stable". Also, popular opinion is that Debian Testing does not receive security updates. This is wrong since 2005. Debian Testing now has its own [Security Team]("http://secure-testing-master.debian.net/").

And Debian is not for everyone. Ubuntu is a good choice for some and there is nothing inherently wrong with it. It is just different. Sort of like KDE and GNOME. Some prefer the former, some the latter.

It was best put by the author of Debian System, Martin Krafft:
"Debian may not be the best choice for your first steps in the Linux world. If you are choosing Linux because you have had enough and want to author your documents, compose messages, and browse the Web on a [more] stable, secure, and free operating system from now on, then you may want to consider one of the Debian derivatives... They are frequently optimized for specific applications or target a specific user base, which makes them simpler to learn... These distributions do not handle the broad set of applications that Debian supports and can thus do with less flexibility (and complexity). Once you have learnt to walk with one of these, you can always come back to Debian..."
(page 22, 1st Ed.)

But from my somewhat extensive experience with the Ubuntu community, there is a lot more hostility, propaganda and just childishness coming from the Ubuntu community towards the Debian community than vice-versa. And this has been getting much worse in the past year. That has been my observation. Maybe it is due to Ubuntu attracting novice users or former Windows users, I do not know. However, this does not apply to the Ubuntu developers (especially the core ones) so far as I am aware as they are more knowledgeable and have respect for Debian.

---

### Post by mips on 2007-01-21
> **AgenT said:**
> 
But from my somewhat extensive experience with the Ubuntu community, there is a lot more hostility, propaganda and just childishness coming from the Ubuntu community towards the Debian community than vice-versa. And this has been getting much worse in the past year. That has been my observation. Maybe it is due to Ubuntu attracting novice users or former Windows users, I do not know. However, this does not apply to the Ubuntu developers (especially the core ones) so far as I am aware as they are more knowledgeable and have respect for Debian.

Have to agree there. A lot of people seem to have an opinion but actually know very little. Btw, I'm not claiming to know anything.

---

### Post by AgenT on 2007-01-21
> **mips said:**
> Have to agree there. A lot of people seem to have an opinion but actually know very little. Btw, I'm not claiming to know anything.For some reason, some Ubuntu users think that slandering other distributions is actually productive and actually think that Ubuntu is somehow vastly superior to all others which is not so. It is different and does things somewhat differently than other distributions. Ubuntu, Debian and even Fedora and Gentoo are much more similar than they are different. And in the end, all of them are GNU/Linux. A few years ago, maybe even one year ago, there was none of this hostility in the Ubuntu community.

Maybe an analogy would help: think of Ubuntu, Debian and Fedora as different people from different parts of the world. In the end they are all human. Strange that a distribution that champions "humanity to others" has a userbase that is one of the most hostile towards others. Do remember that I am talking about some of its users, not all and definitely not the developers.

---

### Post by xabbott on 2007-01-21
> **AgenT said:**
> For some reason, some Ubuntu users think that slandering other distributions is actually productive and actually think that Ubuntu is somehow vastly superior to all others which is not so. It is different and does things somewhat differently than other distributions. Ubuntu, Debian and even Fedora and Gentoo are much more similar than they are different. And in the end, all of them are GNU/Linux. A few years ago, maybe even one year ago, there was none of this hostility in the Ubuntu community.

Maybe an analogy would help: think of Ubuntu, Debian and Fedora as different people from different parts of the world. In the end they are all human. Strange that a distribution that champions "humanity to others" has a userbase that is one of the most hostile towards others. Do remember that I am talking about some of its users, not all and definitely not the developers.

I was a  Debian user before every trying Ubuntu (and now use Arch). I've been using Linux to varying degrees since about late 98. I'm not trying to insult Debian. My remake about the age of the stable release was sarcasm. I think everyone makes jokes about Debian's (stable) age.

What I happen to see more in this forum is Ubuntu users who feel they've "graduated" to Debian. When in a way, that's insulting to Debian itself. I've posted this on the Debian forums too. Debian (Etch) is **not** harder than Ubuntu to install or use. It's honestly reached a point where the difference is so small. Then people tell themselves it's faster and/or more stable. But aside from Sarge I just don't see it. A knowledgeable Linux user can make Debian and/or Ubuntu slim and quick. 

One of reasons I wouldn't suggest Debian to a new desktop user right now is because Etch hasn't been released. Also, if you are the type of Windows user who wants to use the latest and greatest Debian won't be for you unless you are comfortable using Sid. I typically used Sid and was fine with it. But I'm not going to tell new users to do that.

Ubuntu is desktop oriented and if you are a typical new linux desktop user I don't see any reason not to use it over Debian. Debian on the other hand is much more versatile in terms of installation methods, package choices, and architectures in which it will run on. Also depending on your needs Debian's slower release cycle will be beneficial. It's never been my intention to bash Debian. Only dispell this myth that Debian is where you go once you've "mastered" Ubuntu.

---

### Post by tturrisi on 2007-01-22
> ...Only dispell this myth that Debian is where you go once you've "mastered" Ubuntu.
good point!
On the contrary, hacking up ubuntu can be great fun and quite educational!

I used debian long before I ever tried ubuntu.  (I have a woody server that's been running 24/7 for 5 years, only reboots are due to power outages)  I tried ubuntu so as to be able to get debian installed on my laptop dual boot w/ xppro.  Previous atempts at using debian on the laptop failed because the hardware support I needed did not yet exist.  So prior to trying a hd install I used ubuntu live to see if it had the needed hw support.  It did, so I installed to disk.  Later on, I replaced the ubuntu install w/ etch so as to fulfill my original goal of using debian on the laptop.

---

### Post by handy on 2007-01-25
For cutting edge Debian, with complete compatibility repo' wise there is also Sidux, basicaly the new Kanotix really. Another way to get stable sid, good community a lot smaller & tighter than the monster sized Ubuntu community.

---

### Post by rabid emu on 2007-01-25
I wanted to try Debian and even made a 3rd partition on my laptop to do a netinstall of the newest RC of Etch (I want a desktop system, not a server, so I naturally want the latest stuff at the cost of 'stability' (not that any linux distro is really that 'unstable' in the sense of Windows, where it crashes several times a month...I've almost never had Ubuntu crash and when it has I know exactly what went wrong and how to fix it, and it was almost always my fault)).  The install of Debian worked fine I suppose but once it was installed I realized that, like every other Linux distro I've tried except for Ubuntu, my wireless card wasn't working.  As I'm on a laptop this is important to me.  Building the ipw3945abg driver is a real bitch (I've tried unsuccessfully on FC5, FC6, and Debian).  Also I saw that, basically, Debian felt the same as Ubuntu, it had the same basic programs (synaptic, apt...) and the same appearance apart from the themes and logo).  I didn't see much of a difference between running Debian and Ubuntu, except that Ubuntu supported my wireless card.  So now I have Kubuntu Feisty Herd 2 installed on that partition and it's been working great; incredibly stable in fact.

---

### Post by Tuna on 2007-01-26
Hey, I've been researching a bunch of different distro's a bit (I don't know a whole lot about them) to see if I might want to try something else.  I'm relatively new to Linux in general as I only have about 3 months or so of experience with Ubuntu now.  Overall I'm happy with Ubuntu.  I have the occasional problem, but nothing too terribly difficult to figure out, especially since there's so much info on this forum.  Does it seem like a viable option to install Debian in my case?  I'm kind of a stickler for getting all the latest and greatest software updates as long as it doesn't sacrifice the stability too incredibly much.  I read this whole thread and somebody said Debian Testing is just as stable if not moreso than Edgy (which is what I'm running now).  Is this truly the case?  I'd probably rather run Testing than Stable since Stable is 1.5 years old as I read earlier in this thread.  I have no problems at all with the using terminal or anything, and have never used Automatrix or anything like that (if that matters).  This is going on my laptop, so wireless is a must.  And considering the post above mine, I definitely would leave Ubuntu on my laptop and make another partition just in case I couldn't get wireless to work (obviously), but the overall goal would be to switch from Ubuntu to something else.  The other distro I was considering is Mandriva.  Any insight is appreciated.

---

### Post by r4ik on 2007-01-27
Try,

[http://distrowatch.com/?newsid=03992#0](http://distrowatch.com/?newsid=03992#0)

It is a mandriva based live cd with install option.

---

### Post by yigal.weinstein on 2007-01-27
I think it really has to do with what you want.  I am invested in free software.  Debian is a good distribution but I think it compromises usability for total control of the OS.  This is very good, for instance, for a server where the use of a computer is not necessarily for graphic, text, etc. manipulation, games, but for possibly unique roles in a cluster etc..

If you want the latest and greatest make a Feisty chroot.

I lump Mandriva, Fedora (i.e. Red Hat), OpenSuse into the same bag.  Their interest is to create an OS but they are unwilling to see the ramifications of what free software will allow.  They are not unique and while they may create good quality products the hart that is in Ubuntu cannot and will not be in these other distributions, and I don't think they will ever be.

If this is not a concern to you then it doesn't matter which distribution you choose.

I am a vegan, I meditate for fun, and believe that each action I make does create a difference however small but meaningful.   Ubuntu is a distribution that insists that good software should be available to humanity as a whole for no $ and if possible the code should be open source, gpl, lgpl etc..  This to me is common sense and so I plan to stay with this distribution for as long as Ubuntu stays true to the values it has explicitly set down.

> **Tuna said:**
> Hey, I've been researching a bunch of different distro's a bit (I don't know a whole lot about them) to see if I might want to try something else.  I'm relatively new to Linux in general as I only have about 3 months or so of experience with Ubuntu now.  Overall I'm happy with Ubuntu.  I have the occasional problem, but nothing too terribly difficult to figure out, especially since there's so much info on this forum.  Does it seem like a viable option to install Debian in my case?  I'm kind of a stickler for getting all the latest and greatest software updates as long as it doesn't sacrifice the stability too incredibly much.  I read this whole thread and somebody said Debian Testing is just as stable if not moreso than Edgy (which is what I'm running now).  Is this truly the case?  I'd probably rather run Testing than Stable since Stable is 1.5 years old as I read earlier in this thread.  I have no problems at all with the using terminal or anything, and have never used Automatrix or anything like that (if that matters).  This is going on my laptop, so wireless is a must.  And considering the post above mine, I definitely would leave Ubuntu on my laptop and make another partition just in case I couldn't get wireless to work (obviously), but the overall goal would be to switch from Ubuntu to something else.  The other distro I was considering is Mandriva.  Any insight is appreciated.

---

### Post by mips on 2007-01-27
> **Tuna said:**
> Does it seem like a viable option to install Debian in my case?  I'm kind of a stickler for getting all the latest and greatest software updates as long as it doesn't sacrifice the stability too incredibly much.

Try Sidux which is based on Debian Sid, they just try to stabalise it . Still uses the debian repos.

---

### Post by handy on 2007-01-27
> **mips said:**
> Try Sidux which is based on Debian Sid, they just try to stabalise it . Still uses the debian repos.

+ 1 :) 

***_[http://sidux.com/](http://sidux.com/)_***

---

### Post by M_the_C on 2007-01-27
Debian was the first Linux distro I tried and I gave up because it was too much too fast.

About half a year later I tried Ubuntu and found it very easy to use, I know feel confidant enough in my Linux skills to try Debian again.

Just thought I'd tell you my impression.

---

### Post by Tuna on 2007-01-27
> **mips said:**
> Try Sidux which is based on Debian Sid, they just try to stabalise it . Still uses the debian repos.

Is Sid the next release after Etch?  What makes Sidux better than just using Debian Sid?  Only asking because I genuinely don't know.  Thanks for all the information and advice so far, everybody.  :D

Edit: Nevermind, I just found it after a bit of research on the Debian forums.  Though I still would like to know what makes it better than Debian Sid if somebody wouldn't mind giving a short explanation.  To my understanding, Etch will be the stable version very shortly, and Sid will be moved to testing, correct?  From what I understand from this thread, Debian's Testing builds are pretty stable.  Is this correct?  I'm setting aside another partition for trying out other distros.   I may try out MCNLive as well to see what I think of that.  I've almost got the Mandriva Free 2007 DVD finished downloading here, after that I'm starting the download for Sidux as well to burn to a CD.  To further elaborate what I'm looking for, I definitely want free software like Ubuntu has.  I also will be using it on a daily basis so it needs to be relatively stable.  I don't mind messing with stuff and actually enjoy messing with stuff to get it to my liking.  But at the same time, I don't really want something that I'm going to run into bugs with multiple times a day, either.  Also I enjoy that there's such a large community here since I'm not well-versed with actually digging into files without assistance, so I kind of need that too.  Maybe Ubuntu is best for me.  Who knows?   But I'd atleast like to give some others a shot to see if there's something I like better (not that I'm exactly unhappy with Ubuntu or anything, just trying to expand my horizons a bit).

---

### Post by jdhore on 2007-01-27
> **Tuna said:**
> Is Sid the next release after Etch?  What makes Sidux better than just using Debian Sid?  Only asking because I genuinely don't know.  Thanks for all the information and advice so far, everybody.  :D

Edit: Nevermind, I just found it after a bit of research on the Debian forums.  Though I still would like to know what makes it better than Debian Sid if somebody wouldn't mind giving a short explanation.  To my understanding, Etch will be the stable version very shortly, and Sid will be moved to testing, correct?  From what I understand from this thread, Debian's Testing builds are pretty stable.  Is this correct?  I'm setting aside another partition for trying out other distros.   I may try out MCNLive as well to see what I think of that.  I've almost got the Mandriva Free 2007 DVD finished downloading here, after that I'm starting the download for Sidux as well to burn to a CD.  To further elaborate what I'm looking for, I definitely want free software like Ubuntu has.  I also will be using it on a daily basis so it needs to be relatively stable.  I don't mind messing with stuff and actually enjoy messing with stuff to get it to my liking.  But at the same time, I don't really want something that I'm going to run into bugs with multiple times a day, either.  Also I enjoy that there's such a large community here since I'm not well-versed with actually digging into files without assistance, so I kind of need that too.  Maybe Ubuntu is best for me.  Who knows?   But I'd atleast like to give some others a shot to see if there's something I like better (not that I'm exactly unhappy with Ubuntu or anything, just trying to expand my horizons a bit).

OK, the short answer...Sid will never be Testing or Stable...Sid will ALWAYS be the most bleeding-edge Debian packages a.k.a. Unstable, some of the packages from Sid will be moved to testing once they're seen to be more stable

---

### Post by Tuna on 2007-01-27
> **jdhore said:**
> OK, the short answer...Sid will never be Testing or Stable...Sid will ALWAYS be the most bleeding-edge Debian packages a.k.a. Unstable, some of the packages from Sid will be moved to testing once they're seen to be more stable

Ah, so Sidux basically just works to get the Sid packages Stable as quickly as possible?  I guess I'll definitely have to try it then.  (Just finished burning Debian Etchy to CD)

---

### Post by sherlock-holmes on 2007-01-27
i tried everything from various forums to google to get my fglrx working on a fresh debian etch install. 

it still shows mesa...so its still not working ...no hardware acceleration...
btw whats the equivalent of ubuntu linux-restricted-modules for debian. i cant seem to get it from repos...

anyway  i feel ubuntu is much more easier....but debian is not bloated ...i have only 800 packages !... but debian etch is much more responsive than ubuntu...

faster...

---

### Post by tturrisi on 2007-01-27
> **sherlock-holmes said:**
> btw whats the equivalent of ubuntu linux-restricted-modules for debian. i cant seem to get it from repos...
There is none.  Just edit your sources.list to: (or equivilant)

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main non-free contrib 
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main non-free contrib 
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free 
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free

Then download the package you want using apt if it exists in repositories or build-install it yourself.  What "restricted-module" do you need?

---

### Post by jdhore on 2007-01-27
> **Tuna said:**
> Ah, so Sidux basically just works to get the Sid packages Stable as quickly as possible?  I guess I'll definitely have to try it then.  (Just finished burning Debian Etchy to CD)

Well...the Reason Debian is Debian is because they test the HELL out of EVERYTHING before they make it testing or stable so a package in Sid may be perfectly stable, but just not have moved through yet. Sidux (i believe) is basically "snapshots" of new Sid versions. Since Sid packages are ALWAYS being updated

---

### Post by handy on 2007-01-28
You can read all about Sidux on their site:

[_***sidux.com***_]("http://sidux.com")

Basically it is the cutting edge software made stable for those who want to be on the cutting edge...

---

### Post by yigal.weinstein on 2007-01-28
There is nothing stable about the cutting edge.

---

### Post by xabbott on 2007-01-29
> **yigal.weinstein said:**
> There is nothing stable about the cutting edge.
truth. 

I still don't get why you would run sidux instead of sid...

---

### Post by Kindred on 2007-01-29
Is sid even considered cutting edge these days?  I've been waiting on gtk 2.10 for ages, while I was running it on Arch about 6 months ago (and Ubuntu had it in Edgy), plus the whole Gnome 2.16 thing.. (I don't use it but still..). I do like using Debian but it's starting to bother me.

---

### Post by fluffnik on 2007-01-29
> **yigal.weinstein said:**
> There is nothing stable about the cutting edge.

I run Sid most places, it rarely breaks.

Unstable in Debian terms is more about configuration, namespace and packaging issues than how often a given binary might fall over.

Once you've customised the configuration it's very rare for apt to stomp on your config without explicit authority or for significant system level changes to happen without a headsup.

If you quickly scan the changelogs of critical updates before clicking install you're unlikely to get any unpleasant shocks from Sid...

---

### Post by handy on 2007-01-30
> **xabbott said:**
> truth. 

I still don't get why you would run sidux instead of sid...

I don't, I run PC-BSD :KS

---

### Post by yigal.weinstein on 2007-01-30
> **fluffnik said:**
> I run Sid most places, it rarely breaks.

Unstable in Debian terms is more about configuration, namespace and packaging issues than how often a given binary might fall over.

Once you've customised the configuration it's very rare for apt to stomp on your config without explicit authority or for significant system level changes to happen without a headsup.

If you quickly scan the changelogs of critical updates before clicking install you're unlikely to get any unpleasant shocks from Sid...

I agree with you mostly.  I used Sid for more than a year before switching to Ubuntu.
However, when my latex editor an add on of vim, vim-latexsuite, broke in multiple ways, when Yelp Gome's help file system - which is still pretty bad - had some pretty bad bugs of not parsin the xml files correctly, when any number of  problems happened for me in Sid I decided after a while that Ubuntu was and it still is a better bet.

Is unstable Debian really unstable? Of course not but the support available in Ubuntu is hands down better than anything I have experienced in Debian and at least theoretically the Ubuntu team is just another layer of protection for my system so it doesn't have to be broken in more than a few places.  

Is unstable Debian really cutting edge?  Now that's a question.  Consider that while Edgy uses Gnome 2.16 and therefore Evolution 2.8 and Sid is at 2.14 and Evolution 2.6.  The same thing can be said about gtk in Edgy that is why we have pretty handles that change colors when we scroll in Metacity and Debian does not.  So one could easily claim that Ubuntu is the cutting edge of the 2.

---

### Post by glabouni on 2007-01-30
> **AgenT said:**
> Debian is known for stability and also for having many different options. 

debian is also quite infamously known for its realllllyyyyy slooooooooow release cycle. 

let's recap

2002/07/19 debian stable 3.0 codename woody is out
2005/06/06 debian stable 3.1 codename sarge is out
next release will be debian etch, no date fixed and currently in testing

that's almost 3 years between two stable releases, and 18 months since the last release.

on one hand debian is known for its stability and robustness, on the other hand debian is known for its obsolete packages and ease to break while trying to get that required package installed that messed up your dependencies. 

This is why I chose ubuntu over debian in the first place. The fixed 6 month release cycle was appealing to me. Now I'm about to quit using ubuntu for another linux flavour, mainly due to lack of freedom of choice and too many not-working (at all or as intended) stuff.

---

### Post by yigal.weinstein on 2007-01-30
glabouni I would be interested to know 1. what stuff isn't working and 2. what distribution are you moving to?

---

### Post by Kateikyoushi on 2007-01-31
I am also curious, I also have some issues but not major enough to waste time on finding another distro.

---

### Post by handy on 2007-01-31
Ubuntu is wonderful, I will continue to use both Ubuntu & PC-BSD as they are both great.  Shortcomings in Ubuntu are fulfilled in PC-BSD, & the other way around too!

It would be nice if I could have the best of both worlds. :KS

---

### Post by daniel-linux on 2008-03-03
i tend to agree with AgenT and tturrisi, who seem to be advanced users and know what they're saying

i have been using ubuntu for a few years now, and i finally switched to debian (which was perhaps a bit too much to start with)

the paradox is that if you run debian lenny for instance, you will be at the same time more stable (as a system) and more up to date than running an ubuntu distro

that's because lenny is based on etch (the stable version), but every now and then, when new packages are ready from sid, they trickle down into lenny and you can basically update your system weekly to get the latest stable software that's out there

with ubuntu on the other hand, if you go for the LTS release and choose using dapper drake, you will have neither stability (since it's based on sid), nor updated software (you'll be using firefox 1.5 etc., unless you upgrade)

all in all, i think that the package selection management is run in a much more controlled and professional fashion in debian than in ubuntu (which makles me think about how calm, reserved and carefull ian murdock is, in comparison with mark shuttleworth, who is a lot more outgoing, more adventurous - hell, he's been to the moon and back B-) -, more of a spotlight kid/sid, but in a sense maybe a bit more superficial, more of a businessman than a geek etc.

which is not bad by the way, since ubuntu fills the gap between serious gnu/linux distros and the popular desktop OS-s as win xp and mac OS X, so it's a good place to start

but leaving that context aside, there's no question about debian's superiority to any user that needs stability as well as new, good quality, pieces of software

i ran hardy heron alpha 5 the other day, just out of curiosity, and it's a complete MESS

i don't think i've ever seen so many bugs in a gnu/linux distro in my life. by the time i was finishing a bug report for one, i would run into another... it's ridiculous 

i'm pretty sure they won't get the job done until april, but they'll freeze the work and release a new, "stable" version of it anyway :) how crazy is that B-)

anyway, to each its own - as a distro, debian is definitely better, but for promotion of the gnu/linux platform among the dummies that have never used anything but mac or xp in their entire miserable lives (i was one of them :D), it's good work ;)

---

### Post by Junichiromayo on 2008-03-03
> **glabouni said:**
> debian is also quite infamously known for its realllllyyyyy slooooooooow release cycle. 

let's recap

2002/07/19 debian stable 3.0 codename woody is out
2005/06/06 debian stable 3.1 codename sarge is out
next release will be debian etch, no date fixed and currently in testing
Yes, but Etch is released since April 2007

---

### Post by r4ik on 2008-03-03
If you keep it stable Debian will bore you to death.

---

### Post by kerry_s on 2008-03-03
> **r4ik said:**
> If you keep it stable Debian will bore you to death.

:lolflag:
i agree, debian stable is just to stable.

---

### Post by daniel-linux on 2008-03-04
this is a silly argument

if you push it that far and security/stability is no longer a concern for you, 

why not switch back to windoze altogether? ;)

---

### Post by markharding557 on 2008-03-14
> **daniel-linux said:**
> i tend to agree with AgenT and tturrisi, who seem to be advanced users and know what they're saying

i have been using ubuntu for a few years now, and i finally switched to debian (which was perhaps a bit too much to start with)

the paradox is that if you run debian lenny for instance, you will be at the same time more stable (as a system) and more up to date than running an ubuntu distro

that's because lenny is based on etch (the stable version), but every now and then, when new packages are ready from sid, they trickle down into lenny and you can basically update your system weekly to get the latest stable software that's out there

with ubuntu on the other hand, if you go for the LTS release and choose using dapper drake, you will have neither stability (since it's based on sid), nor updated software (you'll be using firefox 1.5 etc., unless you upgrade)

all in all, i think that the package selection management is run in a much more controlled and professional fashion in debian than in ubuntu (which makles me think about how calm, reserved and carefull ian murdock is, in comparison with mark shuttleworth, who is a lot more outgoing, more adventurous - hell, he's been to the moon and back B-) -, more of a spotlight kid/sid, but in a sense maybe a bit more superficial, more of a businessman than a geek etc.

which is not bad by the way, since ubuntu fills the gap between serious gnu/linux distros and the popular desktop OS-s as win xp and mac OS X, so it's a good place to start

but leaving that context aside, there's no question about debian's superiority to any user that needs stability as well as new, good quality, pieces of software

i ran hardy heron alpha 5 the other day, just out of curiosity, and it's a complete MESS

i don't think i've ever seen so many bugs in a gnu/linux distro in my life. by the time i was finishing a bug report for one, i would run into another... it's ridiculous 

i'm pretty sure they won't get the job done until april, but they'll freeze the work and release a new, "stable" version of it anyway :) how crazy is that B-)

anyway, to each its own - as a distro, debian is definitely better, but for promotion of the gnu/linux platform among the dummies that have never used anything but mac or xp in their entire miserable lives (i was one of them :D), it's good work ;)
lenny is not based on debian stable it is much closer to sid and is way newer than etch in fact if you tried to put a lenny package into etch it probably would not work 
etch is over a year older than lenny.
you need to get your fact right

---

### Post by daniel-linux on 2008-03-15
> **markharding557 said:**
> lenny is not based on debian stable it is much closer to sid and is way newer than etch in fact if you tried to put a lenny package into etch it probably would not work 
etch is over a year older than lenny.
you need to get your fact right

there you go, wise *** ;)

"The code name for the next major Debian release after etch is lenny.
This release started as a copy of etch, and is currently in a state called testing. That means that things should not break as badly as in unstable or experimental distributions, because packages are allowed to enter this distribution only after a certain period of time has passed, and when they don't have any release-critical bugs filed against them."

[http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/)

end of conversation

---

### Post by markharding557 on 2008-03-15
that means lenny started its development cycle from as a copy of etch,as time moves on it moves ever further away from etch and as such is not based on etch.
as i said all its new code comes down from sid so it could be argued that lenny is based on code from sid

---

### Post by dptxp on 2008-03-16
> **markharding557 said:**
> that means lenny started its development cycle from as a copy of etch,as time moves on it moves ever further away from etch and as such is not based on etch.
as i said all its new code comes down from sid so it could be argued that lenny is based on code from sid

You should accept your mistake and learn, not try to justify the wrong information this way.:popcorn:

---

### Post by kellemes on 2008-03-16
Old thread.. ;-)
Anyway, to respond to OP. For me Debian is precisely what I need, it gives me the base I need to build my system on. Debian (whatever branch) doesn't try to pretend to be anything, it just is.. you (the end user) has to mold the system as wished.
I can use it for servers and expect it to be very trustworthy, or I can have it to be the bleeding-edge desktop like Ubuntu tries to be.
For my desktop I get most packages from Lenny and only individual packages from Sid. This makes my system very very stable and  secure (for a Desktop-system anyway), I cannot remember having to reboot because of problems. Still, those standard packages I use are very much bleeding edge, even more so as Gutsy has to offer.

---

### Post by daniel-linux on 2008-03-17
> **markharding557 said:**
> that means lenny started its development cycle from as a copy of etch,as time moves on it moves ever further away from etch and as such is not based on etch.
as i said all its new code comes down from sid so it could be argued that lenny is based on code from sid

FYI:

"The stable distribution is currently etch; The next stable distribution will be called as lenny.
Let&#8217;s consider the particular case as to what happens when lenny is released as the new stable
version.
   &#8226; oldstable = sarge; stable = etch; testing = lenny; unstable = sid
   &#8226; Unstable is always referred to as sid irrespective of whether a release is made or not.
   &#8226; packages constantly migrate from sid to testing (i.e. lenny). But packages in stable (i.e.
      etch) remain the same except for security updates.
   &#8226; after sometime testing becomes frozen. But it will still be called testing. At this point
      no new packages from unstable can migrate to testing unless they include release-critical
      (RC) bug fixes.
   &#8226; When testing is frozen, all the new bugfixes introduced, have to be manualy checked by
      the members of the release team. This is done to ensure that there wont be any unknown
      severe problems in the frozen testing.
   &#8226; RC bugs in &#8217;frozen testing&#8217; are reduced to zero.
   &#8226; The &#8217;frozen testing&#8217; with no rc-bugs will be released as the new stable version. In our
      example, this new stable release will be called as lenny.
   &#8226; At this stage oldstable = etch, stable = lenny. The contents of stable and &#8217;frozen testing&#8217;
      are same at this point.
   &#8226; **A new testing is forked from the current stable.**
   &#8226; Packages start coming down from sid to testing and the Debian community will be working towards making the next stable release."

[http://www.debian.org/doc/user-manuals#faq](http://www.debian.org/doc/user-manuals#faq)

Do your homework mate, then you can argue about it as much as you please ;)

---

### Post by markharding557 on 2008-03-17
> as i said all its new code comes down from sid so it could be argued that lenny is based on code from sid
[QUOTE]&#8226; A new testing is forked from the current stable.
&#8226; Packages start coming down from sid to testing and the Debian community will be working towards making the next stable release."[/QUOTE]
you just confirmed what i was saying when i said testing code come from sid not stable.
and don't tell me when i can and can not argue,i can argue when i like

---

### Post by deepclutch on 2008-03-18
Sid not stable?well I am running Debian Sid apt-pinned with testing and experimental(for upstart) for more than a year or so.only once in a while will I have to do this "dpkg --force-depends/force-overwrite -i xs.deb" .
Only buggy thing I found in Debian Sid "was" gnome-system-tools and system-tools-backends.as of now,both are fixed.

also,Debian Gnome is clean,faster than Ubuntu.
Debian FTW! :D

---

### Post by daniel-linux on 2008-03-19
> **markharding557 said:**
> you just confirmed what i was saying when i said testing code come from sid not stable.
and don't tell me when i can and can not argue,i can argue when i like

you just don't get it, do you :)

testing is BASED on stable, THEN packages start trickling down  into it from unstable 

but they will only get into testing when they have met certain criteria, and more so when they reach stable - at which point they have undergone serious changes as far as bug fixes go and so forth, so they cannot be called "sid" anymore 

as per quoted debian-faq:

"Packages are installed into the &#8216;testing&#8217; directory after they have undergone some degree of
testing in unstable.
They must be in sync on all architectures where they have been built and mustn&#8217;t have depen-
dencies that make them uninstallable; they also have to have fewer release-critical bugs than
the versions currently in testing. This way, we hope that &#8216;testing&#8217; is always close to being a
release candidate."

and 

"The &#8216;unstable&#8217; directory contains a snapshot of the current development system. Users are
welcome to use and test these packages, but are warned about their state of readiness. The
advantage of using the unstable distribution is that you are always up-to-date with the latest
in GNU/Linux software industry, but if it breaks: you get to keep both parts :-)"

yes, you can argue when you like, but that only proves that your whimsical statements are nothing but dust in the wind

---

### Post by markharding557 on 2008-03-19
i am not going argue about this any more,iv,e got more important things to do than argue with someone who is so experienced in linux that that he couldn't until very recently edit a menu.
also noted four of your seven posts are arguing with me ,don't you have anything better to do?,this is a help forum,so reply if you like i will not be

---

### Post by p_quarles on 2008-03-19
*Very* old thread closed. 

In any case, the argument here is just splitting hairs. Yes, Testing is initially based on Stable, but people use Testing for the new packages, not the old ones.

---

