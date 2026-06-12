---
title: "playing streaming asx files?"
date: 2005-10-02
forum: Desktop Environments
---

### Post by jrib on 2005-10-02
Hey everybody, I've been using Ubuntu for about a month now and am enjoying it a lot.  Right now though I am on windows because I couldn't get a streaming asx file to play correctly.  Hopefully someone can help me or give me some advice.

The stream I am trying to play is: [mms://rdp.oninet.pt/antena1]("mms://rdp.oninet.pt/antena1") (Feel free to try it, it is a news station in Portugal.  You can also try changing the mms:// to [http://,](http://,) they have that setup and both work in windows.).  I have tried totem-gstreamer, totem-xine, rythmbox, mplayer, xine, xmms (admittedly not VLC but I got tired of installing things).

If anyone can actually play that [link]("mms://rdp.oninet.pt/antena1") please let me know what you use.  I don't mind figuring it out but I'm out of ideas and have searched everywhere.  Or if you know for a fact that this is currently impossible/extremely hard to play let me know too.  Thanks in advance.

---

### Post by cbudden on 2005-10-02
Sorry, cannot get it to play in anything, including realplayer

---

### Post by Cloud[01] on 2005-10-05
Use Totem Movie Player:

Applications -> Sound & Video -> Totem Movie Player

then: Movie -> Open Location

Anyway this is not the "xxx.asx" usrl but the one you get inside of it using an editor, just put in Totem the "xxx.asx" link and it will play it :) (hopefully!)

ciop ciop

---

### Post by jrib on 2005-10-05
[QUOTE='Cloud[01]']
Anyway this is not the "xxx.asx" usrl but the one you get inside of it using an editor, just put in Totem the "xxx.asx" link and it will play it :) (hopefully!)
[/QUOTE]

You're right it isn't actually ".asx".  However, I can wget the file: ```
$wget http://rdp.oninet.pt/antena1
```

What I see inside looks like: ```
 [Reference]

Ref1=http://rdp.oninet.pt/antena1?MSWMExt=.asf

Ref2=http://10.1.10.80:80/antena1?MSWMExt=.asf
```

This is how the stream is linked from the site.  I didn't look inside of a .asx and grab that link.  I just figured it was .asx format... altough it may not actually be.  I'll try to do some googling on that later and maybe create a .asx from the actual streaming file.

What is strange is that totem and some other players actually play the file.  I hear pieces for a few seconds.  It sounds like they play a couple of seconds and then buffer for a minute.  It may just be a problem with proper buffering.

Thanks for the suggestion.

---

### Post by dbrower256 on 2006-08-21
I've been trying to get Totem to play this file: [http://byutv.org/streaming/byutv250b.asx](http://byutv.org/streaming/byutv250b.asx).  I get an error saying "no uri handler implemented for "mms".

---

### Post by jrib on 2006-08-26
> **dbrower256 said:**
> I've been trying to get Totem to play this file: [http://byutv.org/streaming/byutv250b.asx](http://byutv.org/streaming/byutv250b.asx).  I get an error saying "no uri handler implemented for "mms".

I've found that mplayer can play the most type of files.  I use it for every media file I use except dvd's because it doesn't do dvd menus, but xine handles that well.

mplayer is in the multiverse repository so be sure to have that enabled so you can install it if you don't already have it.

I can play your file, [http://byutv.org/streaming/byutv250b.asx](http://byutv.org/streaming/byutv250b.asx), with mplayer:
```
mplayer -playlist http://byutv.org/streaming/byutv250b.asx
```

Give it a try and see if it works for you.

By the way, totem can play the file for me as well.  I use totem-xine so that may be why.  Also make sure you have all the multimedia codecs that help.ubuntu.com manual and the restricted formats wiki page discuss.

---

### Post by chudder on 2007-01-07
I can't play this link, no player does, they all freeze, including kaffiene, mplayer, realplayer, totem, xmms, vlc, rhythmbox (entering it as a radio stream), xine and I just can't get to it to play.  I use MediaConnectivity and it shows the file as [http://www.lds.org/ref/scriptures/bm/4_ne/1.asx](http://www.lds.org/ref/scriptures/bm/4_ne/1.asx) but then if I have player like VLC attempt to play it give in the lower right corner, _**mms://stream.lds.org/scriptures/bm/4_ne/1.wma**_ so I hope that helps give enough information, if not the URL is [http://scriptures.lds.org/en/4_ne/1]("http://scriptures.lds.org/en/4_ne/1") and then click on "Listen" which is in the upper left corner of the web page.  

Thank you to anyone who can solve this mystery.  
Chud

---

### Post by jrib on 2007-01-07
> **chudder said:**
> I can't play this link, no player does, they all freeze, including kaffiene, mplayer, realplayer, totem, xmms, vlc, rhythmbox (entering it as a radio stream), xine and I just can't get to it to play.  I use MediaConnectivity and it shows the file as [http://www.lds.org/ref/scriptures/bm/4_ne/1.asx](http://www.lds.org/ref/scriptures/bm/4_ne/1.asx) but then if I have player like VLC attempt to play it give in the lower right corner, _**mms://stream.lds.org/scriptures/bm/4_ne/1.wma**_ so I hope that helps give enough information, if not the URL is [http://scriptures.lds.org/en/4_ne/1]("http://scriptures.lds.org/en/4_ne/1") and then click on "Listen" which is in the upper left corner of the web page.  

Thank you to anyone who can solve this mystery.  
Chud

do you know if it works on windows?  I can't get it to work either.

---

### Post by tpg on 2007-01-07
If I click the link in Firefox, it prompts me to open totem. If a click 'Launch Application', the stream opens and works! I have totem, totem-mozilla, and totem-xine installed (as well as libxine-extracodecs). This is in fully up-to date Edgy. Hope this helps.:)

---

### Post by GranpaDan on 2008-05-24
> **chudder said:**
> I can't play this link, no player does, they all freeze, including kaffiene, mplayer, realplayer, totem, xmms, vlc, rhythmbox (entering it as a radio stream), xine and I just can't get to it to play.  I use MediaConnectivity and it shows the file as [http://www.lds.org/ref/scriptures/bm/4_ne/1.asx](http://www.lds.org/ref/scriptures/bm/4_ne/1.asx) but then if I have player like VLC attempt to play it give in the lower right corner, _**mms://stream.lds.org/scriptures/bm/4_ne/1.wma**_ so I hope that helps give enough information, if not the URL is [http://scriptures.lds.org/en/4_ne/1]("http://scriptures.lds.org/en/4_ne/1") and then click on "Listen" which is in the upper left corner of the web page.  

Thank you to anyone who can solve this mystery.  
Chud

I just clicked on the first link in your post, and the audio for the scripture started playing automatically (after a brief time for downloading the cache). I am using hardy, and have gone through the steps recommended in reassuringlyoffensives sticky at the beginning of the mutimedia and video section of the forum.

You might check that out.

---

### Post by chudder on 2008-05-24
> **GranpaDan said:**
> I just clicked on the first link in your post, and the audio for the scripture started playing automatically (after a brief time for downloading the cache). I am using hardy, and have gone through the steps recommended in reassuringlyoffensives sticky at the beginning of the mutimedia and video section of the forum.

You might check that out.

I did get it working, thanx!

---

