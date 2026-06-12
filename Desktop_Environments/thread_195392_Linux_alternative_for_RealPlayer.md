---
title: "Linux alternative for RealPlayer?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by H.E. Pennypacker on 2006-06-12
Does Linux provide anything that is a lot like RealPlayer 10.5.  I stress I am *not* talking about the current version available for Linux (10.0.).  Windows' current version is 10.5, and it does everything I like.

I have already checked out Amarok, Movie Player (Totem), Juk, and Rhytmbox.  None of them compare to RealPlayer in terms of featurer.  Keep in mind that QuickTime, Windows Media Player, VLC Player, and Winamp fall short of matching RealPlayer's features, as well.  

It seems there's just nothing like RealPlayer.  Even in Windows, there's really nothing comparable to RealPlayer.  It does everything I like, including:

1.  A File > Open command where I can put in a link, and it will immediately stream the file.  Not only that, but it will stream just about any media file type player available anywhere on Earth.  If it won't play a certain file type, you can download a small upgrade.  

2.  It has a library where I can save a bunch of links for streaming files.  It's efficient, convenient, and you never have to download multimedia files, because you can just stream them.  Most media players don't have a way of creating a playlist just with streamable URLs.

3.  It's compact and small.  It can be heavy when the library is opened, but you can always close the library.

4.  It looks great.

I know Linux provides a media player that will cover a few things here and there of my needs, but like I said, I've checked out a whole bunch of media players, and nothing seems to match my needs.  I could be wrong, however.  Can anyone enlighten me?

Please remember the list of media players above I've already tested.  They are not on the same level as the latest release of RealPlayer for Windows (neither are most Windows media players).

---

### Post by IYY on 2006-06-12
I think you're the first person I've ever seen who actually likes Real Player and uses it as a media player.

---

### Post by mscman on 2006-06-12
Have you tried using Helix?  The Linux version of RealPlayer is based off of Helix.  I know you can stream media, although I'm not sure about the playlist thing, but it does have favorites.  Might be worth a try.

---

### Post by rado_london on 2006-06-12
I love realplayer as well. Although I use it to play single mp3 as it is quick.

---

### Post by taurus on 2006-06-12
[QUOTE=rado_london]I love realplayer as well. Although I use it to play single mp3 as it is quick.[/QUOTE]
Why even waste system resource for one mp3.  Use a terminal program like mpg123 (or mpg321)...
```

mpg123 <filename>.mp3

```

---

### Post by mdurham on 2006-06-12
You can download a Linux version of RealPlayer from the RealPlayer web site. They also provide installation instructions.
I find it works very well inside Firefox.

---

### Post by Ahriman on 2006-06-12
Have you tried Listen? It's in the repos, and while it looks sort of like Rhythymbox, it has a fair few more features than RB. I use it as my media player, and it's great for podcasts and other streaming media.

---

### Post by H.E. Pennypacker on 2006-06-27
> I think you're the first person I've ever seen who actually likes Real Player and uses it as a media player.

I am familiar with all the RealPlayer hate, although the haters can't provide an application like it.

> Have you tried using Helix? The Linux version of RealPlayer is based off of Helix. I know you can stream media, although I'm not sure about the playlist thing, but it does have favorites. Might be worth a try.

It may be able to stream...but not the most popular formats. 

> I love realplayer as well. Although I use it to play single mp3 as it is quick.

Same here..unfortunately it doesn't have all the features that I needed in Windows.

> 
Why even waste system resource for one mp3. Use a terminal program like mpg123 (or mpg321)...

Back in Windows, I mostly streamed media files, hardly ever downloading.  Out of the hundreds of files I had in my RealOne Library, only a handful were files located on my hard-drive.  Others were links to online streams.

That's why I wouldn't bother with the terminal...not only is it an awkward application, I hate using it.

> 
You can download a Linux version of RealPlayer from the RealPlayer web site. They also provide installation instructions.
I find it works very well inside Firefox.


The version of RealPlayer in Linux is so limited, it is almost without features.

> Have you tried Listen? It's in the repos, and while it looks sort of like Rhythymbox, it has a fair few more features than RB. I use it as my media player, and it's great for podcasts and other streaming media.

I have tried Listen, and it doesn't do what I want it to do.  Here's what I usually do: I go on a website like singingfish.com, and I take a URL from the website.  I then switch over to my media player, select "File -> Open URL" so that I can stream the URL I copied.  In addition to that, I want to be able to save the URL (with the artist's info), so that I don't have to run back to singingfish every time.

RealPlayer carried this out so well, it's unbelievable.  So far, I have not been able to find a single application to replicate RealPlayer, because most media players don't store streaming info.

---

### Post by art on 2006-06-27
I don't know if this will do the job (haven't tried it yet), but it might. Songbird was released today, you might wanna give that a shot. Available here:
[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

---

### Post by neutro on 2006-06-27
Nobody mentionned XMMS yet... an old classic. It's a Winamp clone. I think it satisfies most of the O.P.'s requirements...

1. Right-Click -> Play -> Open Location (CTRL-L), paste URL
2. Works well with standard playlists (you can save a playlist containing streams)
3. It's compact and small allright
4. Looks great... well that one depends on your tastes. At least it's skinnable, but smallish interfaces mimicking something akin to car radios are rather not in vogue right now.

Also, you might want to check out gmplayer (graphical front-end to mplayer), and also xine. Mplayer plays about anything if the w32codecs package is installed, but I find using the keyboard much more easy than decoding the uninspired gmplayer themes. I prefer typing mplayer <filename or url> and then the arrows for seeking, q for quitting, f for fullscreen (if video), spacebar for pause...

---

### Post by yopnono on 2006-06-27
Test banshee

---

### Post by michux on 2006-06-27
[QUOTE=H.E. Pennypacker]Does Linux provide anything that is a lot like RealPlayer 10.5.  [...] It seems there's just nothing like RealPlayer.  [/QUOTE]

I would say: try Kaffeine with Xine or Mplayer engine (not gstreamer, cuz it does not support Real media and WMV) or just old plain mplayer.

[QUOTE=H.E. Pennypacker]1.  A File > Open command where I can put in a link, and it will immediately stream the file.  Not only that, but it will stream just about any media file type player available anywhere on Earth.  If it won't play a certain file type, you can download a small upgrade.  [/QUOTE]

MPlayer does exactly the same. You can either choose File-->Open in Kaffeine or other frontend or just simply enter: *mplayer url://the_url* to play any (really **any**) media file.

[QUOTE=H.E. Pennypacker]2.  It has a library where I can save a bunch of links for streaming files.  It's efficient, convenient, and you never have to download multimedia files, because you can just stream them.  Most media players don't have a way of creating a playlist just with streamable URLs.[/QUOTE]

Mplayer or Kaffeine does have it.

[QUOTE=H.E. Pennypacker]3.  It's compact and small.  It can be heavy when the library is opened, but you can always close the library.[/QUOTE]

Mplayer is fast as hell. Kaffeine is a little more advanced graphically (and used Qt which is more resource-hungry).

[QUOTE=H.E. Pennypacker]4.  It looks great.[/QUOTE]

Matter of personal taste. I think amarok looks best of all media players in Linux but it does not support video (yet?). Kaffeine and mplater are fine for me.

[QUOTE=H.E. Pennypacker]Please remember the list of media players above I've already tested.  They are not on the same level as the latest release of RealPlayer for Windows (neither are most Windows media players).[/QUOTE]

Good luck with choosing the right one for you and please share your choice!

---

### Post by ffi on 2006-06-27
[QUOTE=IYY]I think you're the first person I've ever seen who actually likes Real Player and uses it as a media player.[/QUOTE]

Then here's the second....

I like it with vtuner, I wish I had an alternative for that program, listening to streaming media without hassles....

---

### Post by H.E. Pennypacker on 2006-07-12
> I don't know if this will do the job (haven't tried it yet), but it might. Songbird was released today, you might wanna give that a shot. Available here:
[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

Songbird sounds like an excellent piece of software, but it is unstable currently, and is not really ready for public use.

> Nobody mentionned XMMS yet... an old classic. It's a Winamp clone. I think it satisfies most of the O.P.'s requirements...

XMMS is alright.  I've tried it out, and while it is very light, it doesn't match up to RealPlayer 10.5.  XMMS' playlist doesn't allow for enough information, and if you try to play a new stream, the playlist is cleared.  There may be an option to stop this from happening.  Also, what if I want to play a song from one playlist, and another song from another playlist?  There's no playlist mixing.  What if I feel like listening to songs from different playlists?  RealPlayer offers that functionality.

> 2. Works well with standard playlists (you can save a playlist containing streams)

Instead of saving a playlist to a folder, with RealPlayer, I could manage it all from RealPlayer.  I wouldn't have to "load" playlists.  They were all there, and no searching for them.  You select which playlist you want, and that's it.  Check out a screencapture of one of my playlists:

[[img]http://www.UploadYourImages.com/thumb/942928realone_playlist.jpg[/img]]("http://www.UploadYourImages.com/view/942928realone_playlist.jpg")

It holds lots of info.

> 3. It's compact and small allright
4. Looks great... well that one depends on your tastes. At least it's skinnable, but smallish interfaces mimicking something akin to car radios are rather not in vogue right now.

It does look great, and it is *compact.*

> Mplayer plays about anything if the w32codecs package is installed

MPlayer is a pain.  For one, it's video window and the menu are seperate.  How annoying!  And what if I don't want to play a video...just an audio file?  I am looking for a media player that is not geared either towards audio or video, and its meant for everything.

> Test banshee

Banshee is really nothing new.  Also, its far from what I am looking for.  It's a lot like Listen.

>   I would say: try Kaffeine with Xine or Mplayer engine (not gstreamer, cuz it does not support Real media and WMV) or just old plain mplayer.

I'll try out Kaffeine, although I dislike using KDE applications.  I'd prefer something written for GTK+.

> Good luck with choosing the right one for you and please share your choice!  

For now, it's going to be XMMS (or BMP, or BMPx, or Audacious, or any other XMMS derivative).  

I'll be emailing Real Networks to see if they plan on releasing RealPlayer 10.5 anytime soon, because the last release has been two years ago.  Even if they do, I don't think they'll be supporting proprietary codecs.  Hmmm.

---

### Post by neutro on 2006-07-13
It seems to me that your problem is... that RealPlayer 10.5 is not available for Linux yet. Each player is more or less unique, and RP 10.5 is  clearly your favorite. No, it doesn't seem that there's an open source player having the exact feature set of RP 10.5. So maybe you'll simply have to

- continue using RP 10.5 on WinXP
- wait for RP 10.5 on Linux
- learn to cope with different interfaces...

> 
XMMS is alright.  I've tried it out, and while it is very light, it doesn't match up to RealPlayer 10.5.


I'm pretty sure it doesn't. I'm not even sure if it is still being developed. I heard about an "XMMS 2" in developement, though.

> 
XMMS' playlist doesn't allow for enough information, and if you try to play a new stream, the playlist is cleared. There may be an option to stop this from happening.


Yeah; I think that when you do that, XMMS closes the current playlists, opens a new empty one and add the URL to this playlist. Sorry, I'm not an XMMS expert, but I remember that back in the days, I used to have playlists containing many streams. Maybe I pasted them manually, I really don't remember.

> 
Also, what if I want to play a song from one playlist, and another song from another playlist?  There's no playlist mixing.  What if I feel like listening to songs from different playlists?  RealPlayer offers that functionality.


Again, XMMS playlist management is quite basic: only one playlist is loaded at a time. XMMS is not a music database management system such as iTunes or AmaroK, and was originally built to play *files*. Nowadays, many people don't even know where their music files actually lie, and even in which format they are encoded. To play songs from different playlists in XMMS... you have to actually add those two individual files to the current playlist.

> 
Instead of saving a playlist to a folder, with RealPlayer, I could manage it all from RealPlayer.  I wouldn't have to "load" playlists.  They were all there, and no searching for them.


This gripe, while understandable, is actually somewhat funny, since if you save your (XMMS) playlists in one folder, they are all there at your fingertip if you click on the "load playlist" button. The only difference is that you get to select them from a file browser dialog instead of from a sidebar or some other widget.

Nowadays apps don't trust the ubiquituous file browser to handle file browsing (snicker).

> 
MPlayer is a pain.  For one, it's video window and the menu are seperate.  How annoying!  And what if I don't want to play a video...just an audio file?  


I really find the gmplayer app (the GUI to mplayer) annoying too. However, I use mplayer a lot in the terminal. It may seem old-style, but it has lots of advantages... It has no annoying interface taking up screen real estate. Every function is accessed from the keyboard directly, not a "virtual" button. Press spacebar to pause. F for fullscreen. Arrows for fast-forwarding or rewinding.

Playing any media file is as simple as typing "mpl[tab] <filename>" at the prompt. If it's an MP3, you'll hear it, if it's a movie, you'll see it, that's all. Of course, no fancy playlist management here. But if you like what you hear on a stream, try the handy "-dumpstream" option :) It's light, efficient, keeps out of the way, and can handles (almost) every file format out there.

I know it can be a pain not having everything at the same place, but I for one settled on using the best tool available for each job.

Just for the record, I'm too not that satisfied with the state of music players for Linux. There's a ton of them, but most lack some feature I'd like. JuK would be terrific but can't play streams. AmaroK can do almost everything, but is bloated and crash on me quite often. Well. Let's keep hoping :)

---

