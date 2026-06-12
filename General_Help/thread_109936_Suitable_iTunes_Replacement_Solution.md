---
title: "Suitable iTunes Replacement Solution?"
date: 2005-12-29
forum: General Help
---

### Post by starscream1 on 2005-12-29
Please can someone have a look at his post and see if they can come up with a good solution. I'm stumped so far :(

I have just changed from Windows XP to Ubuntu...but I have one massive void to fill.

Accessing my extensive music library.

Now I have all my music stored on a windows share.

I have mounted this using fstab in media so it is always accessible.

I can play music (mp3s) from Ubuntu easily by just going to my itunes mounted media and opening in say xmms. Plays great direct from the mount.

Now what I really need is a piece of software that will put all my music into a library the way iTunes did. Because it was iTunes songs that I purchased are protected aac files. Albums I imported from CD are mp4 files and any songs I already had or imported from other sources are mp3 files.

So I need to be able to have all 3 file types playable and added to one big library. 

Requirements

- Ability to rip CD to mp3
- Ability to burn to CD playlists
- Ability to play mp4 files and recognise tags for artist, album, title etc
- same for mp3
- same for protected AAC files (way to convert to mp3 and add again to library?)
- Ability to buy music online with an extensive database as itunes music store. Obviously need non protected mp4 or mp3 files.


The reason I ask for a suitable solution is that I know no one piece of software will do all this, unless juk or amarok can have plugins to performs all of this?

I have a feeling I will need to convert aac files I have.

Would napster or something similar let me buy unprotected songs? I dont want to ilegally download. I am happy to pay.

I am currently testing Madman for the library which uses xmms to play the files but madman doesnt import aac files or mp4 files so its only mp3 :( seemed good too.

Hope someone has a similar working setup.

even better would be one big ass audio conversion utility which would convert all my files to mp3 in one swoop. Does such a thing exist?

I would be extremely grateful to anyone who can help me out here. Otherwise I am going to be forced to stick with XP, please dont make me!! he he

thanks,

John

P.S, one other thing to bear in mind is that when I tried to add the itunes media mount to software like juk and amarok it completely failed, did not import anything, not even mp3s? Madman organiser managed to import just the mp3s.

---

### Post by penguain on 2005-12-29
its not out yet.. or even in beta but it should be out soon

[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

its an open source "rip" off of itunes

penguain

---

### Post by ykpaiha on 2005-12-29
check gtkpod work great
You can as well use some amarock plugins
I rather prefer gtkpod for my ipod.
and for ripping
under kde it rip all by itself if you read a cd (you just choose the ogg: mp3 or else)
other like grip as well very good riper..(gogo,flac,ogg...=)

---

### Post by hw-tph on 2005-12-29
Or just use Rhythmbox or Quod Libet or anything else that works. But actually, the best replacement would probably be Amarok, but it is QT based. I hate using QT (KDE) apps in Gnome personally but if you can live with it, give it a try. Very impressive app, and it's available from the official sources (1.3.5 in the repositories, 1.3.7 from the [Kubuntu site](http://kubuntu.org/announcements/amarok-1.3.7.php)).


Håkan

---

### Post by dbeckham32 on 2005-12-29
Yes, I think that SongBird application ([www.songbirdnest.com](www.songbirdnest.com)) is going to be a big deal. Hopefully it will evolve into a wonderful application on par with Amarok.

I wish Apple would come out with iTunes for Linux, but I wouldn't hold my breath.

---

### Post by Suger on 2005-12-30
For the aac/mp4, you need faad support. That is gstreamer0.8-faad or xmms-mp4 in synaptic, depending on the program you use.

No need to convert anything (gosh, I have 20 GB of mp4, I don't even want to think about the conversion time :p ).

Personally, I like Quodlibet a lot, but I think you have to compile from scratch to get aac/mp4 support, the synaptic version is a little old.

---

### Post by MetalMusicAddict on 2005-12-30
I have to agree SongBird looks great. I like that Winamp devs are working on it also. Maybe we will be able to get some of those great visualizations or at least the framework to create them. Goom just doesnt cut it.

---

### Post by kaamos on 2005-12-30
Have you tried banshee? It seems to be able to do most of the stuff you want to do.
[SIZE="1"]
(..personally I've never gotten any version of banshee to even start. Damned mono apps..)[/SIZE]

---

### Post by mcduck on 2005-12-30
[QUOTE=MetalMusicAddict]I have to agree SongBird looks great. I like that Winamp devs are working on it also. Maybe we will be able to get some of those great visualizations or at least the framework to create them. Goom just doesnt cut it.[/QUOTE]
If visualizations is what you want, check out ProjectM and libvisual.

[http://xmms-projectm.sourceforge.net/]("http://xmms-projectm.sourceforge.net/")

---

### Post by MetalMusicAddict on 2005-12-30
Nice. It looks like it has to be ported to specific players right? Looks like they have XMMS, Winamp (dont see the point) and iTunes files already setup. Just need to compile. I would love to see this done for SongBird and Rythmbox. Wish someone would make a Ubuntu .deb.

---

### Post by mcduck on 2006-01-01
[QUOTE=MetalMusicAddict]Nice. It looks like it has to be ported to specific players right? Looks like they have XMMS, Winamp (dont see the point) and iTunes files already setup. Just need to compile. I would love to see this done for SongBird and Rythmbox. Wish someone would make a Ubuntu .deb.[/QUOTE]
I have the .debs, I can't remember where I got them but send me your e-mail address in PM and I'll mail them to you :)

---

### Post by flosofl on 2006-01-11
Here's my setup:

[LIST]
[*]For playback/podcasts/iPod Management/streaming:[COLOR="Blue"] Amarok from the subversion repository.[/COLOR]
[/LIST][INDENT]**Read this[COLOR="Blue"] [thread]("http://www.ubuntuforums.org/showthread.php?t=80492")[/COLOR].  Read everything.**
Except for the iTunes Music store, this thing is perfect (for that I use iTunes in crossover office).  My collection is managed with MySQL, I can manage playlists with my iPod, get podcasts, play streaming audio.  One of the coolest "little" features is it will search for album art.[/INDENT]
[LIST]
[*]For ripping m4a: [COLOR="Blue"]Grip with faac [/COLOR]
[/LIST][INDENT]**Read this [COLOR="Blue"][thread]("http://www.ubuntuforums.org/showthread.php?t=81375")[/COLOR].**  It takes a little playing around.[/INDENT]
[LIST]
[*]For purchasing from iTunes Music Store: [COLOR="Blue"]Crossover Office with iTunes[/COLOR]
[/LIST]

---

### Post by hscottyh on 2006-01-12
For an alternate place to get music, I suggest:
[http://www.allofmp3.com](http://www.allofmp3.com) from Russia.

You have a choice to download in your choice quality in the following formats: MP3, WMA, OGG, MPC, and AAC _with no DRM_!

The cost of each song varies as they charge you 2 cents per megabyte. Which averages out at about 10 cents a song at 194k sampling rate.

Although the music industry doesn't like it.... I've researched the legalities of it in the US and it seems to be legal as they do pay royalties according to Russian law and it's not illegal in the US to import music from other countries for personal use.

I don't mind paying for music either, but I'm frugal and like to get the best price. Hopefully it'll take lobbiest a while to get the laws changed?

---

### Post by handy on 2006-01-12
Here's a conversion tool:

[http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/)

Cheers,

handy

---

### Post by marinosr on 2006-01-12
!?!?!?!?!?

Thanks for that link to allofmp3.com. That site is REDICULOUS!

---

### Post by CameronCalver on 2006-03-12
When i open banshee and gtkpod it works fine but when i plug in my ipod the program qits then if i try to open it again it just wont start???

---

### Post by hw-tph on 2006-03-13
hscottyh, thanks for the tip!
I was going to just ignore it since they didn't have any of the first four artists I searched for. They did, however, have the fifth - The Afghan Whigs. And not only that, they carry the Howlin' Wolf live promo as well! Woot! I'm a happy man now. :D


Håkan

---

### Post by motrennoc on 2006-10-24
> **dbeckham32 said:**
> Yes, I think that SongBird application ([www.songbirdnest.com](www.songbirdnest.com)) is going to be a big deal. Hopefully it will evolve into a wonderful application on par with Amarok.

I wish Apple would come out with iTunes for Linux, but I wouldn't hold my breath.

Why doesn't Apple support Linux more? They like windows?
I'm downloading songbird now. It looks like it's come a ways since these last posts
T

---

### Post by beerorkid on 2006-10-24
I checked out songbird last week, it is pretty awesome.  But still use banshee for my ipods.

---

### Post by morphet on 2007-01-05
Amarok is funky to handle, despite it's beautiful and innovative interface.  Banshee crashed every time it got to song number 1000 give or take while scanning. My candidate:

Quod Libet. Don't let it's rugged looks mislead you. Impressive library handling capabilities, rock solid (40+ gigs of music and it didn't even blink), trivial learning curve for the itunes regular. Search for it in the repositories. A newer version is out on their site, but the edgy repo included one is so good, I don't want to mess with it.

(imac g5 ppc, Edgy)

EDIT: I installed v. 0.24 from the official site, and it was extremely easy, so disregard the last line.

---

