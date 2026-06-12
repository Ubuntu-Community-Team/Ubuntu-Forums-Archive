---
title: "TV Streaming program"
date: 2006-06-13
forum: Desktop Environments
---

### Post by jstreed on 2006-06-13
I'm looking for the linux equivalent of tvuplayer ([http://www.google.com/search?q=tvuplayer&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/search?q=tvuplayer&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)) 

I'd like to be able to stream some television shows (namely the world cup) through linux, but right now I'm stuck in windows.  Any ideas?

---

### Post by lazyron on 2006-07-08
/bump

Would like to see this too, or info on getting it working under wine.

---

### Post by JamesWilson on 2006-08-21
Please, someone, work on getting TVUPlayer to work for us!

I've tried under wine, crossover, and cedega. No go. :(

---

### Post by Lem on 2006-08-21
MythTV uses VLC to stream in one of it's plug-ins, so I'm sure it's possible.

---

### Post by moon_dog on 2006-09-13
/bump

i'd like to see this as well.  is there any program for linux that does what tvuplayer does?  i've got democracytv, but it doesn't do what tvuplayer does

---

### Post by sledhead45 on 2006-10-02
bump

tvuplayer in ubuntu would be sweet!

---

### Post by someguyouknow on 2006-10-02
<----also interested.

---

### Post by someguyouknow on 2006-10-03
I havent found a solution but i found this
[http://www.lifehacker.com/software/bittorrent/hack-attack-get-your-tv-season-pass-with-democracy-204057.php](http://www.lifehacker.com/software/bittorrent/hack-attack-get-your-tv-season-pass-with-democracy-204057.php)

---

### Post by fragos on 2006-10-03
I have a number of friend that use MythTV with a PVR 150/250/350 card.  Those cards have hardware encoding and use the ivtv driver instead of bttv.  Your TV card might make a difference in what you can do.  There are MythTV HOWTOs on this forum.

---

### Post by umomma on 2006-10-06
I was able to get TVUPlayer to work on Edgy (wine version 0.9.22). I first installed wine then before running it (did not generate a .wine) I ran the fantastic ies4linux script. Using this environment I simply installed then ran TVU. It works 'ok' on my aging laptop, but there is one big issue. Once the video starts the rest of my screen will turn black (stop redrawing). Anyone have an idea how to fix this? You will also have to set the WINEPREFIX environment variable to point to the ie6 install before you start installing TVUPlayer.

---

### Post by Naegling23 on 2006-10-06
there is a program called sopcast that has a linux client.  I tried installing it, but I couldnt get it to work.  If anyone wants to take a look at it, that would be pretty neat.  It has my flyers games, and I would love to be able to use it, I just couldnt figure it out.

---

### Post by t3ddyg on 2006-10-29
check out this post for sopcast info:
[http://ubuntuforums.org/showthread.php?t=258049](http://ubuntuforums.org/showthread.php?t=258049)

---

### Post by gardara on 2006-12-30
I have been trying to get tvu player to work, I am able to install it with wine but when I try to run the program I can start the program but I can't get past the auto-updater program that starts up... does anyone have a solution to make the auto-updater work or if there is a way I can disable this auto-updater...?

---

### Post by FattyCNS on 2007-01-16
.

---

### Post by utopial on 2007-06-01
there r several things that really need developing for linux and this is one of them

tvuplayer is taking over as the main tv streamer. sopcast does have a linux version but not all the channels

is there any work being done to develop a solution for this?

---

### Post by gregturn on 2007-06-01
I use MythTV. Go read about the stuff at [http://wiki.mythtv.org](http://wiki.mythtv.org). Warning: it has some complexity to it, which means it takes more than 2 minutes to setup. But that is because this is the BEST in open source PVR software, so it covers LOTS of things, and supports MANY configurations. (Okay, maybe I'm a little biased after using it for 3 years). :popcorn:

---

### Post by lucazade on 2007-06-01
Try this deb of gsopcast, it works well for me ..  :popcorn:

---

### Post by utopial on 2007-06-21
there is a website called livefooty.org
it streams live football (soccer) from all over the world. it's very popular and uses sopcast, tvants, ppstream, tvuplayer and a couple of other players. it will show a match, u click on the link and it opens up the match within the browser (ie using the plugin and navigating to the right channel). when i had XP, i installed the plugins for these programs in IE6 and it worked well. it never worked in firefox cause firefox doesnt seem to have plugins for these programs.

is there going to be a solution for this or is firefox going to lag behind in the streaming media department which is pretty much the fastest growing area in IT at the moment??

---

### Post by jjgomera on 2007-07-26
tvuplayer have already a native version for linux, but only for broadcasters, not for viewers:confused:

[http://pages.tvunetworks.com/downloads/broadcast.html](http://pages.tvunetworks.com/downloads/broadcast.html)

Tvants is easy to use in linux with wine

Both have deb packages easy to install: [http://ubuntuforums.org/showthread.php?t=366123](http://ubuntuforums.org/showthread.php?t=366123)

---

### Post by frecon on 2008-05-04
[HOWTO: TVUPlayer on Linux - watching and recording (Ubuntu 7.10)](http://forum.tvunetworks.com/forum/posts/list/127619.page)

I haven't tried it myself so i don't know if it'll work.

Otherwise, you have TVAnts and Sopcast. Check [www.myp2p.eu](www.myp2p.eu) to see what's on.

[SIZE="4"]Installation of TVAnts[/SIZE]
Install wine
```
sudo apt-get install wine
```

Download TVAnts from [http://www.tvants.com/download/tvantssetup.exe](http://www.tvants.com/download/tvantssetup.exe)

Then run the setup. (It should start automatically with wine)

When you start a stream you will get a message ie. "Failed to open channel http://localhost:16900/1.asf..." Open VLC and select File > Open networkstream... and put the link you got from the error message (here [http://localhost:16900/1.asf](http://localhost:16900/1.asf)) under http.
[SIZE="4"]
Installation of Sopcast[/SIZE]
Follow this guide: [http://ubuntuforums.org/showthread.php?t=728683](http://ubuntuforums.org/showthread.php?t=728683)

---

