---
title: "RealAudio player/plugin"
date: 2005-01-01
forum: Desktop Environments
---

### Post by dunric on 2005-01-01
Does exist in Ubuntu repositories some package with RealAudio streams support ?

Thx

---

### Post by bob k on 2005-01-01
[QUOTE=dunric]Does exist in Ubuntu repositories some package with RealAudio streams support ?

Thx[/QUOTE]
 You'll have to get it from real audio. DO NOT get the real audio version 10 gold. You will have to Google for real audio 8. I had the address but can't find it right now.

You have to use RA 8 because they changed the streaming codec and nobody is using it. If you already have RA 10 installed you can install RA 8 with no problems. just select the one you want to use from the MIME menu.

Been there and done that
Bob

---

### Post by DougInKY on 2005-01-01
[QUOTE=bob k]You'll have to get it from real audio. DO NOT get the real audio version 10 gold. You will have to Google for real audio 8. I had the address but can't find it right now.

You have to use RA 8 because they changed the streaming codec and nobody is using it. If you already have RA 10 installed you can install RA 8 with no problems. just select the one you want to use from the MIME menu.

Been there and done that
Bob[/QUOTE]

This is interesting. I have been using Real 10 since it went gold on several computers (and different distos) with not a stumble one. I like it a lot. Can you point me to a site that plays in RA 8 but not in RA 10?

Thanks,
Doug

---

### Post by Perfect Storm on 2005-01-01
So far I havn't any trouble with gold 10, both on my Mandrake and ubuntu system, can we get an explaination, thank you!

---

### Post by wolovids on 2005-01-01
I wouldn't say any problems.   :D

If you do not use [ESD and don't need software mixing](https://helixcommunity.org/forum/message.php?msg_id=2318), then RealPlayer 10 should work decent on Ubuntu.  

 And then there's the [swf plugin issue](https://helixcommunity.org/forum/forum.php?thread_id=906&forum_id=7) with debian systems.

---

### Post by LongTooth on 2005-01-01
If all who install Ubuntu for the first time would avail themselves of the "HOWTO: Tweaking Ubuntu after your first installation" thread,  [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)  they would fine how to add Flash, Java and Xmms. Also how to install Nvidia and ATI drivers, configure Rhythmebox for MP3. Also how to install Realplayer and many other programs one would need to make their Ubuntu system preform like they want. It's the first HowTo I visit went I installed Ubuntu. Others have added their HowTo's further into the thread. So don't stop after the initial post. Many things there that will make Ubuntu a pleasure to run. 

I would also recommend the HowTo: Ubuntu Multimedia. [http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)  Again, read through all of the thread. Several problems crop up but within the same thread, solutions are given. Such as:

"... MPlayer
-------
It's time to grab all of the packages needed to install MPlayer...

... $ sudo apt-get install libpng-dev...

Further into the thread someone will state this last command will not install. An error message will display. the solution is:

"... $ sudo apt-get install libpng12-dev...

So read all of the thread. Did I mention one should read ALL of the thread? I think I did.

One other HowTo I would also recommend is the HOWTO: Make your fonts smooth enough to drool over. At [http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456)


Happy Ubuntu hunting. Its fun.

P.S. I too have never had any problems with RealPlayer 10.

---

### Post by dunric on 2005-01-01
Gr8. Thx much for your hints, guys  :)

---

### Post by DougInKY on 2005-01-01
<<< One other HowTo I would also recommend is the HOWTO: Make your fonts smooth enough to drool over. At [http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456) >>>

Thanks LongTooth for that font post. Somehow I had missed seeing it in my reading. Oh, it works just as good as you said. Love my new look. =D> 

Doug

---

### Post by bob k on 2005-01-01
[QUOTE=DougInKY]This is interesting. I have been using Real 10 since it went gold on several computers (and different distos) with not a stumble one. I like it a lot. Can you point me to a site that plays in RA 8 but not in RA 10?

Thanks,
Doug[/QUOTE]

I have been to most of the radio sites that I listen to and none of them will work RA 10 gold. Here is one or two that I listen to on a regular basis.

[http://www.jazz.fm/](http://www.jazz.fm/)
[http://www.khyi.com](http://www.khyi.com)  they call this americona

---

### Post by bob k on 2005-01-01
I really like the icon theme on desktop 1. what are you using for your windows manager.

Sorry this post was for AI. Workin on a new system and tryn fix the little problems.

---

### Post by Perfect Storm on 2005-01-02
It's based on TiCons icon theme but must of the icons I manually added.

---

### Post by DougInKY on 2005-01-03
[QUOTE=bob k]I have been to most of the radio sites that I listen to and none of them will work RA 10 gold. Here is one or two that I listen to on a regular basis.

[http://www.jazz.fm/](http://www.jazz.fm/)
[http://www.khyi.com](http://www.khyi.com)  they call this americona[/QUOTE]

Thanks for the answer Bob K. When I went to view them the first said it was using an obselete codec and wouldn't play. I suspect from your post it does play in RA 8.

The second site wouldn't load either but appears to be set to use the windows media player from what I could see. It is using a java script that won't play on my system to try to start the stream.

These are the first two sites I have seen not work. Thanks for the heads up. If I run into many that I am trying to view, I just might roll back to RA 8 too but so far the sites I listen to I either use RA 10 or XMMS without problems. It is nice to know that there are sites that use RA codecs that won't play.

Doug

---

### Post by DougInKY on 2005-01-03
[QUOTE=bob k]I have been to most of the radio sites that I listen to and none of them will work RA 10 gold. Here is one or two that I listen to on a regular basis.

[http://www.jazz.fm/](http://www.jazz.fm/)
[http://www.khyi.com](http://www.khyi.com)  they call this americona[/QUOTE]

Okay, I couldn't stand not knowing why these sites wouldn't play for me. I rebooted into Windows XP and went to look at the sites again.

Jazz FM uses the RA 3 codec. Now that is one old version of RA. It is interesting that RA 10 in Windows went out to the Real site and downloaded that old codec. Maybe we need to be bugging the people working on the code for linux to backport the old codecs for Linux too?

The second site opens a window in Firefox and starts Window Media Player so this not playing for me in RA 10 is no big surprise. If I had the windows codecs installed and had Mplayer I suspect that I might have been able to listen to this site under Ubuntu. I don't know as I don't have the windows codecs or Mplayer running on my machine.

Doug

---

### Post by macewan on 2005-01-16
[QUOTE=DougInKY]Okay, I couldn't stand not knowing why these sites wouldn't play for me. I rebooted into Windows XP and went to look at the sites again.

Jazz FM uses the RA 3 codec. Now that is one old version of RA. It is interesting that RA 10 in Windows went out to the Real site and downloaded that old codec. Maybe we need to be bugging the people working on the code for linux to backport the old codecs for Linux too?

The second site opens a window in Firefox and starts Window Media Player so this not playing for me in RA 10 is no big surprise. If I had the windows codecs installed and had Mplayer I suspect that I might have been able to listen to this site under Ubuntu. I don't know as I don't have the windows codecs or Mplayer running on my machine.

Doug[/QUOTE]
 mms://wms9.moontaxi.net/moontaxi_CA34EEE0-1881-46A1-8974-8A38C6941223_unicast


If you have totem-xine & the right plugins this above link will work


The stream listed below is for the Jazz channel. Thanks for pointing me to that site  
 :D 

mms://wms9.moontaxi.net/moontaxi_C78DFA85-1880-4242-A535-215D9A3795A9_unicast

While remembering this is with totem-xine - open totem > select movie > open location and then paste the above link.

---

