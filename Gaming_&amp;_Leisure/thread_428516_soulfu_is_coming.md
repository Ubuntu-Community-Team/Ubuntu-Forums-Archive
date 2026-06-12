---
title: "soulfu is coming"
date: 2007-04-30
forum: Gaming &amp; Leisure
---

### Post by aanderse on 2007-04-30
there was some mention on these boards some month ago about a new game in development (from the original developer of egoboo) called soulfu ([http://www.aaronbishopgames.com/)](http://www.aaronbishopgames.com/)),  it looks really great with a sort of snes zelda feel to the graphics (but 3d) and the videos are awesome.  the game has now been released for windows, with the gnu/linux and mac versions soon to come (as the website states).  if anyone was really anxious i'm sure they could give it a try in wine, but i'm sure the gnu/linux version will be out very soon :)

also ... the author was convinced to put egoboo under a gpl license, so who knows, maybe if we e-mail him and ask him politely he will consider the same for soulfu because it looks like a great game.

so keep an eye out on the site because soulfu is coming soon.

---

### Post by Swarms on 2007-04-30
Looks amazing, tried quickly to run it in wine but it crashed my pc and didn't went further. :)

---

### Post by tuple on 2007-05-02
On edgy here with the wine repository.  Not in front of my machine so I can't check the wine version right now.  It worked great in wine for me.

This game is best with a gamepad/joystick of some sort. There is a network portion that he hasn't released yet.  It is supposedly done.  This game could be lots of fun multiplayer.

Gotta say that I'm impressed, one person built and designed pretty much this whole game?!  Nice job Aaron!

It will remind you of egoboo, but the game play seems much better.  Sadly, all recent egoboo developement does not support linux at all.  Even in wine I couldn't get it to work.

There is a #soulfu channel on freenode if anyone wants to chat about it :)

---

### Post by udevil on 2008-01-20
Hi, I finally got a working Soulfu ubuntu package running on my Eee PC 701 (eeeXubuntu).  But the deb is too big (14MB) to attach here. What can I do? :)

---

### Post by udevil on 2008-01-22
Here is the Ubuntu .deb package converted from the Suse RPM with alien. I've tested it and it works nicely. Have fun! 

[http://www.mediafire.com/?7dcm2fl9hgn](http://www.mediafire.com/?7dcm2fl9hgn)

---

### Post by argraff on 2008-01-24
This is so cool - I've been running SoulFu under wine for a while, but the deb works better. Still don't have sound in this game for me! (Anyone?)

I don't know if he'll release it GPL, but I could ask him (brother-in-law). And yes, he's a one man show - I watched him do it! Amazing. And despite many conversations about the topic, I still can't wrap my head around how you actually *make* a video game...:lolflag:

If he's interested, can he make the deb available on his site?

---

### Post by henriquemaia on 2008-01-24
> **udevil said:**
> Here is the Ubuntu .deb package converted from the Suse RPM with alien. I've tested it and it works nicely. Have fun! 

[http://www.mediafire.com/?7dcm2fl9hgn](http://www.mediafire.com/?7dcm2fl9hgn)

This game is great. Thanks for posting the .deb .

---

### Post by slimdanny on 2008-01-25
Thanks for the deb, I'll be sure to add the game to my site.

---

### Post by XplOzIOn on 2008-01-26
how about some amd64 version for a change?

---

### Post by Perfect Storm on 2008-01-26
Got it working with Ubuntu 64-bit with a little bit of hack. :guitar:

---

### Post by XplOzIOn on 2008-01-26
> **Artificial Intelligence said:**
> Got it working with Ubuntu 64-bit with a little bit of hack. :guitar:

Please show me the ways of the bonsai tree.

I have not been able to make it work :(

---

### Post by Perfect Storm on 2008-01-26
I'm writing on it. Just keep an eye on my Ubuntu 64-bit gaming guide sticky.

---

### Post by XplOzIOn on 2008-01-26
> **Artificial Intelligence said:**
> I'm writing on it. Just keep an eye on my Ubuntu 64-bit gaming guide sticky.

Yeah i noticed you added it there. Im htting Refresh every  minutes hehe

Thanks alot AI ! =D>

---

### Post by Perfect Storm on 2008-01-26
Okay here it is: [http://gaming.gwos.org/doku.php/guides:64bit:soulfu](http://gaming.gwos.org/doku.php/guides:64bit:soulfu)
I hacked the 32-bit package and put it up for download - Note it still ned 32-bit layers which are described in the guide.

Feedback is welcome (I may have missed something).

---

### Post by XplOzIOn on 2008-01-26
> **Artificial Intelligence said:**
> Okay here it is: [http://gaming.gwos.org/doku.php/guides:64bit:soulfu](http://gaming.gwos.org/doku.php/guides:64bit:soulfu)
I hacked the 32-bit package and put it up for download - Note it still ned 32-bit layers which are described in the guide.

Feedback is welcome (I may have missed something).

Testing.. Testing..... Testing....

Test Result: 

```
xplozion@opteron:~$ sudo dpkg -i soulfu.deb
Selecting previously deselected package soulfu.
(Reading database ... 97717 files and directories currently installed.)
Unpacking soulfu (from soulfu.deb) ...
dpkg: dependency problems prevent configuration of soulfu:
 soulfu depends on libsdl-net1.2; however:
  Package libsdl-net1.2 is not installed.
dpkg: error processing soulfu (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 soulfu
```

i did

```
getlibs -i soulfu.deb
sudo apt-get install -f
```

Game runs now... add the missing lib32 and everything great!!

---

### Post by Perfect Storm on 2008-01-26
Check if libsdl-net is installed. But it shouldn't really matters as you have the 32-bit layers SDL net installed.

---

### Post by XplOzIOn on 2008-01-26
Hey AI,

libsdl-net1.2 wasent installed. I Installed it afer getting the error.

---

### Post by Perfect Storm on 2008-01-26
Strange...It is in the dependency list of the package.

Try uninstall soulfu.deb and reinstall it and see if it's ok.

---

### Post by XplOzIOn on 2008-01-26
> **Artificial Intelligence said:**
> Strange...It is in the dependency list of the package.

Try uninstall soulfu.deb and reinstall it and see if it's ok.

Since the dependencies are already installed, uninstalling soulfu and installing it didn't gave me any errors.

You sure the dependencies are in the list? Just to make sure

Also in the guide i believe you should change Alien Arena to Soulfu

> Before Installation

Make sure that the driver to your 3D graphic card is proper installed and working.
Next you need is to install 32-bit libs to make Alien Arena working;

---

### Post by Perfect Storm on 2008-01-26
Aye,

```
Depends: libc6 (>= 2.6-1), libgl1-mesa-glx | libgl1, libogg0 (>= 1.1.3), libsdl-net1.2, libsdl1.2debian (>= 1.2.10-1), libvorbis0a (>= 1.1.2),  ia32-libs, getlibs
```


will do - a bit hasty this time.

---

### Post by XplOzIOn on 2008-01-26
Indeed its strange it gave me the error.

Well lets see if someone else tries. 
Saw you edited the game name in the guide :)

---

### Post by Perfect Storm on 2008-01-26
Aye, I'm quick to correct stuff ;)

---

### Post by Sukarn on 2008-01-28
Package from Artificial Intelligence installing fine here.

I haven't tried running the game yet.

---

### Post by penguin master on 2008-04-28
I cant seem to run it. I'm a ubuntu noob and have no idea how to run it              
:confused::confused::confused:

---

### Post by 0graham0 on 2009-05-14
Just installed this today on Ubuntu 9.04 x64 and I am getting a really bad screen flicker when I run it. I've tried turning off all the video options in game; i've tried full screen and windowed mode and i've also tried different resolutions all with the same result: scren flicker. My video card, an ATI radeon x300 hasn't had a problem in other games including 3d titles like Tremulous. Any help is greatly appreciated.

---

### Post by Frem on 2009-05-15
Do you have Desktop Effects turned on?

---

### Post by jimy_james on 2009-05-24
this is slightly off topic but... I installed SoulFu, it looks great, runs well, and is generally just bitch'n.  I've been looking for a great rpg for a while, now it's here.  Anyways can anybody save?  Saving seems like a pretty crucial feature, where is it? or how can it be done? any ideas'd be great.  thanks

---

