---
title: "Ventrilo in Wine"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by Tellisk on 2007-04-19
So it sounds like the ideal solution to any problem concerning Ventrilo is to use TeamSpeak instead. Unfortunately my guild in WoW uses a Ventrilo server, so I'd like to get that working.

So far, everything works. (People say I sound like a robot, but I can deal with that and worry about it later)

The only problem is that when Ventrilo is not my top window, it doesn't detect my push-to-talk key.

This of course, makes speaking in-game impossible. Anyone know any fix?

---

### Post by Tellisk on 2007-04-19
OK nevermind, it works. Only if WoW is on top though, which is good enough for me. (must be a Wine thing)

---

### Post by BetaguyGZT on 2007-04-20
I'd love to get Ventrillo working. What specific configuration in the Vent Setup are you using? I get an error saying it can't find the codecs.

---

### Post by jkw on 2007-04-22
> **BetaguyGZT said:**
> I'd love to get Ventrillo working. What specific configuration in the Vent Setup are you using? I get an error saying it can't find the codecs.

Same here. Says that I don't have GSM-codecs.

---

### Post by Psychomechanix on 2007-04-23
Bumping this thread since I'd LOVE to get ventrilo going. 

Ok...I am a complete noob to Linux. I'm using Feisty 7.04. Can someone post a Dummy's Guide to running Ventrilo through WINE? I also know nothing about WINE. I do have it installed and so far the only thing I have done with it is use it to start UTorrent, which seems to work fine. Help would be greatly appreciated thx!

---

### Post by Sammi on 2007-04-24
Firstly: ALWAYS check appdb.winehq.org for info on the program you're trying to run in Wine before you come here to ask. There's almost always a good guide for getting around common problems there.

In this case the howto for Ventrilo is found on this page: [http://appdb.winehq.org/appview.php?iVersionId=3936](http://appdb.winehq.org/appview.php?iVersionId=3936)

This howto solves all the problems you guys talk about, except the robot voice thing.

The hack for getting around the push-to-talk bug is a bit hard for newbies IMO though.

---

### Post by willskills on 2007-04-24
Just a tip guys - if you are struggling to get sound from Ventrilo & WoW at the same time, you might need to do the following if you are using a usb headset (or just have a rubbish mixer on your soundcard)

Now, I am making some assumptions (you have installed WINE, Ventrilo and aoss) - if you haven't and need some help - pm me :)

Now to the Ventrilo config!

Firstly, type 'winecfg' in a terminal, and you'll get the wine config, click the audio tab. In here, make sure that OSS and Esound are both "ticked". Close winecfg.

Now open up Ventrilo, click on setup, and make sure that your Input and Output are set to ESound.

Now, run Ventrilo first; aoss wine /path_to_vent/ventirlo.exe

then run whatever game you want, for me, it would be WoW, so; aoss wine /path_to_wow/WoW.exe

Please post back if this helps you! (I seem to be the only person that had to do this, to get sound working in Vent & WoW) - I think it might be down to the fact that the mixer my usb headset (plantronics) has, and it not well supported, but I don't know enough to verify that :)

---

### Post by bluewagon on 2007-04-25
in winecfg, i dont have an esound option, just ALSA, OSS, and NAS

---

### Post by Tellisk on 2007-05-21
Ok. I set them to Esound. Now it seems I can talk in Ventrilo. The icon next to my name turns green when I hold my ptt key and say "Can you hear me?" But it seems when others in the channel speak, Ventrilo freezes.

---

### Post by FragMonkey on 2007-05-21
I get the same freezing problem...

---

### Post by Tellisk on 2007-05-22
I'm thinking what I might do tomorrow, is just uninstall Ventrilo and start from scratch settings. I probably changed something that helped at one point until I changed something that broke Ventrilo when in conjunction with the first change. Going back to default and following one of these guides might just be all I need.

---

