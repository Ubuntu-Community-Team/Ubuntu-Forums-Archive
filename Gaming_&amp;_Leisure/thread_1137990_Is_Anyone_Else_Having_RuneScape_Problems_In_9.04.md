---
title: "Is Anyone Else Having RuneScape Problems In 9.04?"
date: 2009-04-26
forum: Gaming &amp; Leisure
---

### Post by Grant A. on 2009-04-26
Is anyone else having problems wið RuneScape in Firefox on Kubuntu 9.04? When I try to play in HD, ðe game turns grey and freezes upon choosing ðat setting. Does anyone know how to rectify ðis problem? Does ðe Java 5 plugin fix it?

---

### Post by maheshjr2000 on 2009-04-26
You running intel as your GFX?

---

### Post by Grant A. on 2009-04-26
Nvidia GeForce 6600.

---

### Post by lnxnut on 2009-04-26
I'm running Ubuntu 9.04 with ATI HD3300 and God knows if it works with ATI it should work with Nvidia.  One thing I noticed you mentioned JRE 5, try 6.  Make sure your graphics driver is installed and in your synaptic package manager search sun java and make sure all your plugins are installed, and make sure your running 6 and not 5, not saying 5 doesn't work but 6 is the newest.

---

### Post by lnxnut on 2009-04-26
One more thing just crossed my mind, are you running the 32 or 64-bit version of kubuntu?

---

### Post by Grant A. on 2009-04-26
I'm using the 32-bit Kubuntu and Java 6, I was wondering if Java 5 worked, though.

---

### Post by bobbicat on 2009-04-26
I think people who have Jaunty are all finding that if they try to play Runescape High Definition then the result is a browser crash. 

I'm using the 32-bit Kubuntu and Java 6 with Firefox. 

I've also seen reports of the same problem with 64-bit, other browsers & various versions of Java. Different hardware both Intel & AMD, various graphics cards, all are reported with the same problem. Updating software doesn't seem to have helped anyone either.

I believe the problem might be related to OpenGL, but that is only what I have read from searches I've made. I'm no authority on the subject. 

If you recall, when Runescape HD was released there were similar problems. 

I haven't been able to find any recommended workarounds for the issue, maybe someone will come up with one to fix this problem. 

Then again, perhaps we will have to wait until the bug gets fixed.

---

### Post by BoGFx on 2009-04-26
I am having problems as well.  I recently got a member status, so from there on I tried to play HD. I have a 32 bit and without HD it works fine. 
 
The second my browser attempts to load, everything crashes. I eventualy mailed Jagex support about it. They told me they were/have fixed it. 
 
The time being, text based games don't crash, that is why I transfered over to [www.vitalmafia.com]("http://www.vitalmafia.com") . 
 
Note to Mods: I am notmeaning to advertise the site, just saying my opinion, and until it is fixed, find a backup plan.

---

### Post by morbid_bean on 2009-04-27
Me, I have always had problems with Runescape HD

---

### Post by Strongman332 on 2009-04-29
problem happens in ubuntu 9.04 64 bit

nvidia 8600 gt

i think this may affect all environments not just KDE

i have reinstalled Java 16 times still does not work

---

### Post by Strongman332 on 2009-04-30
this got rune scape working for me in 9.04 but not in hd
```
sudo apt-get update

```
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
```
sudo update-java-alternatives -s java-6-sun
```

then run
```
gksudo gedit /etc/jvm
```

and add the fallowing to the file (it should be empty)

```
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr
```

save then run rune scape and enjoy

---

### Post by abaker on 2009-04-30
I have been having this same problem as well with 9.04. 
Also in the previous version of Ubuntu I could get on runescape HD but I couldn't move my mouse out of the window area or else it would crash.  Anyone know why this is yet?

---

### Post by bobbicat on 2009-05-01
There appears to be some sort of bug that prevents Runescape from running in High Definition mode. 

The bug appears after updating to Jaunty.

This bug was reported about a month ago. 

So far, apart from acknowledging that the bug exists, no action has been taken.

The workaround appears to be to remove Jaunty from your computer and reinstall Intrepid.

---

### Post by Strongman332 on 2009-05-01
thats a sorry work around

in fact its not one at all

has any one considered trying rune scape in a wine loaded firefox

---

### Post by MakotoTheKnight on 2009-05-01
> **Strongman332 said:**
> thats a sorry work around

in fact its not one at all

has any one considered trying rune scape in a wine loaded firefox

Let's not consider this an option.

I suppose the best option right now is to sit back and wait for the developers to fix this bug. That's all we can do, really.

---

### Post by bobbicat on 2009-05-02
Thanks for the helpful comments :) 

I suppose the best option right now is to sit back, play Runescape in Intrepid and wait for the developers to fix this bug. That's all I can do, really. 

Sad ?? Never !

---

### Post by Strongman332 on 2009-05-02
> **MakotoTheKnight said:**
> Let's not consider this an option.

I suppose the best option right now is to sit back and wait for the developers to fix this bug. That's all we can do, really.

you have a point and i will have to agree with you here if the Java fix i posted dose not work. sorry your going to have to wait.

---

### Post by Omgee on 2009-05-06
Same problem here, only I'm still running Ubuntu Intrepid -- 8.10. Fresh install, just installed Java 6 and associated plug-ins. I can run the low-res version just fine, but HD crashes Firefox instantly.

---

### Post by Rigorous on 2009-05-06
Are they even working on a fix for this?

---

### Post by Benjabba on 2009-05-07
Nope, I tried this sequence and it did not work.  I still get the grey screen, 

Ubuntu 9.04 inspiron 1545 ati video enabled, worked with intrepid, don't want to go back.

---

### Post by wolfyking2 on 2009-05-08
Well, even though I'm not using Jaunty, i have an intel card and HD in runescape works fine...except that it's really slow :D

---

### Post by frigginacky on 2009-05-10
Same problem here.  If I'd realized Jaunty was going to kill RS HD, I'd have stayed with Intrepid a bit longer. :(  Hope it gets fixed soon.

---

### Post by Davefin on 2009-05-10
Well, I am having the same problems, but - it runs when I run it SOMETIMES, but slow - and when I move, resize the windows or switch to another, it freezes and crashes. Getting really ....ed with it =P

I certainly won't do a downgrade =P Now I just farm and sometimes hunt in SD, swear, look at forums, create RS-related thingies in gimp, chat with friends and have more time on everything... But still, I can't wait till they fix it... =P 

Ubuntu, sunjava6, ATI Sapphire HD... >.> in windows it runs without any lag with all effects, anti-aliasing, fullscreen... but I won't use Wine, too much risk..

We just have to wait, hope and bump this thread, maybe they'll fix it sometimes xD

---

### Post by LingLing on 2009-05-12
:(

i was experiencing the same problems with hd in jaunty.

but now it doesn't even work in low res anymore! (since 2 days or so)

i have a PC and laptop, both with nvidia and jaunty.

---

### Post by connorh123 on 2009-05-12
It's fine with me.
The only problem is HD, but that's okay.

---

### Post by Orlsend on 2009-05-13
RS works on Intrepid, even in HD.

---

### Post by Davefin on 2009-05-13
yes, in Interpid it works... the problem is in Jaunty only.. and SD works fine...
but HD in Jaunty - white screen :/

---

### Post by Strongman332 on 2009-05-14
has some one made a bug report yet?

---

### Post by frigginacky on 2009-05-15
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/355742]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/355742").

---

### Post by Grant A. on 2009-05-16
Does it work well in Hardy?

I'm giving up on Jaunty. :(

---

### Post by demonon on 2009-05-17
I use ubuntu jaunty x64 and I have the official java installed through my packet manager.
HD doesn't work in RS, and my game turns completely white sometimes too for no reason.
I have tried playing in Firefox and my system is up to date.
I really haven't tried poking around, so I don't know how severe this problem is.

O yeah, I have an Nvidia 8600 gt and have the latest 180.44 drivers installed.

---

### Post by TaintedBllack on 2009-05-18
HD Fullscreen works for me but for some reason both the gnome panels still show up covering up part of the game. Any idea on how to make it cover over both the panels?

---

### Post by Grant A. on 2009-05-19
Ok guys, I reinstalled Kubuntu Hardy Heron, and RuneScape HD works great now. There were a few minor problems, such as the sound not coming on right away, but the latest update to RuneScape seems to have fixed that.

**Note:** It takes a little while for the game to start up, but it runs fine after that, aside from the fact that moving the cursor outside of the browser will freeze the game until it moves back into the area of the screen that the window is occupying.

Perhaps it's true what they say, the LTS release is always better in terms of stability. :)

---

### Post by travis.cthall on 2009-05-24
Running 9.04 32bit on an ATI 3200, HD runs fine, but when i switch desktops it goes blank...

---

### Post by Strongman332 on 2009-06-19
confirmed runescape hd does work in wine with fire fox and the JRE 6u14 if you get the direct download form the java web site. I have only had 1 crash i had to restart fire fox but it was ok:popcorn:

---

### Post by Davefin on 2009-06-19
Idk if it works in hardy, but a friend of me found out that is works when you launch it from [[SIZE=4]miniclip.com[/SIZE]]("http://miniclip.com"). I can't tell if it is true because my GRUB is messed up now, but make sure to try it and, if success or not, post it here ;) thx.

---

### Post by Strongman332 on 2009-06-20
miniclip.com does not work

---

### Post by tanager2 on 2009-07-17
I can't run Runescape at all in the new release - not even in low def. Problems connecting to server. If anyone can tell me how to revert to the previous Ubuntu version (I didn't set mine up) I'd appreciate it. It had its own problems but it was better than this, dangit.

---

### Post by doorknob60 on 2009-07-18
Hey, HD works for me now. I suspect that using Firefox 3.5 somehow fixed it, even though other browsers it also works in now too. I'm using Arch, but I heard someone else on the RS forums that uses Ubuntu say that it started working for them too after upgrading to FF 3.5. Try it for yourself :)

---

### Post by Technique13 on 2009-07-18
i fixed the HD problem in 9.04 just by updating to firefox 3.5, dont have sound though...

---

### Post by Shiva64 on 2009-07-30
I've been having the same problem. Using Jaunty, with all latest updates, and using Firefox 3.5.1. Using some sort of NVidia GeForce card, unsure as this is a friend's laptop. But from what I gather, it's not a graphics card problem, so yeah. Latest Java as well.

And this only happens in HD mode. :/

---

