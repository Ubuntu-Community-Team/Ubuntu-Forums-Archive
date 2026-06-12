---
title: "windows media player on wine"
date: 2010-06-20
forum: Desktop Environments
---

### Post by mIXpRo on 2010-06-20
hii, 
i've installed windwos media player on wine, 
i followed the instructions on winehq.org , and i also tried it with winetricks ,
the software runs normally , but when change the tab say from Library to now playing it shows an error , see attachment 

any ideas , thnx in advance

---

### Post by ronnielsen1 on 2010-06-20
Not w/o knowing which version of windows media center that is. 

Have you tried any of the following?

[http://en.wikipedia.org/wiki/Category%3ALinux_media_players](http://en.wikipedia.org/wiki/Category%3ALinux_media_players)

---

### Post by mIXpRo on 2010-06-20
i have wine 1.2-rc4 , and i tried to install wmp 10 .

i need windows media player for a reason , i need to stream with mms protocol some lectures with 1.5x playback speed , this i can't do with any other player .

---

### Post by MooPi on 2010-06-20
Try Virtualbox instead of wine. My Windows XP virtual handles MediaPlayer fine.
[http://dl.dropbox.com/u/5209151/thisNthat/WmPlayer.png](http://dl.dropbox.com/u/5209151/thisNthat/WmPlayer.png)

---

### Post by mIXpRo on 2010-06-20
i've tried once virtualBox , but when streaming only the sound plays without the video , 
what could be the problem ?

---

### Post by ronnielsen1 on 2010-06-21
[http://appdb.winehq.org/appview.php?iVersionId=3212](http://appdb.winehq.org/appview.php?iVersionId=3212)

> You have to run the following commands to get it to install, don't dl from m$'s website but run these commands to get it to install with extra dll's etc..
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks wmp10
(don't sudo it)


I still recommend a native linux player though. There's tons to choose from

---

### Post by mIXpRo on 2010-06-21
> **ronnielsen1 said:**
> 

I still recommend a native linux player though. There's tons to choose from

i've tried vlc , but mms didn't work so i had to change the steaming type to rtsp , which didn't support speeding the playback .

---

### Post by lkjoel on 2010-06-21
Try PlayonLinux. That is sorta like winetricks and wine-doors.

---

