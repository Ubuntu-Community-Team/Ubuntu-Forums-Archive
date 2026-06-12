---
title: "Debian vs ubuntu"
date: 2008-12-28
forum: Debian
---

### Post by retskrad on 2008-12-28
I heard Ubuntu is like Debian, but more userfriendly?

I also heard debian is alot better than ubuntu, but takes alot more time to understand?

[Offtopic]
And also, I don't get why people makes multipl OS's, Defora, debian, opensuse, they are all very much alike. Can't they all come toether and fefeat microsoft and mac?

---

### Post by icyest on 2008-12-28
[@Offtopic]
Yes they can, but that's not the way human market networks work for the open source. We like to divide into little tribes.
Think of it this way; Linux is like the American Indian tribes, scattered and unique in variation of culture/customs, and Micro$oft is like the British, while France is Apple.

Ubuntu actually has a community so you can learn. Ubuntu's community (forum) is the strongest of the Linuxs'. I would use Debian unless you have friends nearby who can learn Debian together. (unless you have a B.S. Computer Science)

---

### Post by retskrad on 2008-12-28
So, ubuntu was made from debian? So debian is alot better, but alot harder to learn and very bad community?

---

### Post by oldsoundguy on 2008-12-28
Ubuntu (and it's spin offs) are based on Debian.  But it is more GUI oriented and with both package manager (syanptic) and add/remove programs, you will spend a lot less time cutting and pasting or writing in terminal.  It is just easier to use.  but with ease comes limitations.  your choice. 
There is one Ubuntu (Linux Mint) that, unless you want to change a default program to another one,  you do not even have to use synaptic or add/remove! .. it just loads and runs.  BUT not as may bells and whistles. 

Personally, I am a computer USER and the idea of spending endless hours tweaking the system to get it ABSOLUTELY PERFECT has no appeal to me. Perfection is too fleeting!

Defeating one of the purposes of the system .. that of not having to constantly screw with it as you have to do in Windows with it's swiss cheese security and the need to spend 4 hours + every week maintaining it.

---

### Post by retskrad on 2008-12-29
I trie debian and its way harder than ubuntu to setup and confugure

---

### Post by ajcham on 2008-12-29
> **retskrad said:**
> [Offtopic]
And also, I don't get why people makes multipl OS's, Defora, debian, opensuse, they are all very much alike. Can't they all come toether and fefeat microsoft and mac?

Each project has it's own goals, development styles and philosophies.  They all consist of different bunches of people who have different ideas of what they want in an OS, and it's better this way.  If we tried to get the developers of Gentoo, Debian and Red Hat to all work together on a single project all we'd have would be endless flame wars and no work would ever get done. And 'defeating Microsoft' is low down on the priority list for most devs - it's not about making the biggest and best OS for everyone - it's about making the best OS *for themselves*.

---

### Post by retskrad on 2008-12-29
I dont believe none of them will be the starndard OS, like SO or mac. ubuntu is kinda close, being very suer friendly. Although it ahs many years to come. Debian, in my opinion, will never reach a standard OS.

---

### Post by ibuclaw on 2008-12-29
Debian may not be the standard to GUI orientated Desktop, but it is one of the most standardised Operating Systems for Linux, nonetheless.

For example, I would rather not setup any server with anything else but Debian, as I can completely rely on it to run, to stay running, and to not break on me after some security or software upgrades...

Regards
Iain

---

### Post by retskrad on 2008-12-29
do you use debian? how isit?

---

### Post by ibuclaw on 2008-12-29
Ubuntu makes alot of seemingly simple tasks very transparent to the user. So all you have to worry about is, perhaps, the speed of their/your internet connection when pulling down updates. ;)

With Debian, you are given a bare bones operating system that's sole job is to boot successfully, and you must build it up yourself to be what you want it to be. Although you are given about a dozen options at installation time as to what you want installed for you before the first boot:
ie:
Desktop Environment
Mail Server
File Server
DNS Server
DHCP Server
etc...

As you can probably see from what I can remember, it is very server orientated. But, then again, so is all of Linux.

But, back to the point, if you want the nice subtle things that Ubuntu gives you, you are required to setup all the work yourself, such as nvidia drivers, xorg.conf files, etc... But that does not mean that it is certainly any harder to setup.
Thanks to Ubuntu, there are more than an abundance of HowTOs that will work just as well in Debian. [Here is a how to automatically compile manually installed NVIDIA drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573"), as written by a friend.

I have also mentioned stable... to which Debian is one of the most stable operating systems I have ever used. With the exception of the first time I used manually installed nvidia drivers, but it was an elementary mistake, and you learn to evade it. (see link above) :)

But, where stability is a high priority, you may find that some of the more exotic applications are not available through the standard repositories, and you'll have to search and find external repositories to suit your needs. Such include: [http://debian-multimedia.org/](http://debian-multimedia.org/)

I also found Debian to be a very good developing platform, and using it certainly helped me understand software better, and gave a deeper understanding to how an operating system works internally (though, it is not solely down to just using Debian, but other OS's such as Gentoo, Archlinux, and FreeBSD also).

But, in my full honest opinion, if you are looking for something that uses the best between stability and freely available software, I would recommend Ubuntu Hardy 8.04.1 ... It, to me, is the most beautifully thought out modern operating system of today, but you can still backport things from intrepid, if you wish to have the newest software available.
Here is my complete list of external sources for Hardy in a Nutshell:
```

## Kiwilinux (Ubuntu 8.04 - Hardy Heron compatible)
deb http://kiwilinux.org/archive hardy main
deb-src http://kiwilinux.org/archive hardy main
## Lightweight X Desktop Environment
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
## Medibuntu - Ubuntu 8.04 "Hardy Heron"
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
## WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main
## Opera
deb http://deb.opera.com/opera/ lenny non-free
## PlayOnLinux
deb http://deb.mulx.net/ hardy main
## Google
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
## Nautilus DropBox
deb http://www.getdropbox.com/static/ubuntu hardy main
## XBMC
deb http://ppa.launchpad.net/team-xbmc/ubuntu hardy main
## Galaxium
deb http://ppa.launchpad.net/galaxium/ubuntu hardy main
## VLC and other new Audio Libs
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main
## Ubuntu-Tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
## Open-Office 3.0 for Hardy
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
## General Assortment / Other
deb http://ppa.launchpad.net/misery/ubuntu hardy main
deb-src http://ppa.launchpad.net/misery/ubuntu hardy main
## VirtualBox
deb http://download.virtualbox.org/virtualbox/debian hardy non-free

```

But, if you wish to give Debian a go. Check out the bottom link in my Sig.
The Linux Professional Institute Manuals, they give a very good walkthrough of how Linux works internally, and, to me, have been a very valuable source of information for passing the LPI1 exams, and working towards LPI2 Certification.

Regards
Iain

---

### Post by bryonak on 2008-12-29
Just to add a bit of noise...

Debian has been started in 1992/1993 and is probably the biggest open source project ever (more than 1000 regular developers). Meanwhile it has become very sophisticated and efficient, it runs on about 15 different architectures (your computer, cell phone, router, GPS system, toaster, ...).
It's main focus is stability (leading to security and reliability).
Most of the internet is run on Linux, a very big part of which consists of Debian. Also of the 500 fastest supercomputers in the world, more than the half runs Debian.
The reasons are it's stability, reliability, security, efficiency and so on.

2004: Canonical takes the Debian codebase and starts to work on Ubuntu. Why?
Because Debian for all it's glory lacks one thing: user friendliness. It is focused on technical stuff, not nice menus and fancy effects.
The reason why Ubuntu is so popular is because it allows non-technical users to enjoy the system.
The reason why Ubuntu has sailed past other "user friendly" distros like Mandriva, FedoraCore or Suse is (among others) because it has an excellent codebase: that of Debian.

Debian is not "better" than Ubuntu, nor the other way around. They are more than 90% identical.
It's just the application area that differs: if you want a desktop/laptop, Ubuntu will be much easier to install and use.
If you want a server, all the graphical fluffy things will be useless bloat, so you're better off with Debian.

I won't go much into the Ubuntu server edition, which exists mainly because Canonical feels like a respectable Linux corporation has to have a server edition. Apart from a few differences (startup process, root account, ...) and rebranding it's equal to Debian.

---

### Post by retskrad on 2008-12-29
I just tried Debian and my first impression was, the old linux style, not very userfriendly, I hate the menus, It just didint give me easyness of Ubuntu..

---

### Post by 2hot6ft2 on 2008-12-29
I think this explains everything very nicely. [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by ibuclaw on 2008-12-29
> **2hot6ft2 said:**
> I think this explains everything very nicely. [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

I don't think that explains anything at all to do with the difference between Debian and Ubuntu.

Now, don't take this personally, but a few years ago when I started out on Linux, the only distribution I would use was Debian, why? Because it was the only distribution that **just worked**, for me, the Linux New-Bee.

I had on the odd occasion been attracted to Ubuntu Dapper, Feisty, then Gutsy... but for one reason or another, maybe because of their "bleeding edge-ness" at the current time was more important than stability, or maybe it was because of my [motherboard was originally a foxconn]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249") before I replaced it with an AMiTrends. Who knows?
But truth of the matter is, as long as it worked with the hardware I was using, I stuck with it... and Debian Etch was the only Operating System that worked with my hardware without freezing/crashing after the first 5 minutes, and the rest just flowed.

I'm sure I'd said this before, but user-friendliness, to me, is all about hardware compatibility. As long as all the hardware works, I couldn't care less about the desktop environment. Since you can either accept it, or reject it... learn how it works, or exclaim that everything is never where you want it to be.

Software will always require training and a little bit (or a huge amount) of adjustment.
Hardware, on the other hand, should never be an issue to the end-user, and it's workings should be transparent.

It took me a good 6 months to master how to build a usable Desktop in Debian from a bare-bones netinstall in less than 40 minutes after the first boot-up into the console login-screen. But, truth is, I put my thinking cap on, I stuck to it, and I felt that I learned something adventurous in the end.
When Ubuntu Hardy Alpha 1 came round in January 2008, it seemed like a natural transition, and I suppose, I've been using Hardy ever since. (And probably will do for the next few years).

And as for Debian looking like "Linux Old-Style"...
Check out my debian-laptop: [http://usera.imagecave.com/tinivole/Screenshot.png](http://usera.imagecave.com/tinivole/Screenshot.png)

Regards
Iain

---

### Post by nitehawk777 on 2008-12-29
@tinivole,....
(maybe I should start a new thread on this?)..
But I REALLY would like to use pure Debian too,..but I have just a slow dialup service.  Would the DVD or CD sets have all the apps I need (without hours of downloading?) I tried the one install CD,..and it was pretty incomplete,....
I have somewhat of that problem with Ubuntu, also (have to spend about 3 hours to download the codecs).  With Linux Mint,..all the downloading time is spent with stuff like wine,..etc. etc.

So,...pure Debian is,...or isn't a good idea with dialup?:confused:

---

### Post by retskrad on 2008-12-29
> **tinivole said:**
> I don't think that explains anything at all to do with the difference between Debian and Ubuntu.

Now, don't take this personally, but a few years ago when I started out on Linux, the only distribution I would use was Debian, why? Because it was the only distribution that **just worked**, for me, the Linux New-Bee.

I had on the odd occasion been attracted to Ubuntu Dapper, Feisty, then Gutsy... but for one reason or another, maybe because of their "bleeding edge-ness" at the current time was more important than stability, or maybe it was because of my [motherboard was originally a foxconn]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249") before I replaced it with an AMiTrends. Who knows?
But truth of the matter is, as long as it worked with the hardware I was using, I stuck with it... and Debian Etch was the only Operating System that worked with my hardware without freezing/crashing after the first 5 minutes, and the rest just flowed.

I'm sure I'd said this before, but user-friendliness, to me, is all about hardware compatibility. As long as all the hardware works, I couldn't care less about the desktop environment. Since you can either accept it, or reject it... learn how it works, or exclaim that everything is never where you want it to be.

Software will always require training and a little bit (or a huge amount) of adjustment.
Hardware, on the other hand, should never be an issue to the end-user, and it's workings should be transparent.

It took me a good 6 months to master how to build a usable Desktop in Debian from a bare-bones netinstall in less than 40 minutes after the first boot-up into the console login-screen. But, truth is, I put my thinking cap on, I stuck to it, and I felt that I learned something adventurous in the end.
When Ubuntu Hardy Alpha 1 came round in January 2008, it seemed like a natural transition, and I suppose, I've been using Hardy ever since. (And probably will do for the next few years).

And as for Debian looking like "Linux Old-Style"...
Check out my debian-laptop: [http://usera.imagecave.com/tinivole/Screenshot.png](http://usera.imagecave.com/tinivole/Screenshot.png)

Regards
Iain

Well, I didnt mean the coloures and all that, I mean before, when linux was  windows classic, it was not very userfriendly, thats how I see debai, buts its stable and very good.

---

### Post by oldsoundguy on 2008-12-29
this has been glossed over in previous posts, but it needs to be clarified.

As the Linux is NOT Windows link so well points out,
Linux started as a system for geeks to play with geeks.  It was nearly impossible to get help on any of the early systems simply because of that attitude at the supposed help sites.
I began with Mandrake 3 and continued on through all kinds of builds and iterations of builds .. and NEVER was able to actually USE a Linux system as a day to day .. leave it on my desktop and do everything but play games and run Adobe programs system UNTIL, two years ago, a very good friend said the magic word: Ubuntu!
I installed it and in a very short time was able to turn my Windows computers into just what they deserve to be .. game boxes (although I do not game) and a device to run Adobe for my photography .. and as a giant catch all/processor for my A/V files.
EVERYTHING else .. business, word processing, on line activities, research, eBay auctions .. you name it is all done on Linux now.
PART of the reason for the ability to change over can be laid at the feet of these forums .. no more snooty attitude that you just are stupid for asking a question and do not deserve a real answer.
I have nothing against tinkering .. I do it .. but it should not be needed to get up and running with a basic OS and some basic programs.
Linux Mint proved to be the easiest system to install and use out of the box (it is Ubuntu based) .. 
but I do prefer Ubuntu itself as it does offer that flexibility for a USER as well as someone that likes to experiment. 
I have one machine set up just to test drive the various items in the repositories to see IF I want to install them on the main computer .. that box goes through a LOT of changes .. and with the exception of a conflict between NoScript in Firefox and the eBay chat room sign on that crashed things(eBay changed the location of member verification on the rooms) (that got fixed yesterday .. I helped out on the testing and ver 1.8.8.4 from the site does it now) .. the box has never crashed with anything loaded from the repositories .. some real "what the heck would I want to use this for?" items in there .. but some gems also!!

So yes, Ubuntu (or it's variants) if you really want to USE your computer and not spend a lot of time delving into the innards of it.

---

### Post by tuxxy on 2008-12-29
> **icyest said:**
> [@Offtopic]
Yes they can, but that's not the way human market networks work for the open source. We like to divide into little tribes.
Think of it this way; Linux is like the American Indian tribes, scattered and unique in variation of culture/customs, and Micro$oft is like the British, while France is Apple.


I prefer European countries as Linux distributions and Microsoft as America :o

---

### Post by nitehawk777 on 2008-12-29
@oldsoundguy....
You may have cleared up my confusion.  I'm still fairly new to linux,...(less than a year) so still trying to find the "right" distro (as if there is such a thing).  However,...with slightly older computers and dialup,...I just want my OS to WORK!!!  So Ubuntu (and it's varients) are perhaps the best choice for my situation and needs.:)

---

### Post by polmir on 2009-01-01
By selecting Ubuntu have everything installed and even programs, which will never enjoy.

By choosing Debian installing only what you need is.

The best way to start the adventure with Debian using the minimum CD:
[daily-builds i386 iso-cd]("http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/")

Debian is not difficult.
It has a wealth of documentation:
[User-manuals.en.html]("http://www.debian.org/doc/user-manuals.en.html")
[Debian Reference.en.pdf]("http://www.debian.org/doc/manuals/reference/reference.en.pdf")

---

### Post by mikjp on 2009-01-02
> **oldsoundguy said:**
> Ubuntu (and it's spin offs) are based on Debian.  But it is more GUI oriented and with both package manager (syanptic) and add/remove programs, you will spend a lot less time cutting and pasting or writing in terminal.

Well, Debian is not that much more terminal oriented nowadays. It even has a live CD installer with GUI. And also Debian has synaptic.

Most of the usual reasons for using Ubuntu instead of Debian are only FUD :-)

---

### Post by RedSquirrel on 2009-01-02
> **polmir said:**
> By selecting Ubuntu have everything installed and even programs, which will never enjoy.

That's true if you install the full ubuntu-desktop. If you install an Ubuntu command-line system, you can add whatever you want.



> **polmir said:**
>  The best way to start the adventure with Debian using the minimum CD:
[daily-builds i386 iso-cd]("http://cdimage.debian.org/cdimage/daily-builds/daily/current/i386/iso-cd/")

Ubuntu has a minimal CD [here]("https://help.ubuntu.com/community/Installation/MinimalCD").

---

### Post by malspa on 2009-01-02
> **nitehawk777 said:**
> @tinivole,....
(maybe I should start a new thread on this?)..
But I REALLY would like to use pure Debian too,..but I have just a slow dialup service.  Would the DVD or CD sets have all the apps I need (without hours of downloading?) I tried the one install CD,..and it was pretty incomplete,....
I have somewhat of that problem with Ubuntu, also (have to spend about 3 hours to download the codecs).  With Linux Mint,..all the downloading time is spent with stuff like wine,..etc. etc.

So,...pure Debian is,...or isn't a good idea with dialup?:confused:

I use dial-up.  I installed Debian using a CD set.  I don't know if it would include ALL the apps you need, but I thought it was a good way to go.  The CD set saved me a lot of time.

Debian isn't as simple an installation as Mint or even Ubuntu, but it isn't all that difficult.  Nice system once you get everything installed and configured.  The whole thing was easier than I expected it to be and I wished that I hadn't waited so long to try it.

---

### Post by polmir on 2009-01-02
**RedSquirrel**, do you tried to install a minimum version of Ubuntu and Debian?

Compare them?


Edit:
After instillation:```
dpkg -l > list.txt
```

---

### Post by nitehawk777 on 2009-01-02
I thought maybe I was the last person in the universe to still be on dialup!!!  Glad to hear of someone else using the land lines that has tried Debian.  I just might try it after all,...(if you say you've done it).:)

---

### Post by malspa on 2009-01-02
> **nitehawk777 said:**
> I thought maybe I was the last person in the universe to still be on dialup!!!  Glad to hear of someone else using the land lines that has tried Debian.  I just might try it after all,...(if you say you've done it).:)

Yes, I installed Debian Etch just over one year ago with a 5-CD set. I installed the KDE version.  I had to do a couple of things to get kppp to work so that I could dial out; it wasn't set up ready-to-go, I had to add the user to the "dip" group and had to create the file /etc/resolv.conf.  I think that was about it for kppp.

Having the CDs available was really nice; when Debian Lenny becomes "Stable" I will go the same route to get it installed.

---

### Post by nitehawk777 on 2009-01-02
Well,..I've been with linux just about a year now,..
but I'm getting familiar with things pertaining to dialout.  So I think I can do the configuring things.  I could dialout with just that one install CD of Debian  (it was just tooooo incomplete)!
So I just now ordered a set of DVDs from FrozenTech. (Got a nicer P4 computer for Christmas, with a DVD reader on it):D

I can configure my way around in and out of KDE (and KPPP)...so here goes an adventure,......

---

### Post by malspa on 2009-01-02
Good luck, nitehawk.  I was afraid to try it, but like I said, I ended up wishing I hadn't waited so long.  I thought it was gonna be a major project.  It wasn't.

---

### Post by RedSquirrel on 2009-01-02
> **polmir said:**
> **RedSquirrel**, do you tried to install a minimum version of Ubuntu and Debian?

Compare them?


Edit:
After instillation:```
dpkg -l > list.txt
```

I have installed minimal versions of Ubuntu and Debian several times, but I haven't compared them in the manner you suggest (well, not recently anyway :D).

I would be interested in seeing the lists if you can produce them (or at least a list of the additional packages that Ubuntu would install). I would do it myself, but I've just settled back into Gentoo after several days of distro-hopping. ;)

I believe Ubuntu is a bit heavier than Debian and may have a few more services started, but I would be interested in the specifics if you have easy access to the information. Thanks.

---

### Post by polmir on 2009-01-02
Another way to compare distribution after installation:```
lsmod
```
I do not have wifi card in my computer. Ubuntu always install the modules that support wifi card.

---

### Post by hyperyoda on 2009-01-18
I run Ubuntu on my desktop and Debian lenny on my server. I agree Debian is a very stable choice for a server OS especially if it is a stable or testing release. Another good stable server OS is CentOS (based on RHEL).

Zach

---

### Post by markharding557 on 2009-01-23
debian lenny is nearly as user freindly as ubuntu.
there should be no debian v ubuntu because they are like parent and offspring ubuntu has debian dna through and through.
i am a fan of both because without debian ubuntu could not be what it is today and some ubuntu patches and things find their way back upstream too.
i see debian as a diamond and the ubuntu developers as skilled polishers who cut and polish that diamond into what their audience expects

---

### Post by gjoellee on 2009-01-23
You gain greater flexibility with Debian, but it is slightly harder to use...

---

### Post by Frak on 2009-01-24
Debian is aimed at more technical users. It's not in the least difficult to use. Back in the day, Debian was one of the easiest OS's to use, next to RedHat, Slackware, Caldera, and S.u.S.E (which was just a Slackware spin-off at the time). You didn't need to worry about dependency checks, which for the time was a major feature, for which Slackware still doesn't have (though, that's his own choice, nobody else's).

Today, most beginning users would rather use Ubuntu for its sheer transparency of all the maintenance work.

---

