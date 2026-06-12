---
title: "Multimedia in Linux will be the Death of Me"
date: 2005-12-16
forum: General Help
---

### Post by Noah0504 on 2005-12-16
I love the entire idea of Linux and OSS.  It's one of the reasons I've always been so interested in it.

When I finally wanted to become serious about getting into Linux, I turned to Ubuntu.  Everyone was talking about how user friendly it was, and they where all very right.  Ubuntu is great.  It's really been the only distro that's recognized all of my hardware without even a hint of a problem.

Previously, I've run a dual-boot of Ubuntu and Windows XP.  A few days ago, I decided to finally give Windows the boot and make Ubuntu my only OS.

So far things are going well.  I've learned that the GIMP is a great Adobe Photoshop replacement and OpenOffice.org is a fantastic office suite.  However, there has been one problem I don't think I'll ever completely solve.  Multimedia support in Linux is something on the lines of "horrible."  Now, I understand licensing issues, but there just has to be an easy way to get support for formats such as Divx.

I installed w32codecs and totem-xine, but for some strange reason, totem-xine displays a blue line to the left of any video I play.  It's not the end of the world, but I always find myself glancing at it instead of the video I'm trying to watch.

Currently I have VLC Media Player installed.  I haven't had the chance to try it out, but from what I hear, it plays most video formats.  But, again, there is one more problem.  There is no plugin for Firefox.  I've heard Mplayer does the same and also includes a plugin for firefox, but I really don't like the look and feel of Mplayer.

Right now I'm still discovering the world that is Linux.  I'm still enjoying Ubuntu minus my troubles with multimedia support, and I think I'm going to be using it for sometime.

---

### Post by 23meg on 2005-12-16
Well you can use the mplayer plugin in Firefox and whatever other software you like and that works for you for standalone use, right?

---

### Post by ardchoille on 2005-12-16
I like to use Xine, mainly because it is the only media player in the Linux world which supports Closed Captions for the hearing impaired (closed captions are different from subtitles). Xine just works better for me than any other media player I have used.

---

### Post by Dr. Nick on 2005-12-16
If you find a media player that you like and has support for the formats then look [here]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")
The link will  install a firefox extension that will just launch your preferred media player for embedded videos. I personally just use mplayer and the mplayer plugin. What is it that you dont like about mplayer? The gtk1 look?
I have had no problems with mplayer and most all the formats I want are supported.
[]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")

---

### Post by teaker1s on 2005-12-16
look in wilki search 'restricted formats'

---

### Post by Noah0504 on 2005-12-16
[QUOTE=Dr. Nick]If you find a media player that you like and has support for the formats then look [here]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")
The link will  install a firefox extension that will just launch your preferred media player for embedded videos. I personally just use mplayer and the mplayer plugin. What is it that you dont like about mplayer? The gtk1 look?
I have had no problems with mplayer and most all the formats I want are supported.
[]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")[/QUOTE]
Thanks.

Yeah, I don't really like the look of Mplayer.  I like my applications to look like they "fit in."  That's why I like using Totem.  I can get it to play everything I need, but for some reason, I haven't solved the mysterious blue line yet.  And the Totem Firefox plugin doesn't always work either.

---

### Post by Dr. Nick on 2005-12-16
You can still use totem to play local media and the mplayer-plugin for streaming web apps. Using the mplayer plugin in ff doesnt really show much of the interface, only downfall is taht you do need mplayer installed. Thats where mediaplayer connectivity may help
What kind of video card do you have? That may be part of the blue line problem, also is the blue line happen on audio files?

---

### Post by 23meg on 2005-12-16
[QUOTE=Noah0504]Thanks.

Yeah, I don't really like the look of Mplayer.  I like my applications to look like they "fit in."  [/QUOTE]Do a forum search with the terms mplayer and gtk2 and you'll find a GTK2 build of Mplayer that "fits in" like other apps.

---

### Post by Noah0504 on 2005-12-16
[QUOTE=Dr. Nick]You can still use totem to play local media and the mplayer-plugin for streaming web apps. Using the mplayer plugin in ff doesnt really show much of the interface, only downfall is taht you do need mplayer installed. Thats where mediaplayer connectivity may help
What kind of video card do you have? That may be part of the blue line problem, also is the blue line happen on audio files?[/QUOTE]
Yeah, I think I may just suck it up and install Mplayer.  Umm, I'm not sure about the specifics of my video card.  It's made by Trident.  It's only 16MB.  Yes, the blue line appears no matter what, I don't even have to be playing video.  It only appears after I install the xine engine.  It's fine when I use gstreamer.

---

### Post by Noah0504 on 2005-12-16
[QUOTE=23meg]Do a forum search with the terms mplayer and gtk2 and you'll find a GTK2 build of Mplayer that "fits in" like other apps.[/QUOTE]
Thanks.

---

### Post by 23meg on 2005-12-16
[QUOTE=Noah0504]Yeah, I think I may just suck it up and install Mplayer.  Umm, I'm not sure about the specifics of my video card.  It's made by Trident.  It's only 16MB.  Yes, the blue line appears no matter what, I don't even have to be playing video.  It only appears after I install the xine engine.  It's fine when I use gstreamer.[/QUOTE]
What driver are you using with that card? Take a look at the "Device" your /etc/X11/xorg.conf file and see what you have in the line "Driver".

---

### Post by taurus on 2005-12-16
I am very happy with mplayer because I haven't had any problems with it.  Works on every type or format even bin extension...  After a while, you just get used to it!

---

### Post by Dr. Nick on 2005-12-16
[quote=Noah0504]Yeah, I think I may just suck it up and install Mplayer.  Umm, I'm not sure about the specifics of my video card.  It's made by Trident.  It's only 16MB.  Yes, the blue line appears no matter what, I don't even have to be playing video.  It only appears after I install the xine engine.  It's fine when I use gstreamer.[/quote]

It is most likely a bug in the video output portion of xine relating to your video card. Mplayer may be better at it since you can change the output engine. I like my applications to match, but for mplayer I make an exception :) I may try the gtk2 ver aswell, but for know just put up with the ugly prefrences UI.

---

### Post by Noah0504 on 2005-12-16
Identifier	"Trident Microsystems CyberBlade/XP"
Driver		"trident"

Seems correct to me.

---

### Post by Noah0504 on 2005-12-16
Okay, well, I think I'm just going to install Mplayer and put up with its drab interface.  Compiling applications is a little beyond me at the moment, so maybe I'll try that sometime down the road.

What's the name of the Mplayer package?  mplayer?

Also, how can I make it my default application for video and DVDs?

---

### Post by Dr. Nick on 2005-12-16
Open synaptic and search mplayer, install the one that most resembles your cpu architecture. If its a faster chip I reccomend the 686 version, or if slower you can use the 386 version. Once installed open nautilus and go to you video files, right click and hit properties and you can set the default player in the "open with" menu for each filetype


EDIT
haha I just realized my mplayer is screwed up :) so I may not be of much more help on specifics if needed until I get it fixed

---

### Post by Noah0504 on 2005-12-16
Well, I may not be installing it.  Mplayer doesn't show up in Synaptic...and yes, I have all of the repositories enabled.  ;)

---

### Post by nix4me on 2005-12-16
[QUOTE=Noah0504]Well, I may not be installing it.  Mplayer doesn't show up in Synaptic...and yes, I have all of the repositories enabled.  ;)[/QUOTE]

Its there.

enable multiverse repository.

nix4me

---

### Post by 23meg on 2005-12-16
[QUOTE=Noah0504]Okay, well, I think I'm just going to install Mplayer and put up with its drab interface.  Compiling applications is a little beyond me at the moment, so maybe I'll try that sometime down the road.
[/QUOTE]
You don't need to compile it, there are packages of mplayer built with GTK2 posted on that thread, just grab the latest and install it with ```
sudo dpkg -i  /path/to/file
```

---

### Post by Noah0504 on 2005-12-16
Well, I installed all of the needed packages and then the mplayer itself, however, when I try and launch it, it won't run.

---

### Post by Dr. Nick on 2005-12-17
[quote=Noah0504]Well, I installed all of the needed packages and then the mplayer itself, however, when I try and launch it, it won't run.[/quote] 
How did you try to launch it, from a menu it created? If so then open a terminal and run gmplayer and look for any error messages

---

### Post by aysiu on 2005-12-17
[QUOTE=Noah0504]Multimedia support in Linux is something on the lines of "horrible."  Now, I understand licensing issues, but there just has to be an easy way to get support for formats such as Divx.[/QUOTE] Linux <> Ubuntu even though Ubuntu = Linux.

Ubuntu is a free OS in every sense. It's free of charge and free of proprietary codecs.

If you want *Linux* with built-in support for proprietary multimedia codecs, consider using Mepis, Blag, or Linspire.

If you want easy multimedia in Ubuntu, I believe there's a project called Automatix that will do that for you...

---

### Post by TrinitronX on 2005-12-17
I followed the thread about how to compile mplayer from the cvs source, and it's been working awesomely, (once I switched the video engine to use my video card).  I also found out that there's a way to have kde skin gtk applications with whatever kde theme you have at the time.  It really has helped make all the once ugly programs look nice like they should :P.
I'm not sure if there's a way to do this in gnome, as I do not use it.

---

