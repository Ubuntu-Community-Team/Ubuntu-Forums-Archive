---
title: "Starsiege: TRIBES having trouble"
date: 2006-08-19
forum: Gaming &amp; Leisure
---

### Post by SZF2001 on 2006-08-19
I'm trying to run this game right? Got in installed through wine and everything is going fine. After the setup I launched the game given the option to do so.

But when I wanted to play again something happened. It would not open.

I tried it through the terminal and this is all that happened:


```
coleman@colecomp:~$ sudo wine "C:\Dynamix\TRIBES\tribes.exe"
Password: 
Killed
```

Take note that I left this terminal running all through the night. I checked it about 3 in the morning and it hadn't said killed, even when I started it at 10 that night before.

Any ideas? I'd like to run the game. It's the only one that will run on this crappy computer.

---

### Post by osomer on 2006-10-20
2 months later...I get the exact same error (although I did not attempt to run tribes when it prompted me from the start).

I have look through various webpages and nobody else seems to be having this problem, so did you ever find a solution or has anybody got a fix for this?

---

### Post by nutz on 2007-06-25
I have it installed and it runs flawlessly for me but did require a bit of setup for the sound. When the game first installs the sound doesn't work but after playing with the settings in Wine I got the game to work with DirectSound. I have the GSI version of TRIBES updated to 1.11 and Wine 0.9.39. All features of the game work perfectly and the performance is every bit as good as Windows.

Seriously badass game!

---

### Post by nutz on 2007-06-25
[http://www.planettribes.com/tribes/tribes_top50.shtml](http://www.planettribes.com/tribes/tribes_top50.shtml)

---

### Post by JohnGalt on 2007-06-27
Years ago I tried and could never get it to work. Good to know it does. I'll be putting it back on. Too bad the community is so small for it anymore.

---

### Post by nutz on 2007-06-28
> **JohnGalt said:**
> Years ago I tried and could never get it to work. Good to know it does. I'll be putting it back on. Too bad the community is so small for it anymore.

That isn't true. On any given day there are tons of good games going. You can download the GSI version and update it to 1.11.

---

### Post by SZF2001 on 2007-06-28
Oh man, that one weird server, if you ever see it, something like "SAMARI + something" is a fun server.

---

### Post by nutz on 2007-06-29
My favorite is Shifter_V1G...

---

### Post by OrbJinzo on 2007-06-29
mmm tribes players. 

You need to make sure you have a ClientPrefs.cs file or the game wont run dont ask me why it just wont.

stick that file i included in this post in your tribes config file.  This will get you up and running.

---

### Post by nutz on 2007-06-29
> **OrbJinzo said:**
> mmm tribes players. 

You need to make sure you have a ClientPrefs.cs file or the game wont run dont ask me why it just wont.

stick that file i included in this post in your tribes config file.  This will get you up and running.

That is not correct OrbJinzo. This file is by default included with the installation. It is where the game stores settings and player preferences by default and that is why the game will not run without it. Nobody should need this config file since they will already have one under the default install. And the one included with their install will be setup properly according to their preferences.

You can either make configuration changes to this file directly or from within the game but all the game is doing is storing it to this file. So the cleanest and easiest way for me is to just edit the file directly. It follows a very similar format to the config files for Quake engines.

For instance these lines either enable or disable player shadows. This is the shadow that each player casts...

$pref::shadowDetailMask = "0";
$pref::shadowDetailScale = "0.000000";

0 = disabled and 1 = enabled.

Player shadows are disabled by default so to enable them you just change those two lines so they look like this...

$pref::shadowDetailMask = "1";
$pref::shadowDetailScale = "1.000000";

This file is also very useful if you have a widescreen LCD. The game will not allow a lot of the widescreen resolutions such as 1680x1050 since widescreen displays were not very common when thie game was released. So in order to get the resolutions the game will not allow you to select you would have to edit this config file directly and add that value. That would look like this...

$pref::VideoFullScreenRes = "1680x1050";

---

### Post by nutz on 2007-06-29
I would also like to mention the graphics rendering through Wine. So far it plays the game vastly better than Windows ever did. This game did not originally have OpenGL support, instead it has software and 3dfx for it's rendering options. But after 3dfx went away they realised OpenGL support would now be required so they added it in one of their updates. So if you want OpenGL support you will have to update the game to at least 1.8 since that is when they added OpenGL. 1.11 is the lastest version...

Anyway, back to the graphics. Since they added OpenGL in a somewhat hack fashion it never did perform or look nearly as good as when it ran under 3dfx. I tried this game with multiple different card and configurations and the OpenGL support was just never very good. But now for some reason running under Wine all these problems are solved. The graphics are rendered perfectly with no errors that I have seen thus far and the speed is even better than Windows. I find the game is much more responsive and the graphics are smoother in the higher resolutions.

---

### Post by OrbJinzo on 2007-06-30
I would like to say the fileplanet version which most people after you install does not come with this file nor will it excute with out it.  GSI is fileplanet man.

---

### Post by nutz on 2007-06-30
> **OrbJinzo said:**
> I would like to say the fileplanet version which most people after you install does not come with this file nor will it execute with out it.  GSI is fileplanet man.


That's funny; I just downloaded and installed that exact same version and from the same place too! But mine has that config file in it exactly like it should. Why would they have people download a broken game? 

This file is required regardless of the platform it runs on...

And no GSI is not just fileplanet if that was your thought. It was a free promotional version that they released right before the newer sequel to the game came out. Their idea was to build hype by letting people have the current version free so they could play without limitations and get hooked then when the new one comes out hopefully buy it! It worked...

fileplanet just happens to be one of many places you can download the GSI version from. Back in the day when it was first released almost every major download site had it available.

I have been playing Tribes since it has existed. I was also one of the original beta testers and had over 500 hours of game time before the actual game was even released. The recorded demos that come with the game are footage of some of the beta test games that Dynamix decided to include with the game. Back then we had to edit and update this file quite frequently...

This is however my first experience with it on Linux. And I must say I am extremely pleased!

---

### Post by OrbJinzo on 2007-07-01
heh ditto ive played since 2000. And i know that a was promiontal offer.

---

### Post by Derkik on 2007-07-10
I can't find a site that has a download for clientprefs.cs and I the download here seems to be unresponsive. I only download something called attachment.php. Also, none of the tribes downloads I have found seem to come with this file.

---

### Post by cogadh on 2007-07-10
> **Derkik said:**
> I can't find a site that has a download for clientprefs.cs and I the download here seems to be unresponsive. I only download something called attachment.php. Also, none of the tribes downloads I have found seem to come with this file.
Don't right-click on the link and do the "Save link as..." option, just left-click on it and use the normal save file dialog. If you do the right-click method, you'll end up saving the attachment.php forum page. If you left-click on it, you'll get a normal download dialog and the option to save a zip file.

---

### Post by nutz on 2007-07-10
> **Derkik said:**
> I can't find a site that has a download for clientprefs.cs and I the download here seems to be unresponsive. I only download something called attachment.php. Also, none of the tribes downloads I have found seem to come with this file.

Every Tribes install comes with this file. It is located in the Config directory. Do not download someone elses copy or your game will not work right.

---

### Post by Derkik on 2007-07-11
Thank you, I finally got the game to run after I got the file. Now it is playing wonderfully.

---

### Post by Azereiah on 2008-06-21
It works really well in WINE except for a few problems...

I am an old Tribes modder, and have found that I can't save map files through the Tribes in-game map editor. I was able to do so in Fedora Core 6, but not Ubuntu 8.04 64bit. Might just be the differences in WINE between now and then, though.

I am also unable to make use of 3ds Max 2.5 in order to make new models for the game on Ubuntu, when Fedora Core 6 worked perfectly.

---

### Post by cogadh on 2008-06-21
Dude, way to resurrect the dead, this thread is almost a year old now. Bringing back dead threads (without cause) is frowned upon on these forums, you might want to avoid doing it in the future.

---

