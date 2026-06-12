---
title: "Is Major League Baseball Out?"
date: 2007-03-15
forum: Gaming &amp; Leisure
---

### Post by NoVista on 2007-03-15
I want my baseball, but even the free videos MLB has available don't play.
The MLB Emblem appears on a black background .. the browser status bar says it's transfering data .. but poof .. nothing.
Also ..  anyone out there getting the MLB audio only package and have it working?
Running Firefox on Edgy with Totem plugins, good assortment of codecs, I think, etc.

Advice and instruction needed for this 4 month old Ubuntu guy who ran away from Vista.

---

### Post by Josey on 2007-03-15
I use easy ubuntu to make sure I have all the codecs i need.  Not sure what you need exactly though.

[http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb](http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb)

---

### Post by NoVista on 2007-03-16
So mlb.com audios and videos and streaming live stuff play for you on Edgy/Firefox?
Can anyone else confirm this?

---

### Post by Josey on 2007-03-16
I'm pretty sure they do... could you link to something that doesn't need a subscription there?

---

### Post by NoVista on 2007-03-16
All the free videos use javascript.
just go to
[http://mlb.com](http://mlb.com)
and click on a baseball news story thats in video.
I don't think they have any free audio stuff to check it with, that's why I'm askling also.

Who can confirm mlb.com works for them with Edgy/Firefox?

---

### Post by yabbadabbadont on 2007-03-16
Well, the video url pointed to a file that ended in .wmv so that would indicate you need the win32codecs.  However, when I tried to load the link, it prompted me to install Flash and there was a swf object embedded within the page...

---

### Post by NoVista on 2007-03-16
Ok, yes, Flash is needed and is installed here and works.
Win32 codecs are installed also.

---

### Post by Josey on 2007-03-17
They work for me.

---

### Post by NoVista on 2007-03-17
Dang !
Ok, at least now I know it's workable.
Looks like I have some  tinkering to do .. ..

---

### Post by dclarion on 2007-03-19
Howja do it?  When I try to get a broadcast, Firefox hands the mms:// URI to Totem, and Totem promptly barfs.  I've got WinBlows-specific things playing in other programs, so if I could just adjust the handler Firefox is using?

---

### Post by mickey2 on 2007-03-20
Ok I signed up just so I could tell you how to get mlb. com audio
LOL
Anway you do need the w32 codes and you also need totem xine from synaptic. It will take out the gstreamer plugins but this worked when I put it in.
I had another page wanted to play wma files embed so I added mimms in synaptic and also big one for it to work was for me, as I am in firefox, the mplayer plugin on THIS page  [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

Hope this gets you going. Also mlb.com, we had to pay for the audio service, have no idea if Any free ones.
Mickey

---

### Post by NoVista on 2007-03-24
Ok, I fixed mlb.com so I can now see the videos.
What I had to do was uninstall totem plugins, mplayer plugins, totem xine.
I then re-installed the mplayer plugin, and presto!

I'll check the audio when I subscribe.

---

### Post by mickey2 on 2007-03-24
glad you got it going.
Enjoy

---

### Post by esposj on 2007-03-26
On Ubuntu Feisty, all you need to do is install mozilla-mplayer.  After that, I opened firefox and went to about:plugins , and saw a conflict between totem and mplayer.  They both wanted the same files.  

To fix this I went to /us/lib/plugins and moved out files *totem* .  I restarted firefox, and gameday audio now works!  Let's go yanks!

---

### Post by dclarion on 2007-03-31
> **esposj said:**
> On Ubuntu Feisty, all you need to do is install mozilla-mplayer.  After that, I opened firefox and went to about:plugins , and saw a conflict between totem and mplayer.  They both wanted the same files.  

To fix this I went to /us/lib/plugins and moved out files *totem* .  I restarted firefox, and gameday audio now works!  Let's go yanks!

I tried this on Edgy, and lo and behold, IT WORKS!!!!!  It's not pretty, but it WORKS!

Kiss kiss love love!

Now I can listen to Nats games!

Kiss love love kiss!

Okay...  I'm all better now.  Thanks.

---

### Post by NoVista on 2007-04-09
Ok, I can now confirm the audio only stuff works too.
Baseball is back !

---

### Post by Josey on 2007-04-09
Glad you got it working. :)

---

