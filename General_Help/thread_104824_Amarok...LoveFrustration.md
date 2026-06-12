---
title: "Amarok...Love/Frustration"
date: 2005-12-16
forum: General Help
---

### Post by frost_ad on 2005-12-16
I love the idea of amarok. It is one of the best music players/organizers that I have seen. Plus it has podcast support, Plus it works with iPods. I love a lot of the other stuff too, suggested songs, lyric and artist look up etc. **BUT I CAN'T USE IT**

I'm playing mp3 files off of a shared FAT32 partition. It seems to play some songs ok, but others will just make it crash completely. I really want amarok to work, but it's just unusable as is. I've tried different engines in Gnome and KDE and still have the same problems.

Does anyone have any suggestions? I've tried some things suggested on other threads but nothing has helped so far.

---

### Post by cdhotfire on 2005-12-17
What is the problem excatly?

Try running amarok on terminal and see what pops up.

---

### Post by DaMasta on 2005-12-17
Yeah, tell us the error when it crashes. I run amarok from a fat32 drive and it works fine.

---

### Post by jrib on 2005-12-17
[QUOTE=frost_ad]I love the idea of amarok. It is one of the best music players/organizers that I have seen. Plus it has podcast support, Plus it works with iPods. I love a lot of the other stuff too, suggested songs, lyric and artist look up etc. **BUT I CAN'T USE IT**

I'm playing mp3 files off of a shared FAT32 partition. It seems to play some songs ok, but others will just make it crash completely. I really want amarok to work, but it's just unusable as is. I've tried different engines in Gnome and KDE and still have the same problems.

Does anyone have any suggestions? I've tried some things suggested on other threads but nothing has helped so far.[/QUOTE]

Okay, actually I just discovered amarok today and was very impressed as well.  Like you, I was disappointed when it started crashing.  After browsing through the amarok wiki, I saw that they had some instrucitons on how to use 'gdb- The GNU Debugger' to get to the root of the problem.  I also noticed that they said crashes were usually due to the taglib library.  

Well, I had this one song that i could use to repeatedly crash amarok.  I ran amarok through gdb and, sure enough, when I tried to play that same song amarok froze (gdb stops it from crashing and just freezes it).  When I saw the the output from the 'bt' command in gdb, it showed some reference to the taglib libraries.  Okay, great....  Well I thought I could try editing the mp3tag (I used a program called cowbell which is in the repos) and see if amarok would stop complaining.  I changed all of the spaces to underscores and tried again.  And hey! amarok didn't crash.  I went back and changed the underscores back to spaces in cowbell.  And again, amarok played the song fine.  So it may have just needed to be resaved.

Anyway, basically edit the mp3tag for the songs that are causing amarok to crash using a program like cowbell and restart amarok.  Maybe you're having the same problem.  That's the only type of crash I have experienced anyhow.  Hope it works for you too.

[e] I just used cowbell because it's the first one I found, but if someone knows of a nicer mp3tag editor (maybe one that can act recursively through a folder and reformat tags would be nice) I would be glad if you shared your knowledge :)

---

### Post by frost_ad on 2005-12-18
I'll try renaming that song and see if it works and report back. I think iTunes will figure out the change. Unfortunately I need windows for some software for college, and you can't study without music!

*EDIT*

Well, I decided to just use Rythmbox for playback. I'm using yamipod to transfer and get my podcasts. I'm satisfied with this solution for now. I will check back in with amarok in the future though, it's got some pretty sweet features.

---

### Post by souled on 2005-12-18
[QUOTE=_jason]
[e] I just used cowbell because it's the first one I found, but if someone knows of a nicer mp3tag editor (maybe one that can act recursively through a folder and reformat tags would be nice) I would be glad if you shared your knowledge :)[/QUOTE]

Easytag is a pretty good tagging program. Also in the repos.

---

### Post by jrib on 2005-12-18
[QUOTE=souled]Easytag is a pretty good tagging program. Also in the repos.[/QUOTE]

Just installed it.  Looks alot better than cowbell, thanks!

---

### Post by Rackerz on 2005-12-18
I use amarok, i just installed it actually. It works perfectly fine for me. No problems with mp3s, wma's etc.

---

### Post by Vulpus on 2006-01-03
[QUOTE=frost_ad]I love the idea of amarok. It is one of the best music players/organizers that I have seen. Plus it has podcast support, Plus it works with iPods. I love a lot of the other stuff too, suggested songs, lyric and artist look up etc. **BUT I CAN'T USE IT**

I'm playing mp3 files off of a shared FAT32 partition. It seems to play some songs ok, but others will just make it crash completely. I really want amarok to work, but it's just unusable as is. I've tried different engines in Gnome and KDE and still have the same problems.

Does anyone have any suggestions? I've tried some things suggested on other threads but nothing has helped so far.[/QUOTE]

I too have had similar problems with amaroK after it working fine for ages.  To cut a **_VERY_** long story short the problem can apparently be cured by upgrading your TagLib to version 1.4.  (The current Ubuntu version is 1.3.??).  I havent actually confirmed this myself as I used an alternative solution of removing the offending MP3s.  See here [http://developer.kde.org/~wheeler/taglib.html](http://developer.kde.org/~wheeler/taglib.html)

You should also make sure you have the latest version of amaroK (1.3.7).  again the Ubuntu version is behind on this and you need to download the Kubuntu version.

---

