---
title: "Is Shoutcast TV possible in 6.06 ?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Browser_ice on 2006-08-21
I had done a forum seach on Shoutcast TV and found very few threads about it. Also, none of them were actualy mentioning if this is possible.

Is it possible to have Shoutcast TV with 6.06 ?

I used to have it with my Winamp XP and whish I had it in Ubuntu.

---

### Post by reclusivemonkey on 2006-08-21
> **Browser_ice said:**
> I had done a forum seach on Shoutcast TV and found very few threads about it. Also, none of them were actualy mentioning if this is possible.

Is it possible to have Shoutcast TV with 6.06 ?

I used to have it with my Winamp XP and whish I had it in Ubuntu.

I don't know what Shoutcast TV is, but if you are looking for streaming video on the net in Ubuntu, have a look at Democracy; it may be what you are looking for. I use PenguinTV also, but you will need to locate feeds yourself for that.

[http://www.getdemocracy.com/walkthrough/](http://www.getdemocracy.com/walkthrough/)

[http://penguintv.sourceforge.net/](http://penguintv.sourceforge.net/)

---

### Post by mordi on 2006-08-21
tunapie or lintelkku with mplayer. got it form this wiki:
[http://gentoo-wiki.com/HOWTO_NSV_on_Linux](http://gentoo-wiki.com/HOWTO_NSV_on_Linux)
I didn't try lintelkku. I use tunapie, and  I get pretty much the same stuff as with winamp.

---

### Post by Chris Tucker on 2006-08-21
Shoutcast TV uses NSV, NullSoft Video. NullSoft only does windows right now. so i doubt it, though there may be a port. Over the next few months i'll be looking for such a thing, because i like ess.tv , and have no intentions of buying cable when i move. $5 a month for tv quality (would be exported to a tv), a ton of channels, is quite nice in my opinion :)

---

### Post by bluemax on 2006-09-09
VLC will play NSV (shoutcast tv) streams. The only downside is that you have to know the address of the stream. This is the ONLY thing keeping me from switching completely to linux. There's currently no way to get the listing of Shoutcast TV streams, like you can in Winamp. I'm sure it's just a matter of querying a server for the list, too. But when you ask about it, no one knows what Shoutcast TV is, or no one cares. ](*,) :mad: 

This is also why Winamp, to me, is still the best media player on any platform. It's nice just to have the listing of channels, double-click one and have it just work without any headaches.

---

### Post by bluemax on 2006-09-10
Ah, you guys will be very happy. Look what I found. :)

[http://www.codepost.org/browse/snippets/4](http://www.codepost.org/browse/snippets/4)

This is a link to PHP code which retrieves the full Shoutcast TV listing, with the streams as clickable links. So if you have Apache+PHP installed, you can just use this locally. However I'm probably going to convert this to Python or something to make this a standalone program.

---

### Post by lunadog on 2006-10-14
Just use tunapie.. It works (I wrote it!) :)

[http://tunapie.sourceforge.net](http://tunapie.sourceforge.net)

---

### Post by Browser_ice on 2007-01-28
About Tunapie, 
> **lunadog said:**
> Just use tunapie.. It works (I wrote it!) :)

[http://tunapie.sourceforge.net](http://tunapie.sourceforge.net)

[Forum trafic on your project]("http://sourceforge.net/project/stats/detail.php?group_id=132284&ugn=tunapie&type=forum&mode=12months&forum_id=0"). If its so great how come almost no one visits your site ?


Now to get back on my subject, anything new on this topic ?  Anything seriously worth checking out ?

---

### Post by mocha on 2007-03-05
"Forum trafic on your project. If its so great how come almost no one visits your site ?
Now to get back on my subject, anything new on this topic ? Anything seriously worth checking out ?"

You should check it out before making comments like this.  This app is great and is just what I've been looking for for a long time.

---

### Post by ice60 on 2007-03-24
> **Browser_ice said:**
> 

Now to get back on my subject, anything new on this topic ?  Anything seriously worth checking out ?

i just installed tunapie thinking it played shoutcast streams, it looks like it does with shoutcast video options, and it plays video streams, but am i wrong in thinking they're from shoutcast :confused:

---

### Post by lunadog on 2007-04-03
> **Browser_ice said:**
> About Tunapie, 


[Forum trafic on your project]("http://sourceforge.net/project/stats/detail.php?group_id=132284&ugn=tunapie&type=forum&mode=12months&forum_id=0"). If its so great how come almost no one visits your site ?


Now to get back on my subject, anything new on this topic ?  Anything seriously worth checking out ?

Well, it's your loss. It does exactly what you asked in your original question...

And I would not say that number of posts to a forum is a good way of telling how many people use a piece of software..

I have had 14757 downloads to date (only half of them from me :lolflag:  ).. and that is not including the direct downloads from the apt archives..

I guess that the fact that few people are asking for more features or bugfixes should be a good sign (at least to my mind).

But by all means, have fun in the absence of Winamp videos.. I have heard trolling forums is a good way to pass the time.

---

### Post by mocha on 2007-04-05
Lunadog,

I love your app.  I was excited to see something like this for Linux.  Sometimes there are video streams that open mplayer but then the mplayer screen turns to blocky green colors and crashes.  Is that because the streamer is using a codec that is not supported in mplayer?  Check it later and you'll see what I mean.  I believe some of the Demoscene channels do this, I'm not at my box right now to verify.

Oh, I forgot to ask what apt repository is your app in?  I had to compile it from source.  I don't think it's in the Edgy repositories.

---

### Post by lunadog on 2007-04-06
> **mocha said:**
> Lunadog,

I love your app.  I was excited to see something like this for Linux.  Sometimes there are video streams that open mplayer but then the mplayer screen turns to blocky green colors and crashes.  Is that because the streamer is using a codec that is not supported in mplayer?  Check it later and you'll see what I mean.  I believe some of the Demoscene channels do this, I'm not at my box right now to verify.

I have seen this. I think it is a bug with mplayer not supporting the codec. I usually use totem (xine based) which seems to work with most streams. The ones that totem cannot handle, mplayer or xine or vlc will play. You could help the effort by reporting non-working streams to the relevant project. I reported some bugs to mplayer before, but got very little help. Thus the change to totem.

> Oh, I forgot to ask what apt repository is your app in?  I had to compile it from source.  I don't think it's in the Edgy repositories.

I think it is in Feisty (I am a Debian user not Ubuntu, so I don't really know all the terminology..). You can also get the latest and greatest version from getdeb.net.

Please email me with any suggestions for improvements. 

One thing I have been toying with is completely upgrading the GUI. If there is enough interest I might just to it!!

---

### Post by mocha on 2007-04-06
Hello!  I just upgraded using the package on the getdeb webpage.  I also tried using Totem-xine, and yes, it does play more of the video streams.  Thanks!

---

### Post by jazzroy on 2007-04-24
sorry,
but it looks like on get-deb the file is missing!

---

### Post by IamAcoconut on 2007-06-17
Good thing! Thanks. I've just bulit the newest version from sources, as Feisty's repos only provide 1.3. (lacking adult content ;))

---

