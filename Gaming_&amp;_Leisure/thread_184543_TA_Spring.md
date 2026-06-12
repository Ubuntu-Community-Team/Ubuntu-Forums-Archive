---
title: "TA Spring"
date: 2006-05-30
forum: Gaming &amp; Leisure
---

### Post by ELD on 2006-05-30
Well thanks to a little nudge by me there will soon hopefully be a .deb available for TA Spring the remake of Total Annihilation, only better. Check out this post -  [http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5093&start=0&postdays=0&postorder=asc&highlight=](http://taspring.clan-sy.com/phpbb/viewtopic.php?t=5093&start=0&postdays=0&postorder=asc&highlight=) 

It is a long read, but the jist of it - they are finding ftp space and they should then upload some .debs :)

official website:
[www.ta-spring.com](www.ta-spring.com)

---

### Post by GameGod on 2006-05-30
Sweet, thanks! :)

---

### Post by charlieg on 2006-05-30
But will you still need the original TA with this .deb or does it use some of the custom context available from the TA (Spring) community?

---

### Post by KingBahamut on 2006-05-30
Charlieg, TA-Spring is a total redux of TA as far as Ive known, This is not dissimiliar to TA3d -- [http://ta3d.sourceforge.net/](http://ta3d.sourceforge.net/)

---

### Post by B0rsuk on 2006-05-30
There are, apparently, some custom mods for TA Spring. Spring is not meant as TA clone, but rather a TA-like engine with extra capabilities and many limitations gone.

---

### Post by christhemonkey on 2006-05-30
Ooooh, i do like the look of that!

---

### Post by ELD on 2006-05-30
[QUOTE=B0rsuk]There are, apparently, some custom mods for TA Spring. Spring is not meant as TA clone, but rather a TA-like engine with extra capabilities and many limitations gone.[/QUOTE]

He is very right.

There are a few very good mods for TA Spring at the moment, i am pretty sure the TA Spring debs will come with the start mod (XTA) which is a revamped models and content from the original Total Annihilation.

---

### Post by ELD on 2006-06-02
For interested people the .deb files have now been built for TA Spring.

Check this guide on how to work it:[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play)

Although to get straight into using it for Ubuntu click the link below:
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di)

Using this game you can successfully setup TA Spring, setup maps, mods, ai :)

Yes the author even made a guide!

---

### Post by joncheyne on 2006-06-02
Followed the instructions, on dapper, got this:

```
spring
I: workdir is '/home/jon/.springdir/localhost.localdomain:0.0'
I: type spring-setup to configure mods/maps/units
Warning: Incorrect/Missing content:
  FT_New_Face failed:cannot open resource
```

Any ideas?

---

### Post by B0rsuk on 2006-06-02
[QUOTE=joncheyne]Followed the instructions, on dapper, got this:

```
spring
I: workdir is '/home/jon/.springdir/localhost.localdomain:0.0'
I: type spring-setup to configure mods/maps/units
Warning: Incorrect/Missing content:
  FT_New_Face failed:cannot open resource
```

Any ideas?[/QUOTE]

Do you have the game (Total Annihilation) ? TA Spring by default uses data from the commercial game.

---

### Post by ELD on 2006-06-02
joncheyne: I have posted in the TA Spring forums topic for this, hopefully we will get a reply :)

B0rsuk: TA Spring comes with its own content.

---

### Post by joncheyne on 2006-06-02
ELD: many thanks!

---

### Post by ELD on 2006-06-02
And just so you know, it happens to me too.

I will update here as soon as i get anything from them :)

---

### Post by ELD on 2006-06-08
A note to anyone interested, i am keeping at them with bugs and such and will update here again once i have gotten it to work and bugged them enough to make a stable enough version :)

---

### Post by joncheyne on 2006-06-09
[QUOTE=ELD]A note to anyone interested, i am keeping at them with bugs and such and will update here again once i have gotten it to work and bugged them enough to make a stable enough version :)[/QUOTE]

A valuable service!

---

### Post by Wordlet on 2006-06-10
Thanks ELD :D I am also having the same problem.

---

### Post by tollbooth on 2006-06-12
thanks, I love this game, just one question though, is it just for linux or is it for windows too, I havent read everything on it yet, and my brother loves this game and still uses windows.

---

### Post by ELD on 2006-06-12
[QUOTE=tollbooth]thanks, I love this game, just one question though, is it just for linux or is it for windows too, I havent read everything on it yet, and my brother loves this game and still uses windows.[/QUOTE]

TA Spring is currently only officially for windows, but it is open source and the linux port is comming along. So unofficially it is for any OS which can support it's needs, windows and linux being two of them.

I have been working with the person doing the linux port which i am following and we have figured the error, he is a quote from him:
> 
It seems as there's no 'lndir' utility in the Ubuntu world. Maybe because it's a XFree86-tool which was dropped when everyone moved to xorg. I didn't know about this tool's origin. I'm going to reimplement it's functionality in perl to remove this dependency.

FBO

So once he has reimplemented something (i'm not sure what he is actually changing) we should have a working TA Spring for linux.
Although there is currently no lobby client so we will probably have to play with bots for a while, and we can't play with windows players because of a 'float' problem which windows and linux do differently but they are working on it...slowly.


Do i follow this game too much? Haha :)

---

### Post by Wordlet on 2006-06-12
The fix has been implemented! It doesn't seem to work for ELD but it does for me so so far the effectiveness of this fix is 50/50 lol

[http://taspring.clan-sy.com/phpbb/viewtopic.php?p=86915#86915](http://taspring.clan-sy.com/phpbb/viewtopic.php?p=86915#86915)
that's the link to the post where he has the link to the updated spring-scripts package which will be available on the server tommorrow..well in exactly 24 hours lol. after updating the package run spring-setup press save and exit then run spring and it works :D

---

### Post by ELD on 2006-06-13
Thanks to amazing efforts by the person known as FBO on the TA Spring forums i have it working now (but not fully...but enough).

I will wait until FBO updates his guide to reflect the new changes and then i will let you all know.

---

### Post by Wordlet on 2006-06-15
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play)

The guide has been updated and the packages are now available for Ubuntu dapper. People with dapper only have to follow the link above's instructions while adding the Dapper line to the sources.list file if you still have breezy or older then you'll have to follow the instructions under - 
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di)

---

### Post by dlpfmVfH on 2006-06-16
[QUOTE=Wordlet][http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play)

The guide has been updated and the packages are now available for Ubuntu dapper. People with dapper only have to follow the link above's instructions while adding the Dapper line to the sources.list file if you still have breezy or older then you'll have to follow the instructions under - 
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di)[/QUOTE]

Thanks for the info,
I really love this game, it was my first lan-pary game in the old days...hehe, 
It still rocks TA-spring is in my view one of the best things for linux

---

### Post by Fallom on 2006-06-16
Has anyone had any luck getting the original TA to work with direct IP? TA Spring is great and all, but after messing around with it I still prefer playing the original game.

---

### Post by Wordlet on 2006-06-17
I've been able to get it to work with cedega 4.3

---

### Post by ELD on 2006-06-17
When i used cedega last year it said on the forums and their game database that the IP gaming never worked?

---

### Post by Wordlet on 2006-06-17
There's a fix on the cedega wiki you just need to take a couple of files from the system32 folder of a windows installation or you can download them from a link on the wiki then you edit the .reg file in the .transgaming dir. Here's the link to the cedega wiki total annihilation - [http://cedegawiki.sweetleafstudios.com/wiki/Total_Annihilation](http://cedegawiki.sweetleafstudios.com/wiki/Total_Annihilation)

---

### Post by Fallom on 2006-06-17
[QUOTE=Wordlet]There's a fix on the cedega wiki you just need to take a couple of files from the system32 folder of a windows installation or you can download them from a link on the wiki then you edit the .reg file in the .transgaming dir. Here's the link to the cedega wiki total annihilation - [http://cedegawiki.sweetleafstudios.com/wiki/Total_Annihilation](http://cedegawiki.sweetleafstudios.com/wiki/Total_Annihilation)[/QUOTE]

My god - I didn't think it was possible.

Thank you so much!

Edit: Oh wait, TA crashes when I run it with Cedega. How typical - a game that works for everyone else I know who has Ubuntu wont work for me. This is really frustrating :(

---

### Post by kujeger on 2006-06-17
speaking about cedega and stuff, TA Spring works 100% with wine right out of the box. So there's no excuse to not play some multiplayer.

---

### Post by Wordlet on 2006-06-17
Fallom I've only been able to get it to work with 4.3 4.0-4.2 crash as you said and 5.0+ don't see the fix.

---

### Post by Fallom on 2006-06-18
So is there a multiplayer interface for DebSpring?

---

### Post by HAARP on 2006-06-18
> So is there a multiplayer interface for DebSpring?

No, there isn't. Currently, Linux and Windows Spring have sync issues, you won't be able to play it online anyway

---

### Post by ELD on 2006-06-19
Well i beleive you can play linux spring on a lan but not the internet.

There are lobbys that semi-work on linux, but the developers dissapeared, one looked very promising too :(

I am going to create a website dedicated to Linux TA Spring which will have all the information you may require, download links, forum etc.

Much better than a few posts spread across a few websites, and the official website is not Linux friendly enough for my liking.

I may need moderators and contributors for this website, if you are interested hit me up with a PM, i am determind to make a decent linux community for spring :)

---

### Post by Dali on 2006-06-19
It crashes out for me with this message:

ERROR: Update drivers
  Needed extension GL_ARB_texture_compression not found

I'm pretty sure it has something to do with running Xgl/Compiz but I'm not sure how to fix it.  I tried the export XLIB_.... etc. fix, but no joy.  I use the nonXgl script fix on occasion as well, but that brings me no joy as well.

Anyone have any good ideas?

Cheers,

Dali

---

### Post by Wordlet on 2006-06-19
[QUOTE=Dali]It crashes out for me with this message:

ERROR: Update drivers
  Needed extension GL_ARB_texture_compression not found

I'm pretty sure it has something to do with running Xgl/Compiz but I'm not sure how to fix it.  I tried the export XLIB_.... etc. fix, but no joy.  I use the nonXgl script fix on occasion as well, but that brings me no joy as well.

Anyone have any good ideas?

Cheers,

Dali[/QUOTE]
Try changing the resolution to a lower setting. with spring-setup -> video

---

### Post by Dali on 2006-06-19
Alas, but no.  

Resolution changes don't fix the problem.  I just might try rebooting without xgl and seeing if that really is the issue.

Thanks for the idea, though!

Dali

---

### Post by ELD on 2006-06-21
Just a note, i have setup a new TA Spring Linux website at [www.milztech.com](www.milztech.com)

---

### Post by Tobi Vollebregt on 2006-06-22
I don't really like any attempts to split up the community.

Why don't you just ask one of our site admins (of taspring.clan-sy.com) to make a linux sub forum or anything like that before wasting (IMHO) time setting up your own website?

Or make the website (wiki) more linux friendly yourself?

I don't want to sound harsh, but there's a reason the website currently isn't linux friendly and it's called manpower.

---

### Post by dmh-bidlah on 2006-06-22
I'm getting errors trying to download the packages from the repos. 

Failed to fetch [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb)  Unable to fetch file, server said '/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb: No such file or directory.

etc.
Any ideas?

---

### Post by dlpfmVfH on 2006-06-22
[QUOTE=dmh-bidlah]I'm getting errors trying to download the packages from the repos. 

Failed to fetch [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb)  Unable to fetch file, server said '/pub/linux/people/fbo/debspring/dapper/../all/spring-scripts/2.1-1/spring-scripts_2.1-1_all.deb: No such file or directory.

etc.
Any ideas?[/QUOTE]

Yes, he's updating his server, with new packages, but there are some problems with the package list apt downloads, the new locations aren't updated.

---

### Post by dmh-bidlah on 2006-06-22
I figured as much. Oh well.

---

### Post by Wordlet on 2006-06-22
[QUOTE=dmh-bidlah]I figured as much. Oh well.[/QUOTE]
Should be fixed by tommorrow at 14:30 MST

---

### Post by ELD on 2006-06-25
The packages should be fully working again now.

Also i have found that a person on the TA Spring forums by the name of AF is working on a java lobby, so linux may finally be able to play spring online :D

---

### Post by Cheizzz on 2006-06-25
I'm somewhat confused. if I start TA spring  I end up in an menu that lets me choose out of various "scripts". Is this meant this way? because I have no idea which one to pick just to play a skirmish game of some sort...

Also, TA spring is a 3D game, right? how do I rotate the camera then? I can't find a "options" menu-item to configure these things.

---

### Post by ELD on 2006-06-25
Well the latest version should just auto-send you into a skirmish unless you have set it up to show you the menu.

You want to actually look up the controls on the official website...
[http://taspring.clan-sy.com/wiki/Using_Spring#Camera_Modes](http://taspring.clan-sy.com/wiki/Using_Spring#Camera_Modes)

---

### Post by Wordlet on 2006-06-25
There's a LOT of buttons and things to configure how the game works i believe it's shift mousewheel or ctrl mousewheel to change the angle and such or the up an down arrows if you don't have a wheel mouse. And as ELD said the newest version sends you right into a skirmish

---

### Post by keithjr on 2006-06-26
ELD, great job with all the TA:Spring support you've given us, I'm gonna dive into this and try to learn as much as I can...

Wordlet, for a list of the default key bindings and also instructions on how to customize them, see this guide:  [http://taspring.clan-sy.com/wiki/Using_Spring](http://taspring.clan-sy.com/wiki/Using_Spring)
(this is actually the same guide ELD posted)

Does anybody know how to go about loading some of the automatically-generated replays?  They seem be be generated in ~/.springdir/demos

---

### Post by ELD on 2006-06-26
Thanks a lot :)

And please refer to this post [http://www.ubuntuforums.org/showthread.php?t=203448](http://www.ubuntuforums.org/showthread.php?t=203448)

As it contains better information :)

---

### Post by keithjr on 2006-06-26
[QUOTE=ELD]Thanks a lot :)

And please refer to this post [http://www.ubuntuforums.org/showthread.php?t=203448](http://www.ubuntuforums.org/showthread.php?t=203448)

As it contains better information :)[/QUOTE]


I know that!  I've posted in it several times ;) :rolleyes: 

I didn't want to start posting tech support questions in it, however, so I'm sending those that I have over here.

---

### Post by lefen on 2008-03-10
hay all, apologies for dreging up an old thread but I'm having problems installing TA Spring using DebSpring:

[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#I_just_wanna_play)

I added this to sources.list:

```
## Spring Packages (RTS game)
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
```

but running:

```
sudo apt-get install spring-release
```

returns:

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  spring-release: Depends: spring-scripts but it is not going to be installed
                  Depends: spring-basedata but it is not going to be installed
E: Broken packages
```

Is Spring itself a dead project, since their website seems to be down, or am I doing something stupid with the installer?? :)

Much obliged for any help, I got a Jones for TA :>

---

### Post by ELD on 2008-03-10
Please see this topic -> [http://ubuntuforums.org/showthread.php?t=203448](http://ubuntuforums.org/showthread.php?t=203448)

---

### Post by Perfect Storm on 2008-03-11
[Closed]

Follow the link ELD gave.

---

