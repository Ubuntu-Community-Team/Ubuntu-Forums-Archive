---
title: "totem really does suck in breezy"
date: 2005-10-25
forum: Desktop Environments
---

### Post by irish rebel on 2005-10-25
Guys I cannot uninstall totem because it will screw up my box , but christ its a terrible app compared to xine or mplayer its causing all kinds of crashes with firefox and nautilous  any patches coming out yet for it?

---

### Post by abou on 2005-10-25
Try the Xine backend for Totem rather than the Gstreamer one.  It is totem-xine and most likely easier to install through Synaptic than apt-get.

---

### Post by m@dm@x on 2005-10-25
[QUOTE=abou]Try the Xine backend for Totem rather than the Gstreamer one.  It is totem-xine and most likely easier to install through Synaptic than apt-get.[/QUOTE]

Sorry to walk on someone's thread but abou's suggestion got this to work for me.  I've been working on this for around an hour now.  Since I'm pretty new to Linux, this site and Ubuntu is allowing a "Windows Guy", walk towards to Open side.  Thanks for your help abou.

Max

---

### Post by ecobuntu on 2005-10-25
[QUOTE=m@dm@x]Sorry to walk on someone's thread but abou's suggestion got this to work for me.  I've been working on this for around an hour now.  Since I'm pretty new to Linux, this site and Ubuntu is allowing a "Windows Guy", walk towards to Open side.  Thanks for your help abou.

Max[/QUOTE]

Hey Max-
If you're ever having an issue with an engine (i.e. in Amarok, Kaffeine, etc.) install the xine-engine.  I don't get the gstreamer engine.  Personally I think it sucks.  Go with the xine-engine all the way!

---

### Post by ecobuntu on 2005-10-25
PS- You would look for the xine engine specify to each application!

---

### Post by m@dm@x on 2005-10-25
[QUOTE=ecobuntu]PS- You would look for the xine engine specify to each application![/QUOTE]

I'm installing them now ecobuntu.  At least the ones that looked like I can use them in the future.  Thanks for the help, I love this stuff.

---

### Post by LorenzoD on 2005-10-25
Yes, Totem does suck in Breezy. But it sucked before Breezy and will likely continue to suck after Breezy. Just search for vlc in synaptic, select everything that applies and problem solved.

It's a bit sad that Totem is the default movie player for Ubuntu, because it's one of those programs that can really scare people away from Linux.

---

### Post by ecobuntu on 2005-10-25
[QUOTE=m@dm@x]I'm installing them now ecobuntu.  At least the ones that looked like I can use them in the future.  Thanks for the help, I love this stuff.[/QUOTE]

No Prob. 
PS- Maybe the title of the thread should be "Gstreamer Really does suck in Breezy and Thank God Xine-Engine is there to Save the Day"

---

### Post by ecobuntu on 2005-10-25
[QUOTE=LorenzoD]Yes, Totem does suck in Breezy. But it sucked before Breezy and will likely continue to suck after Breezy. Just search for vlc in synaptic, select everything that applies and problem solved.

It's a bit sad that Totem is the default movie player for Ubuntu, because it's one of those programs that can really scare people away from Linux.[/QUOTE]

I don't care for VLC.  I can't seem to open realvideo with it.  Unfortunately the only player I can get to work is that POS called Kaffeine for that.

---

### Post by DuplexEmotions on 2005-10-25
Maybe somebody who is knowledgable about it can explain **why** totem ships with Ubuntu.

I personally use Xine for general video and mplayer's firefox plugin for streaming video.

---

### Post by abou on 2005-10-26
No problem guys.  When I first installed Ubuntu in August, and being the only second time trying Linux, I really messed with media players to try and find something that worked.  In the end, Xine played DVDs and media the best once DMA was enabled and the Xine backend for Totem fixed any issues.  VLC never really did it for me, I'll be damned if I can get Mplayer to work, and Noatun seems to only work in KDE.  

The only thing in the way was sound.  I couldn't quite get sound and video to sync properly, which was really annoying when watching a Jethro Tull concert.  Turns out this is the solution: [Q: How to configure sound to work properly in GNOME?[COLOR=Black]  _You lose the cool sound effects, but video and sound sync._[/COLOR]]("Q:%20How%20to%20configure%20sound%20to%20work%20properly%20in%20GNOME?")

As far as Gstreamer goes, I'm sure someone can get it to work well, I just can't do it myself.

---

### Post by taavi on 2005-10-26
[QUOTE=LorenzoD]It's a bit sad that Totem is the default movie player for Ubuntu, because it's one of those programs that can really scare people away from Linux.[/QUOTE]I totally agree with you. It looks nice and everything else, but god what horrors lie in the performance. Maybe the problem is between the chair and monitor.

---

### Post by darrenrxm on 2005-10-26
Yes, I do agree totem bites the big one. It was the first thing I uninstalled. I can't believe they do not have mplayer or vlc as the default media player.

---

### Post by doclivingston on 2005-10-26
[QUOTE=DuplexEmotions]Maybe somebody who is knowledgable about it can explain **why** totem ships with Ubuntu.[/QUOTE]

Ubuntu ships with Totem because it's easy to use. *Most* of the other players have a horrible mess of menu items and preferences, that the majority of people won't have a hope of understanding. I'm not saying that Totem is the best media play around, but it works reasonably well.


However, you might be asking why it ships with Totem-gstreamer instead of Totem-xine. The plan for Breezy was to split the Xine packages up into the free codecs (for main) and non-free codecs (for universe/multiverse), and then to determine which backend was going to be best. This didn't happen because the people who were going to do the splitting-up had too much other (more important) work to do, such as dealing with the X transition and the like.


A couple of things to remember:
* no matter what media player or backend Ubuntu ships, the patent-laden codecs (mp3, mpeg, xvid etc) won't be installed by default.
* no matter what media player or backend Ubuntu ships, w32codecs and the like won't be available in the main repositories
* no matter what media player or backend Ubuntu ships, gstreamer will be installed anyway - because Gnome uses it.
* gstreamer 0.10/1.0 (which will be be out in time for Dapper) will fix most of the a/v sync issues that plagued 0.8. It may not fix all the problems, but most should be fixed.

---

### Post by frodon on 2005-10-26
Well there's generally no problem at all with totem, however if you want totem to work quickly and perfectly install the totem-xine package, what you will have is **xine** with the totem interface, i think most of the users here use this package.
There is several interfaces to use with xine : totem, gxine, xine-ui, kaffeine .... choose the one you like, personally i love the totem interface but it's just my choice.
If you like mplayer and only want to use it follow this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=76946&highlight=mplayer")

---

### Post by irish rebel on 2005-10-26
Ok no excuses  Totem is brutal , reason I didnt install xine backend is this I use streamtuner alot and streamtuner works with xmms [ unless u change the default player] if you uninstall totem your box will be crap , install xine backend and xmms will not work with streamtuner because immediately after installing xine backend and update appears [ I forget which one] and then its a nightmare.
  But why oh why does such a great distro use this god forsaken product as the default Multimedia Manager , and since when has mplayer been hard to 
configure ?
We need a campaign to urge the distro masters that TOTEM MUST GO!!!!!

Slan abhaile!

---

### Post by Ugeek on 2005-10-26
As for xine frontend gxine has much much better interface and preference options than totem. you can try this out. also totem has some av synchronization problem .

---

### Post by clearnitesky on 2005-10-26
I've never used Totem, it didn't work when I was a hardcore Slackware fan either. I've always gone for MPlayer as a universal media player but since using Ubuntu I've found that Xine isn't that bad either. :)

---

### Post by Ugeek on 2005-10-26
[QUOTE=frodon]Well there's generally no problem at all with totem, however if you want totem to work quickly and perfectly install the totem-xine package, what you will have is **xine** with the totem interface, i think most of the users here use this package.
There is several interfaces to use with xine : totem, gxine, xine-ui, kaffeine .... choose the one you like, personally i love the totem interface but it's just my choice.
If you like mplayer and only want to use it follow this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=76946&highlight=mplayer")[/QUOTE]


guys, totem technically has no problem with gstreamer backend... but i feel in ubuntu especially with universe codecs it sucks. you should try out Gentoo linux to see how beautifully it works.

---

### Post by frodon on 2005-10-26
[QUOTE=irish rebel]Ok no excuses  Totem is brutal , reason I didnt install xine backend is this I use streamtuner alot and streamtuner works with xmms [ unless u change the default player] if you uninstall totem your box will be crap , install xine backend and xmms will not work with streamtuner because immediately after installing xine backend and update appears [ I forget which one] and then its a nightmare.
  But why oh why does such a great distro use this god forsaken product as the default Multimedia Manager , and since when has mplayer been hard to 
configure ?
We need a campaign to urge the distro masters that TOTEM MUST GO!!!!!

Slan abhaile![/QUOTE]Most of people live really well with totem and love it, that's why it's the **GNOME** player, besides it's really easy to install another player like VLC or Mplayer just using synaptic, so if you don't like gstreammer and xine don't use it. 
You always have the choice (or a solution) with linux, there's no link with the fact that totem is the GNOME player, no link at all.
So if you have a problem using ubuntu, open a new thread and you will get some help to solve it.

---

### Post by clearnitesky on 2005-10-26
[QUOTE=frodon]So if you have a problem using ubuntu, open a new thread and you will get some help to solve it.[/QUOTE]

Hey come on man there's nothing wrong with a bit of friendly debate :p

---

### Post by irish rebel on 2005-10-26
Actually if you read the posts most people hate Totem or rather they post help needed adds requesting how to get rid of it , I am experienced enuf with linux to use other players I just hate how its so integrated with gnome on ubuntu ....kinda reminds me of windows and IE or mp all of the same!

---

### Post by cvmostert on 2005-10-26
[QUOTE=ecobuntu]PS- You would look for the xine engine specify to each application![/QUOTE]

Yes, I also like xine more, it works better on my slow pc.. i have a 450MHz and watch dvds with xine. so i gather totem-xine would work just aswell... i will try it too..

ciao

---

