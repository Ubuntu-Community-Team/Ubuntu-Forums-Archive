---
title: "xmms error &quot;Couldn't open audio&quot;"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Stambo00 on 2005-11-05
In Hoary I used xmms as my favourite music player. Unfortunately in Breezy I can use every single music application except xmms as it gives me the error of :

"Couldn't open audio.

Please check that:

Your soundcard is configured properly.
You have the correct output plugin selected.
No other program is blocking the soundcard."

As far as i can tell no other program is blocking the soundcard, and I am unsure what to do for the other two. Any help would be greatly appreciated.

ps. I'm trying to play mp3 files which I have the codecs installed for, as it works for my other media players

---

### Post by Ampersand on 2005-11-05
Right click somewhere in the xmms main window, and go to properties, change the output to something else (usually ALSA) and try again.

---

### Post by Stambo00 on 2005-11-05
Thankyou a great deal, it worked. So simple really.

---

### Post by beerorkid on 2005-11-15
yeah that was silly easy.  Thanks.  I freaked out for a few days.

---

### Post by orsula on 2006-01-05
I read this thread since I can't listen to audio through xmms. I changed to every output possible but still no dice. For that matter, I can't play music on any of the players, even the simple 'CD player'. System sound works because I get the chime at startup and when I close windows I get a little 'bip'. What might be the issue?...
thanks

---

### Post by Qrk on 2006-01-06
There could be several issues... you'll have to give a little more information.

If you never were given an error message is could be something simple like your volume was muted. Double click on the volume panel applet, and you can change the volume for the different settings. 

It might also be a problem with ALSA... try disabling system sounds. A friend of mine has a similar problen... I had it with ESD in hoary.

Sometimes I go through too much trouble only to realize that a simple fix would be better. I spent several hours or so trying to speed up open office before reading a post that just said to disable Java.

---

### Post by twizler on 2007-10-20
:guitar:THANK YOU IT WORKED FOR ME IN UBUNTU 7.1 -- now i can listen to digitally  imported.fm online radio!!! THANK YOU AGAIN!!!! ! EASY WAY TO OPTIONS 
 [COLOR="Red"]XMMS -- press ( Ctrl + P ) --  edit the output Plugin drop box to ALSA [/COLOR]
[[IMG]http://img89.imageshack.us/img89/7682/xmmsalsabo6.th.png[/IMG]](http://img89.imageshack.us/my.php?image=xmmsalsabo6.png)

---

