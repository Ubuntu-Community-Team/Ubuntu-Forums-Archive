---
title: "I want to play Marathon"
date: 2008-11-06
forum: Gaming &amp; Leisure
---

### Post by crazyfuturamanoob on 2008-11-06
I want to try out marathon, but can't remember the free version of it, or where to download it.

Someone posted about that game in one of my threads, but can't find that thread anymore. :(

Could you post me a link?

---

### Post by LinuxFox on 2008-11-06
Marathon is freeware, here's an [article]("http://www.insidemacgames.com/news/story.php?ArticleID=10700") confirming the game is freeware.  To play it on Linux, you'll need AlephOne.  Here's the links to help get you started...

Marathon: AlephOne - [http://source.bungie.org/](http://source.bungie.org/)
Gamer's Arena Install guide - [http://gaming.gwos.org/doku.php/guides:32bit:alephone#alephone](http://gaming.gwos.org/doku.php/guides:32bit:alephone#alephone)

---

### Post by crazyfuturamanoob on 2008-11-06
Now I got it installed but can't play because it needs some scenarios.

Where do I get those scenarios and how to install?

---

### Post by LinuxFox on 2008-11-06
> **crazyfuturamanoob said:**
> Now I got it installed but can't play because it needs some scenarios.

Where do I get those scenarios and how to install?Scenarios are found at the AlephOne website. [http://source.bungie.org/get/](http://source.bungie.org/get/)

It's been a while since I installed it on Ubuntu, so I'll remember the best I can.  I remember needing to give read and write permission to the AlephOne folder to my username.  After the folder has permission, I could copy the files under my username.

---

### Post by crazyfuturamanoob on 2008-11-06
EDIT: doublepost due to laag, plz remove

---

### Post by crazyfuturamanoob on 2008-11-06
But how do I install the scenarios? Where do I put the files?

---

### Post by LinuxFox on 2008-11-06
> **crazyfuturamanoob said:**
> But how do I install the scenarios? Where do I put the files?You unzip them and place them in the "/usr/share/AlephOne" directory (or wherever your AlephOne folder is).  I only have one scenario installed, so I don't know about multiple scenarios since I never tried it.

Make sure you give the folder permission to create and delete files, and make your username the owner (by default, the folder owner is "root"), otherwise the scenario won't copy.  This is what I had to do.

Open AlephOne and the game should start.  I hope this helps.

---

### Post by crazyfuturamanoob on 2008-11-07
Ok now it works. But man that game is HARD!! Can't get past the second level. I always die when there come a million enemies shooting at me, when I die from a single hit!

Also, I found that game to be better than some today's games. I was surprised when I noticed that there was fists (not really in many games), secondary and primary fire (not seen so often either), a storyline (that's very rarely in games, or it sucks), shadows, and fogging. Because of the over-used fogging effects, it actually looks cool. Like a dream or something.

This game rules.

---

### Post by LinuxFox on 2008-11-07
> **crazyfuturamanoob said:**
> Ok now it works. But man that game is HARD!! Can't get past the second level. I always die when there come a million enemies shooting at me, when I die from a single hit!

Also, I found that game to be better than some today's games. I was surprised when I noticed that there was fists (not really in many games), secondary and primary fire (not seen so often either), a storyline (that's very rarely in games, or it sucks), shadows, and fogging. Because of the over-used fogging effects, it actually looks cool. Like a dream or something.

This game rules.Cool, I'm glad you got the game working and from the sound of it, enjoying it.

Anyway, happy gaming and have fun. 8)

---

### Post by tkmn on 2008-11-07
> **crazyfuturamanoob said:**
> This game rules.

Indeed it does. :guitar:


My favorite in the trilogy is Marathon 2: Durandal. It has the best maps and is a bit easier than the other games.

---

### Post by crazyfuturamanoob on 2008-11-08
> **crazyfuturamanoob said:**
> Can't get past the second level. I always die when there come a million enemies shooting at me, when I die from a single hit!

Didn't notice I had only 2 hp left :D and I didn't know how to get more health from the healing machines (didn't even know what they do). LoL xD

I also noticed that my self-soldered (old) xbox controller is the best possible thing for playing that game. :)

---

### Post by executorvs on 2009-04-22
I was trying to get this to install on Jaunty and intrepid using the source provided in december. however it keeps failing to install and I don't know how to go about solving this. 

both failures are identical.
I've included most of my terminal output in case that helps.

---

### Post by Am Elder on 2009-05-25
Hi, I realize the question from executorvs is a month old now, but since no one else has responded I'll give it a go.  I've just successfully installed Alephone and Marathon.  

From what I can tell, executorvs, it looks as if you don't have the speex module installed.  The files I found in the in the Ubuntu repositories were under libspeex1 and are maintained by Canonical.

If that doesn't help, you can ask the developer maintaining Aleph One on the [new boards on sourceforge]("http://apps.sourceforge.net/phpbb/marathon/").  (the [story board]("http://forums.bungie.org/story/") is as quiet as the grave these days, and [the pfhorums]("http://ubuntuforums.org/www.pfhorums.com/") seem to be down at the moment)

The install is a little confusing.  But if you follow the direction in the INSTALL.Unix file that comes with the source, you'll get there in the end.  And it's well worth it! [ AlephWiki]("http://source.bungie.org/wiki/index.php/Main_Page") also has [good instructions]("http://source.bungie.org/wiki/index.php/Linux_Build_Instructions").  In one case, the wiki directions sent me off in the wrong direction because they didn't tell me to run **make install**.  On the other hand, the wiki has some information that I didn't see anywhere else.

---

