---
title: "Can any Linux Program Handle Large Music Libraries?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-06-07
Ok, I'm starting to get really frustrated. I have 70GB (12,000) mp3s up on my NAS server and I can't find any program that can run in linux and handle this large a network library. In windows; Winamp, iTunes, XBMC, XPMCE, and WMP have no problem at all loading and playing music from the server. 

In Ubuntu, Banshee loads the library but music playback is choppy. Rhythmbox hard locks when it opens (trying to read the library), and XMMS has no problems loading and playing back the entire library but that program doesn't have any search capability (which I must have). 

Any ideas?

---

### Post by MetalMusicAddict on 2006-06-07
Ive had no problems with [Listen]("http://listengnome.free.fr/") and [gMusicBrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html"). I have about 80gigs over a gigabit network.

What do you use to see the NAS? Samba?

---

### Post by Duf_Sh on 2006-06-07
Ever tried Amarok? It uses MySQL, Postgresql or sqlite to store your collection (your choice), has an auto-update mechanism for the collection, and the new version 1.4.0 is in semi-official repos. Sure it is based on KDE, but I find it to be the best around.

---

### Post by zac851 on 2006-06-07
[QUOTE=Thund3rstruck]Ok, I'm starting to get really frustrated. I have 70GB (12,000) mp3s up on my NAS server and I can't find any program that can run in linux and handle this large a network library. In windows; Winamp, iTunes, XBMC, XPMCE, and WMP have no problem at all loading and playing music from the server. 

In Ubuntu, Banshee loads the library but music playback is choppy. Rhythmbox hard locks when it opens (trying to read the library), and XMMS has no problems loading and playing back the entire library but that program doesn't have any search capability (which I must have). 

Any ideas?[/QUOTE]

XMMS has a seach.  Hit the "J" Key, type the name of the song, You can type any word in the song title, or the artist name. and it will pull it up.  Hit enter to play.

---

### Post by pmj on 2006-06-08
The by far fastest player of this kind I've found is GMPC. It has absolutely no problems with only 12k songs. If it has any drawbacks it's perhaps that it's pretty limited feature-wise (no lyrics, last.fm support, tag editing etc) and can take a while to set up.

Other clients you might want to check out is Quod Libet, Listen, Exaile and BMPx.

---

### Post by mcduck on 2006-06-08
[QUOTE=pmj]The by far fastest player of this kind I've found is GMPC. It has absolutely no problems with only 12k songs. If it has any drawbacks it's perhaps that it's pretty limited feature-wise (no lyrics, last.fm support, tag editing etc) and can take a while to set up.

Other clients you might want to check out is Quod Libet, Listen, Exaile and BMPx.[/QUOTE]
Yes, MPD handles large libraries with no problems (GMPC is just a GUI frontend for MPD)

---

### Post by pmj on 2006-06-08
[QUOTE=mcduck]Yes, MPD handles large libraries with no problems (GMPC is just a GUI frontend for MPD)[/QUOTE]
I know that. MPD is really fast, but so is GMPC. No other player I know of can bring up lists of thousands of artists, or search through tens of thousands of songs in just a second or two. Most will freeze the GUI for half a minute whenever you do something like that.

---

### Post by nandasunu on 2006-06-08
I use amarok for my 40gig+ colectiion, works great for me.

---

### Post by Thund3rstruck on 2006-06-08
Thanks for the replies guys... wow, I didn't realize there were so many programs out there. I'll start giving those a shot and I'll scrap Rhthymbox and banshee

---

### Post by Balki on 2006-06-08
Quod Libet ([http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)) is pretty good too.

---

### Post by bluenova on 2006-06-08
I would suggest amarok with a mysql database.

---

### Post by Thund3rstruck on 2006-06-11
I just want to extend my gratitude to everyone here that suggested amaroK. I just got it setup and running and it is absolutly incredible. I can truly appreciate the great amount of time and effort that must have gone into developing this program 

By far, this is the best open source application I have seen...

Thanks Again,
T3

---

