---
title: "Foobar2000 alternative"
date: 2008-06-14
forum: Gaming &amp; Leisure
---

### Post by Jophish on 2008-06-14
Hi there.

Back when I was running windows, I had a wonderful little program called Foobar, It was able to stream music from my home server (where I keep all my mp3s). I was trying to find an alternative for Ubuntu, a small media player that can keep an index of all the mp3 files on the slimserver, and stream them straight to my speakers.
I quite like the set up of rhythmbox, especially the cover art display, is rhythmbox able to look at directories on a LAN?

Thanks.

---

### Post by mccord on 2008-06-14
> **Jophish said:**
> I was trying to find an alternative for Ubuntu, a small media player that can keep an index of all the mp3 files on the slimserver, and stream them straight to my speakers.

i missed foobar too after switching to linux, amarok is nice but a bit resource heavy for my old pc
personally i use mpd (music player daemon) and sonata as the frontend :)

you could have a look at [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html"), from what i hear it comes reasonably close to foobar

> **Jophish said:**
> 
I quite like the set up of rhythmbox, especially the cover art display, is rhythmbox able to look at directories on a LAN?
Thanks.
can't think of a reason why it wouldn't work with mounted samba/nfs shares
you can find a howto for mounting samba (windows) shares here: [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by Jophish on 2008-06-14
I managed to mount my server to a folder in my profile, however in order to do this every time, I think i need to edit fstab. 
Hows this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=190eba17-6492-49fe-a8b4-f3b956987e3f /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dbcdadc2-fbbe-4b82-ac0e-ad963b53ec15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Music folders
//192.168.0.10/Public/music /home/jophish/Music smbfs auto 0 0
```

---

### Post by Jophish on 2008-06-14
I got the fstab to work ok, However gmusicbrowser was not able to play any music, as I can't set the volume to anything but -1. It claims that I am missing alsa-utils, although I have this, and have reinstalled. I can hear music everywhere else though.
Another thing, gmusicbrowser doesn't seem to quite cut it with 130,000+ songs on my database, Is there a different application that can handle this many songs?

---

### Post by disturbedite on 2008-06-14
i'm surprised no one has mentioned yet that foobar2000 works virtually perfectly with wine.

i use audacious myself though.

---

### Post by texasjim on 2008-06-14
Have a look at AMPACHE, it works great over my wireless LAN.
  Jim Hayes

---

### Post by Jophish on 2008-06-14
I have since discovered Amarok, It seems to be working quite well, and I like the interface (just wish that the icons came in orange though).

Thanks anyway guys.

Also, If anyone reading this knows about configuring drivers for graphics cards, please take a look at this thread here: [http://ubuntuforums.org/showthread.php?p=5183776](http://ubuntuforums.org/showthread.php?p=5183776)
I need all the help I can get with it.

---

### Post by sultanoswing on 2008-06-14
I was about to mention Amarok. As an ex-Foobar2000 user myself, Amarok took a bit of getting used to, but it really is a very, very good program.

---

### Post by jdorenbush on 2008-09-13
> **mccord said:**
> you could have a look at [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html"), from what i hear it comes reasonably close to foobar

I have tried just about every audio player for Ubuntu and this is by far the best I have found. Especially if you have lots of music, this is the easiest for organization, it also has a mass renaming option to. Real good program. It has a few visual bugs, but nothing that would stop me from using it. I definitely recommend this!

---

### Post by lakersforce on 2008-09-14
vlc

---

### Post by jdorenbush on 2008-09-14
> **lakersforce said:**
> vlc


VLC is great for video, but is it really made for audio and music collections?

---

### Post by lakersforce on 2008-09-14
> **jdorenbush said:**
> VLC is great for video, but is it really made for audio and music collections?

It's good for network streaming (as with so many other fine applications).

---

### Post by charlieg on 2008-09-16
I'm a big fan of Banshee, but also Quod Libet worked nicely for me.

[http://www.banshee-project.org/](http://www.banshee-project.org/)
[http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)

---

### Post by cjssmo on 2009-03-05
Ampache + XML API + Amarok2 == Streaming Music

---

### Post by zero777zero on 2009-03-05
i use foobar through wine, i havent found another audio player other than winamp that can handle metadata as well as foobar.

---

### Post by 1337 on 2009-03-07
I recommend MPD (Music Player Daemon) + Sonata (both can be found via synaptic) for home music server streaming purposes and [Consonance]("http://www.raiden.net/?cat=2&aid=442") as it reminds me Foobar2000 most and it's very light. Ubuntu packages can be in [this]("https://launchpad.net/~kholis/+archive/ppa") ppa repository. 

Regards

---

### Post by steliyan on 2009-03-30
No alternative to fb2k.. With its perfect cue sheet file support it's irreplaceable.

---

### Post by jdorenbush on 2009-03-30
I loved foobar when I was on Windows, but I have completed avoided using Wine since I have been on Linux. So, no Windows software for me. :)

But Songbird has been working out pretty good for me. No complaints thus far. [http://getsongbird.com/](http://getsongbird.com/)

---

### Post by armagedonc on 2009-08-22
Gnu/linux needs a fb2k software like, fb2k it's a clean and light program that supports every format, cue sheets, tabing, etc. perfectly.
fb2k really dont seems to be a windows program.:(

---

### Post by jdorenbush on 2009-08-22
I've actually become fairly content with the default Ubuntu audio program -- Rhythmbox. Songbird isn't bad either. I just like the native feel of Rythmbox.

---

### Post by Psqad on 2010-05-11
i miss Foobar as well, the great thing about foobar is letting adress my emu-soundcard(plugged-in to my hifi) directly without windows interference with it  and keep my onboard-soundcard(desktop speakers) for windows sounds simultaneously 
anyone experience with that?
my search continuous ... 

[offtopic] great forum as it is now my knowledge base ;) [/offtopic]

---

### Post by Djzn.BR on 2010-08-29
We could start a petition to **Peter Palowski**. **"Please port foobar2000 to Linux"**. I know he doesn't want to port it, has no interest at all. But with the majority of Linux converts growing each day and the lack of a satisfactory audio player, he may change his mind.

Actually I would even PAY for a foobar2000-linux native. Seriously.

From all audio players I have tested on linux, **no one has ever come close** to fb2k in terms of being a straight forward swiss-knife tool.

Perhaps **JavaTunes** will get there... one day.

---

### Post by foobnix on 2010-09-15
[foobnix]("http://www.foobnix.com/?page=screenshots&lang=eng") is good choose on linux instead foobar2000.

---

### Post by cascade9 on 2010-09-15
foobnix....loks at least interesting, but I hate it when I find .deb packages that dont work on debian. :( Maybe they should rename those packages 'udeb' or something. 

Maybe I'm stuffing up that, I should try it again tomorrow. To much hardware work today, and my brain is broken. 

> **Djzn.BR said:**
> We could start a petition to **Peter Palowski**. **"Please port foobar2000 to Linux"**. I know he doesn't want to port it, has no interest at all. But with the majority of Linux converts growing each day and the lack of a satisfactory audio player, he may change his mind.

Actually I would even PAY for a foobar2000-linux native. Seriously.

From all audio players I have tested on linux, **no one has ever come close** to fb2k in terms of being a straight forward swiss-knife tool.

Perhaps **JavaTunes** will get there... one day.

I think there was a 'please port foobar to linux' thread on hydrogenaudio, and Peter Palowski basicly said "not a snowballs in hell" (IIRC, its programmed on visual c++, and porting to linux would be a PITA). 

I'd consider paying for a linux foobar version....except that I'm already using a version thats conisdered pretty old (0.9.4). Single Column Playlist wont work in the later versions. :( 

Personaly, I dont even want a foobar port because of the many 'swiss army knife' tools (like transcoding). I like it because I can make foobar look _exactly_ how I want it to look.....and I've never seen a  linux native player that will give me anywhere near the same control over appearance, layout, etc as foobar does.

---

### Post by damnated on 2010-09-16
[DeaDBeeF](http://deadbeef.sourceforge.net/) has some of foobar's functionality, like full cue file support, or ape playability, and looks like foobar too, to some extent, although AFAIK it's not skinnable, only basic colors can be changed. But at least it's open source so there's a chance it will be a great player in the future.

---

### Post by Redsandro on 2011-03-15
Hi, I was gonna open a topic about this, but this one is exactly that. So here's a little kick.

**Any new opinions on foobar2000 alternatives?**

I don't like Quod Libet, Amarok, Banshee or Exaile. And I hate the likes of XMMS and Audacious.

I've used **foobar2000** through wine for a long time because it's the best player on the planet, but I was hoping to get something **more native**.

**Rhythmbox** is kinda nice because it's so **integrated** with Ubuntu and has plenty of development. But it's just playback, two universes away from foobar2000 in every other field.

So now I listen with Rhythmbox and I 'manage' [SIZE="1"](tag/rename/etc)[/SIZE] with foobar, but I have this annoying feeling that Rhythmbox runs on a virtual machine or something because [SIZE="3"]on my very much older Pentium 3 that acts as a jukebox, foobar is still lightningfast but Rhythmbox chokes left and right on the same big lists of music.[/SIZE]

---

### Post by DoktorSeven on 2011-03-15
The above-mentioned DeaDBeeF is nice and Foobar-like.

---

### Post by gtzam on 2011-03-16
[DeadBeef]("http://deadbeef.sourceforge.net/") is also my choice due to excellent cue sheet support and low resources usage.

---

### Post by Redsandro on 2011-03-16
I recognize the screenshots and the name, I think I've already tried it. But I cannot remember what was the problem for me. Was it the player with the separate component for playback itself?

I also tried Ario, looks nice but I had a frustrating user experience. Audio players are supposed to be somewhat intuitive and 'just work' but I couldn't get this one to import my music. It shouldn't be a hard task. :mad:

BTW gotta love that Jamendo component in Rhythmbox! :D

---

### Post by DoktorSeven on 2011-03-16
> **Redsandro said:**
> I recognize the screenshots and the name, I think I've already tried it. But I cannot remember what was the problem for me. Was it the player with the separate component for playback itself?

You're probably thinking of mpd or xmms2, both of which run in the background and use clients to connect to them.  DeaDBeeF is a standard audio player.

---

### Post by Redsandro on 2011-03-17
> **DoktorSeven said:**
> The above-mentioned DeaDBeeF is nice and Foobar-like.
> **gtzam said:**
> [DeadBeef]("http://deadbeef.sourceforge.net/") is also my choice due to excellent cue sheet support and low resources usage.

Wow it has more features than I initially thought. Sounds like a slim player to me, but I haven't tried this on old hardware or big playlists yet. Either I was confused, or there was another problem when I tried it on my laptop [SIZE="1"](am now on a different computer)[/SIZE].

How come this isn't more popular, in a wikipedia article or even in the standard repository when there's actually a lot worse crap that is?

For personal reference because I need to try this on my laptop:
```
sudo add-apt-repository ppa:alexey-smirnov/deadbeef
sudo apt-get update
sudo apt-get install deadbeef
```

-edit-

Maybe because only 1 person works on it, last version is 9 months old and community development is nonexistent. Shame.

11011110101011011011111011101111

---

