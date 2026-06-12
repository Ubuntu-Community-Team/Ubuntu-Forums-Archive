---
title: "Windows Media Player"
date: 2006-05-04
forum: Desktop Environments
---

### Post by matthewstory on 2006-05-04
I just ordered MLB Gameday Audio so that I may enjoy streamed radio broadcasts of baseball games over the internet, the only problem is that it doesn't work.  I'm almost positive that it works by opening the windows media player plug-in to a browser and then plays it (i say this because I've accessed it over a windows box with success and this is in fact exactly what it did).  So now my question is whether windows media player will work with WINE, and if it does, can I also set it up to plug-in to my firefox (like it does in windows).  I realize that its absurd that a streaming broadcast depends on a single program, but i'm probably not going to be able to make MLB change their practices, and I really like baseball, so any help would be great.  Thanks.

---

### Post by groggyboy on 2006-05-04
what kind of streaming audio is it?

what does the file end with - .pls, .m3u, .mov, etc?

---

### Post by matthewstory on 2006-05-04
Also anticipating any, you can do anything with mplayer, totem etc. so why would you want windows media player installed, I should say that I've set up both Totem and VLC plug-ins up in firefox and neither of them worked with MLB game day audio, though they work for most everything else, (and I do hae the windows codec pack installed as well, I can watch WMVs from pretty much anywhere else).  Unfortunately I think I'm going to need to go with WMP.

---

### Post by matthewstory on 2006-05-04
pretty sure its windows media audio (.wma)

---

### Post by groggyboy on 2006-05-04
you should be able to listen without using wmp.  do you have win32 codecs installed?

---

### Post by matthewstory on 2006-05-04
> I should say that I've set up both Totem and VLC plug-ins up in firefox and neither of them worked with MLB game day audio, though they work for most everything else, (and I do hae the windows codec pack installed as well, I can watch WMVs from pretty much anywhere else)

Yeah, that's why I posted this earlier.  I would love nothing more than to use the VLC plug-in or the XINE plug-in with the Windows Media Codecs, but it doesn't work, like I said it has to be WMP, I think the problem is that it does some sort of proprietary authorization using WMP that XINE and VLC don't have.

---

### Post by groggyboy on 2006-05-04
ya, i missed that the first time i read it.

maybe you have to try wine.  a windows version of firefox, with the wmp extension?  the ubuntu wiki has instructions on how to get macromedia shockwave working using wine and a program called mozplugger.  maybe you could adapt it to your purposes?

i really can't offer you much more help.  try windows media player in wine.  you won't know until you've tried it. :)

edit - here's the wiki's [website]("https://wiki.ubuntu.com/RestrictedFormats#head-55dd46852b91060cde557660462b56e31cac305f")

---

### Post by Bloch on 2006-05-04
How do you install the VLC plugins for firefox? I already have VLC and it plays a great range of formats. It would be nice to have a choice for the cases where the mplayer plugin doesn't work.

Does anyone have any information about whether the mplayer plugin has improved in Dapper? I'm afraid the ability to view streaming video on RTE (Radio Television Eire) and on the BBC sites is a killer app for a friend. He'll have to go back to windows if he can't view them, and so far they've been pretty buggy.
The RTE video / radio are all realplayer format as far as I can tell. The radio opens with mplayer, (after buffering for a long time) plays for about 3 minutes and stops.

So is there a new improved mplayer plugin on the way?

---

### Post by groggyboy on 2006-05-04
bloch - mplayer works quite well with streaming video under dapper.  i just went to the BBC website and watched a video right now!

groggyboy

---

### Post by Bloch on 2006-05-04
If you are still there Groggyboy, how does it work on the RTE page, on one of the SSIA reports
[http://www.rte.ie/news/2006/0502/primetime.html](http://www.rte.ie/news/2006/0502/primetime.html)

because I just found that generally the BBC pages work OK for me.

---

### Post by groggyboy on 2006-05-04
sorry 'bout the delay.  i had to go to work.

bloch: i went to the link you posted, and mplayer played the video.  it was pretty choppy, tho.

since the format is realvideo, you could just install realplayer and use that.

cheers, groggyboy

---

### Post by Bloch on 2006-05-05
Thanks Groggyboy,
That site is just particularly hard to get working. Radio cuts out etc. When I play these video clips on my mac mini OS X a different clip is shown!!!  I've checked this twice. For example the clip 
Eithne O'Brien sampled people's intentions for their windfall returns in the next year
plays a piece about football. But on the mac mini it plays what you expect - what's described in the blurb.
[http://www.rte.ie/news/2006/0502/primetime.html](http://www.rte.ie/news/2006/0502/primetime.html)

But I don't want to bother you any further - it's enough for me to know this site is not ubuntu-friendly. I'm just happy the BBC works better. And boreme.com

Still, some people may be interested to investigate why a totally different clip is shown depending on your platform.

Thanks again

---

### Post by egghead3 on 2006-05-05
mlb.tv works fine with mplayer and the firefox plugin if you follow the instructions towards the end of the first page of this thread.

[http://ubuntuforums.org/showthread.php?t=154781&highlight=mlb](http://ubuntuforums.org/showthread.php?t=154781&highlight=mlb)

---

### Post by _linux_ on 2006-05-05
[QUOTE=Bloch]How do you install the VLC plugins for firefox? I already have VLC and it plays a great range of formats. It would be nice to have a choice for the cases where the mplayer plugin doesn't work.[/QUOTE]
I know I saw a VLC plugin for Firefox in Synaptic somewhere....

---

### Post by groggyboy on 2006-05-06
there is:> sudo apt-get install mozilla-plugin-vlc
i don't use it myself, so i don't know what it's like.  personally, i much prefer the mplayer frontend than the vlc frontend.  it has nothing to do with mozilla, but still...

---

