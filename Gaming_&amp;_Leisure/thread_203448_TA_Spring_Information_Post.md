---
title: "TA Spring Information Post"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by ELD on 2006-06-25
Please remember:: You need 3D drivers for your graphics card to play.

**What is Spring?**
Spring is an Open Source and highly customizable 3D Real Time Strategy Engine (RTS). The engine is called Spring but it has many mods (remakes of total annihilation) and games (non TA ip, original works) for it each with there own style of play. You can also take a unit in FPS mode! This game is a must for RTS lovers on Linux!
It is constantly updated to make it better, latest release as of this post made on "2009-05-29".

*Screen Shots & Videos*: [http://springrts.com/media.php]("http://taspring.clan-sy.com/screenshots.php")
(also attached to bottom of this post are screenshots)

**Getting Spring:**

 Press alt-F2 to run a command.  Enter: 
```

 gksudo gedit /etc/apt/sources.list.d/springproject.list

```Copy and paste the following into the file: 
Ubuntu 9.04: 
```

deb http://ppa.launchpad.net/spring/ubuntu jaunty main
deb-src http://ppa.launchpad.net/spring/ubuntu jaunty main[FONT=Verdana]
[/FONT]
```Ubuntu 8.10:
```

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main

```Ubuntu 8.04: 
```

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) hardy main

```Public key link:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xFC66403D8670A035)
[B] 
And to install it:

[/B]```

sudo apt-get update
sudo apt-get install spring spring-maps-default

```You will then need to get a game or a total annihilation style mod to actually play a game (see 3 below).

Downloading a lobby is no longer needed it comes with one called "Spring Lobby".

**Playing with spring:**

"Applications - Games - SpringLobby" From the menu.
[B]
Multiple data directories[/B] (where you store mods, maps etc)
> if you use spring on windows & on linux, theres no need to do dull symlinking anymore to get the windows data automatically recognized on Linux, but you can just add e.g. '/windows/Program Files/TASpring' to the end of the list of data directories and you automatically have all maps & mods you play on Windows on Linux too[http://springrts.com/phpbb/viewtopic.php?t=6497](http://springrts.com/phpbb/viewtopic.php?t=6497)

**Playing Spring Guide**
[http://springrts.com/wiki/Using_Spring]("http://taspring.clan-sy.com/wiki/Using_Spring")

**Games Packs/Mods**
[http://springrts.com/wiki/Games](http://springrts.com/wiki/Games)

**Reporting Bugs**
*Please use this post to report bugs in the Spring game itself. Note: Only for the spring engine, not for the lobby you use.*
[http://springrts.com/mantis/main_page.php]("http://taspring.clan-sy.com/mantis/main_page.php")

*Please if you have information reply and i will add it here. Hopefully in time this will be a great guide.*

---

### Post by keithjr on 2006-06-25
Hi, I followed the directions in Getting TA Spring, and the game installs and starts up correctly, but as soon as the map appears the game freezes up and I have to close out the console from which it was opened in order to get rid of it.  No debug info shows up.  Any idea?

Also, the "Original Post" thread you posted is 8 pages long... where exactly should we be looking therein?

---

### Post by ELD on 2006-06-25
The original post is only just for show really or for people who really wanna keep up with what is going on.

It usually freezes for me for a little bit too, just wait it out, it should work.

---

### Post by Oblong_Cheese on 2006-06-25
```

owen@oblong:~$ sudo apt-get install spring spring-basedata
Reading package lists... Done
Building dependency tree... Done
Package spring is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package spring has no installation candidate

```

:confused: It's not there?

---

### Post by keithjr on 2006-06-25
[QUOTE=ELD]The original post is only just for show really or for people who really wanna keep up with what is going on.

It usually freezes for me for a little bit too, just wait it out, it should work.[/QUOTE]


AH!  How right you are.  The first load seems to need about 30 seconds wait after the game start, but will come up, and subsequent loads are faster.

I assumed this post would become a bit of a guide or how-to.  I'm sorry if I was mistaken.

Oblong, did you add the necessary repos to your souces.list?

---

### Post by keithjr on 2006-06-25
Ok, well for the information side, I suggest you edit-in this link in the front post, as it is very helpful for first-timers not familiar with the new controls in Spring, as well as the new features.

[http://taspring.clan-sy.com/wiki/Using_Spring](http://taspring.clan-sy.com/wiki/Using_Spring)

---

### Post by Oblong_Cheese on 2006-06-25
[QUOTE=keithjr]Oblong, did you add the necessary repos to your souces.list?[/QUOTE]

```

owen@oblong:~$ tail -n 1 /etc/apt/sources.list
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

```

And I apt-get updated before I tried to install it.

---

### Post by The Noble on 2006-06-25
Thanks for pushing for this, I have been looking forwards to this for a while. I am downloading the game from the repositories as I type this. :)

The only problem is that I can't dowload the bots for the game, due to unmet dependencies. The Message is:

spring-ai-aai:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

Any way around this besides compiling those?

Edit: Wow, I just went down the list on the mods capable for downloads, This is very complete work. Goodbye to 2 gig on my harddrive if this works. :P

---

### Post by ELD on 2006-06-26
I will update the post soon with more info.

[QUOTE=The Noble]Thanks for pushing for this, I have been looking forwards to this for a while. I am downloading the game from the repositories as I type this. :)

The only problem is that I can't dowload the bots for the game, due to unmet dependencies. The Message is:

spring-ai-aai:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed

Any way around this besides compiling those?

Edit: Wow, I just went down the list on the mods capable for downloads, This is very complete work. Goodbye to 2 gig on my harddrive if this works. :P[/QUOTE]

There is already the best AI (NTAI) that comes with spring :), so ai-aai is really not needed :).
I sent a message to FBO about the bot downloading of ai-aai and it will be fixed tomorrow.

---

### Post by keithjr on 2006-06-26
I have another idea for a link...there's a [wiki ]("http://taspring.clan-sy.com/wiki/XTA")page for it but this link is a bit more helpful:

[http://www.clan-sy.com/download/xta/](http://www.clan-sy.com/download/xta/)

It explains the default mod built by the same clan that now developes the spring project.  It (and aesthetic variants of it) come standard with Spring.  It involves a key series of balance changes.  People who have played O(riginal)TA a great deal NEED to read up on these, as their strategies and tactics both much flex when considering them.  When first downloading spring, it isn't really made clear that there are drastic balance changes.

---

### Post by ELD on 2006-06-26
[QUOTE=keithjr]I have another idea for a link...there's a [wiki ]("http://taspring.clan-sy.com/wiki/XTA")page for it but this link is a bit more helpful:

[http://www.clan-sy.com/download/xta/](http://www.clan-sy.com/download/xta/)

It explains the default mod built by the same clan that now developes the spring project.  It (and aesthetic variants of it) come standard with Spring.  It involves a key series of balance changes.  People who have played O(riginal)TA a great deal NEED to read up on these, as their strategies and tactics both much flex when considering them.  When first downloading spring, it isn't really made clear that there are drastic balance changes.[/QUOTE]

That information is actually very out of date and isn't very much use as that is a guide for an old TA version, where as the engine and changes are different in Spring.

---

### Post by ELD on 2006-06-30
There have been a few updates to Linux Spring now and FBO has started an integrated download system for maps and mods into the spring-setup package :D

And also there is now a lot of work done on a Java Lobby:
[http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5715&start=0](http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5715&start=0)

---

### Post by keithjr on 2006-06-30
Indeed there have been very very many changes!  I just started up spring-setup and found dozens of new maps and mods available!  The linux support is getting better and better...

Where is a good place to find the default balance changes, if the xta site is out of date?  Some of the changes are quite dramatic.

---

### Post by ELD on 2006-06-30
For the defualt mod you can see units stats and such here:
[http://taspring.clan-sy.com/warcows/XTAv6/](http://taspring.clan-sy.com/warcows/XTAv6/)

Although i have been told that this site:
[http://www.clan-sy.com/download/xta/](http://www.clan-sy.com/download/xta/)
Is the only info for balances and such....really needs updating though..

---

### Post by HAARP on 2006-07-01
Best way to find information about this are the Spring forums. But 90% of the community plays AA anyway, so XTA isn't that important

btw. That is funny. I played Spring on Windoze before and changed to Ubuntu only to see the Linux port becoming better and better. Just in time :)

---

### Post by ELD on 2006-07-02
[QUOTE=HAARP]Best way to find information about this are the Spring forums. But 90% of the community plays AA anyway, so XTA isn't that important

btw. That is funny. I played Spring on Windoze before and changed to Ubuntu only to see the Linux port becoming better and better. Just in time :)[/QUOTE]

Spring is one of the reasons i use windows along with msn messenger, as messenger is just so much better than others i have tried :P

But hey spring is getting real good for linux.

---

### Post by ELD on 2006-07-04
Thanks to more nudging from me the TA Spring people have now even opened a Linux forum for us :D

Enjoy: [http://taspring.clan-sy.com/phpbb/viewforum.php?f=20&sid=c9f08e1e9a7318e3d2fe2494d782ed1b](http://taspring.clan-sy.com/phpbb/viewforum.php?f=20&sid=c9f08e1e9a7318e3d2fe2494d782ed1b)

I encourage all gamers to try Spring and post in the forum :)

---

### Post by keithjr on 2006-07-05
the 9 pages of posts on the dep-spring thread might have had something to do with that :)

---

### Post by keithjr on 2006-07-05
[QUOTE=Oblong_Cheese]```

owen@oblong:~$ sudo apt-get install spring spring-basedata
Reading package lists... Done
Building dependency tree... Done
Package spring is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package spring has no installation candidate

```

:confused: It's not there?[/QUOTE]


I'm now having this problem after trying to re-install after doing the Clean Workdir selection in the dep-spring menu.  DO NOT EVER DO THIS, anybody.  But anyway, yes, the new version of spring seems to want the following packages, none of which are on the standard ubuntu repos or are pointed to by the tutorial.  I'm currently looking for them somewhere.  They are:

```

  spring: Depends: libboost-filesystem1.33.1 but it is not installable
          Depends: libboost-regex1.33.1 but it is not installable
          Depends: libboost-thread1.33.1 but it is not installable
          Depends: libdevil1c2 but it is not installable
          Depends: libopenal0a but it is not installable

```



EDIT:  FIXED!!

Turns out I had the wrong repos in my sources.list, which were relics from a breezy-to-dapper upgrade.  Users should make sure the following lines are un-commented in /etc/apt/sources.list
```

deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

---

### Post by ELD on 2006-07-06
[QUOTE=keithjr]the 9 pages of posts on the dep-spring thread might have had something to do with that :)[/QUOTE]

Actually i made a new post in their general chat asking for a linux forum, 2 seconds later it was there, i am impressed with the Spring community more and more :D

---

### Post by ELD on 2006-07-07
A small update for you, the linux activity around spring is growing nicely and another person has now started making his own port in pygtk and is looking nice :D
[http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5840](http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5840)

---

### Post by The Noble on 2006-07-09
I installed everything from the repos, which went smooth, but the game didn't start. I didn't care all that much, and I am willing to wait a while for spring to mature. There is one fatal problem for my system though. (More like annoying)

I went to uninstall everything, and spring-mod-xm can't uninstall. It is really messing with me. Any time I try to reinstall and remove, it breaks, and whenever I install anything else, even non related to spring, apt-get and synaptic try to reinstall or remove the package.

Please help, I don't feel like reinstalling everything...again...

---

### Post by ELD on 2006-07-10
Hey the The Noble i had a bit of problems trying to uninstall as well (i only did it to test) please copy this post into a post on the TA Spring Linux forum at this post:
[http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5093&start=200](http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5093&start=200)

And then FBO may shed some light :)

---

### Post by keithjr on 2006-07-10
I also had issues with uninstall and re-install.  Don't try manually removing files.  That won't work.  I ended my attempts in an ubuntu re-install, however, so what do I know...

---

### Post by OctalHashX on 2006-07-17
Hey guys, I followed all the instructions. Then I typed spring-setup, and I got that blue screen. I chose 'start' and hit 'select'. I got this message from my console:

```
I: Preparing workdir...
I: Done.
I: workdir is '/home/shadowgate/.springdir/localhost.localdomain:0.0'
I: type spring-setup to configure spring
spring is using data directory: /home/shadowgate/.springdir/localhost.localdomain:0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Warning: ERROR
  Could not set video mode
I: Spring exited with errors. Press any key to continue.

```

What does this mean? All help is appreciated.

Thanks in advance and all the best.

---

### Post by keithjr on 2006-07-17
> **OctalHashX said:**
> Hey guys, I followed all the instructions. Then I typed spring-setup, and I got that blue screen. I chose 'start' and hit 'select'. I got this message from my console:

```
I: Preparing workdir...
I: Done.
I: workdir is '/home/shadowgate/.springdir/localhost.localdomain:0.0'
I: type spring-setup to configure spring
spring is using data directory: /home/shadowgate/.springdir/localhost.localdomain:0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Warning: ERROR
  Could not set video mode
I: Spring exited with errors. Press any key to continue.

```

What does this mean? All help is appreciated.

Thanks in advance and all the best.


My first guess would be missing video drivers.  What is the output if you run the command "glxinfo" in a console?

---

### Post by OctalHashX on 2006-07-17
Here is the output:

```
user@box:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by keithjr on 2006-07-18
You need to install your video drivers, it looks like.  Not to be rude but this is not a Spring problem so seek advise from the wise ones over in the Hardware forums.

---

### Post by OctalHashX on 2006-07-18
Thanks. All the best.

---

### Post by ELD on 2006-08-20
A note to anyone interested, a guy called hollowsoul has a very good Graphical Interface for playing spring offline on linux and as far as i know works well with the package FBO has supplied (see my first post for links).

Also hollowsoul is working on integrating a lobby for the next version which should hopefully support linux online gaming.

I have updated the first post with more information :)

---

### Post by HAARP on 2006-08-20
It's still a long way to be as playable as the win-version.

---

### Post by ELD on 2006-08-20
Well it is getting better and better, from the looks of things linux vs windows on the net playing so far seems pretty stable, any problems that came up are fixed for the next version.

We have a fully working offline GUI for linux too.

---

### Post by keithjr on 2006-08-20
indeed.  Perhaps link to [here]("http://taspring.clan-sy.com/phpbb/viewtopic.php?t=6492&sid=4d60a4a514f80cd3b9badb776cafa84d") for people that would like to build the game themselves instead of using outdated deb-spring...

Yes, the project is progressing very nicely.  However one must remember that even the windows version of spring is still very much in beta.  The newly supported linux version is just as buggy.  But the future is looking good!

---

### Post by ELD on 2006-08-21
keithjr if you read my post you would see this:

> 
Getting Spring:
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring)
or
TA Spring from SVN


The "TA Spring from SVN" is the same link your provided, i already put it in :P.

deb-spring is not outdated, it won't be outdated until a new release comes out, which then it will be easy for fbo to update deb-spring to simply use the new trunk release.

And yes you bring up a good point, the version isn't even at V1 yet so it will still be buggy people!

I have added more/adjusted the original post :)

Ps. Not that many care but i added a post the the Fedora game forum as well, be nice to have more than 1 distribution playing this game.

---

### Post by HAARP on 2006-08-21
Haven't seen fbo for like a month. Don't know if he'll be there when a new version comes out.

---

### Post by ELD on 2006-08-21
I am in regular contact with him, it should be fine.

---

### Post by ELD on 2007-03-02
A note about TA Spring, since my post i think one or two more versions have been released.

A guy named Hollowsoul is working hard at a good linux-gui he calls unity-lobby, it looks really good at the moment and shouldnt be too long until linux is fully playable.

---

### Post by cong06 on 2007-05-28
I'm not sure if this is the place to ask, but I noticed when I tried to run Spring, after installing, that It demanded 1024x768 graphics.
Is there anyway around this?

I'm not planning on playing. (not on this box)  but I do know that when I tried to run the game in Windows on the same computer (before I switched it over to ubunutu) the Game Lobby loaded nicely, and the game only crashed because of the graphics of the actual game.

Until the Game lobby is accesssible by another IRC client (which it may never be) I'd be nice to be able to access some of the channels even on this computer.

---

### Post by ELD on 2007-05-30
Well there is a guy called AF on the spring forums who is getting close to a working Linux Lobby :)

---

### Post by cong06 on 2007-05-30
oh. so the lobby doesn't even work yet....
I thought it was a bug with my computer.
Thanks for letting me know, I was getting bit frustrated with it not working :D.

---

### Post by ELD on 2007-05-30
There is no fully working linux lobby yet, the one that got to the point of being finished the maker gave up, now theres a few people creating different ones, so the future is good for linux :)

---

### Post by Hobo Joe on 2007-05-30
Speaking of the lobby, I have a really noobish question: How do I install and run it? :/

---

### Post by ELD on 2007-05-31
Ask all questions here => [http://spring.clan-sy.com/phpbb/viewforum.php?f=20](http://spring.clan-sy.com/phpbb/viewforum.php?f=20)

---

### Post by sjaglin on 2007-06-11
Hi, 

I am a Mandriva user and am getting to know ubuntu. Well so far so good, the install was really easy and the forums very helpful. I run the latest ubuntu with gnome as a desktop with 3d "on".

I am very interrested by this game, the gfx look great and have manged to install it on ubuntu (not on mandriva!).

Anyway the spring version I have is : Spring 0.74b3. When I launched it I get a first menu with the mission lists and then all crash with : Couldn't find any map files as a message.

How can I debug that ?

Thanks for your help!

Stef

---

### Post by ELD on 2007-06-11
As i said you should ask questions like that in the forum link i posted above.
As far as i know you need to make sure all mods and maps you download for it are in the right folders.

---

### Post by sjaglin on 2007-06-11
Ooops, Sorry i missed your post (small + me bad eyes...) I ll go to that forum instead,

Thanks 
Stef

---

### Post by ELD on 2007-06-15
No problem, for the next release i think they are actually waiting for a Linux Lobby, a guy called AF is doing a java lobby which is making good progress =]

---

### Post by cong06 on 2007-06-15
> **ELD said:**
> No problem, for the next release i think they are actually waiting for a Linux Lobby, a guy called AF is doing a java lobby which is making good progress =]

oh? the one I've been following looks like it's coming along pretty good too. Nice design, etc. [Spring Lobby by tc-](http://spring.clan-sy.com/phpbb/viewtopic.php?t=10371).

As of now, you have to build it manually, and install a bunch of libraries. I managed somehow though, so it's not impossible.

You know? I think I'm going to try out AF's Lobby though. Just for kicks.

---

### Post by ELD on 2007-06-17
I have been following that game lobby as well which looks nice, only reason i mentioned AF's and not Spring Lobby is that AF's is much further to being complete, but i would rather use spring lobby as it is not java :)

---

### Post by cong06 on 2007-06-17
yeah. that's my opinion too, though it might be easier to install. :P

---

### Post by ELD on 2007-09-26
Have updated original post with new info.

The linux lobbys are really far into development now and are everday useable :).

Come play me on spring!

---

### Post by ELD on 2008-03-05
Have updated the original post for videos and better way to get Spring.

---

### Post by lefen on 2008-03-10
Thanks for the info, am I to infer from the setup guide that an up-to-date repository for Dapper no longer exists? Not to worry if so; it'll soon be time for Hardy ;)

Thanks again!

---

### Post by ELD on 2008-03-11
I am afraid at the moment only works for Gutsy, i think if you change "gutsy" to "dapper" in the repository into it may work, don't hold me to that though it may be dangerous.

---

### Post by Keen101 on 2008-09-30
Does anyone know how to compile this from source?

I am running Ubuntu 8.10 Intrepid Ibex. The PPA repository does not have a package for it yet.

I have followed all the instructions on the compiling page, but I cant find a make file. How am i supposed to compile it?

---

### Post by Vadi on 2008-09-30
try asking on the linux section of their forums for that.

---

### Post by ELD on 2009-06-08
Just a note to say i have updated my original post to be more up-to-date with the newer spring version and website.

---

### Post by Anonymousable on 2009-06-08
Cool. I'm new here (first post). I'm Blue_Falcon on the spring forums and Spring online. It's certainly come along and it works perfectly for me. (Only since I got a new Nvidia graphics card though, Intel drivers didn't work with it).

So basically, I like spring. :D

ELD, maybe update the first post? Because now there are no mods available by apt except for Complete Annihilation.

---

### Post by Vadi on 2009-06-08
Don't think any were to begin with given their grey status.

---

### Post by ELD on 2009-06-09
There was never any mods included via apt because like my good friend Vadi said, they have always been a grey area (TA Based IP), there are a few now which could be included (Kernel Panic i beleive you can do anything with) but they are not. 

Intil drivers have always been a bit iffy with it, hopefully they will do something about that, i see from mantis bug reports it is being worked on slightly by someone.

That is the reason i liked the games page ;)

---

### Post by Anonymousable on 2009-10-23
Yes, someone may have noticed I'm reviving loads of old threads...
But Kernel Panic is now in the repo, and the CA downloader is too.
I can't play at the moment though, because of my CPU problems...

---

