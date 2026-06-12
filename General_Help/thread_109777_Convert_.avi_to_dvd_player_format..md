---
title: "Convert *.avi to dvd player format."
date: 2005-12-29
forum: General Help
---

### Post by chris_andrew on 2005-12-29
Hi, all.

Can anybody tell me whether it is possible to convert my avi files to a format that is playable on a standard dvd player, so that I can watch the files on a domestic tv, as opposed to my computer's monitor.

Cheers,

Chris.

---

### Post by FLeiXiuS on 2005-12-29
The way I do it is with WinAVI.  It's windows based program, but WINE takes care of that.  Really easy to install and I haven't had any problems with it.  

[http://www.winavi.com/](http://www.winavi.com/)

If anyone has any Linux solutions please inform me.  I'd rather have the GUI for this sort of transformation... 

I wonder if there is a front end for transcode?

---

### Post by chris_andrew on 2005-12-29
FL-ei-|X|-iu-S,

Thanks for taking the time to reply.  I switched to linux back in '98, so don't have any Windows software knocking around.  I'm afraid to say that I would prefer not to download any, either.

Thanks, again.

Chris.

---

### Post by chris_andrew on 2005-12-29
I also need to do the same with *.wav or *.ogg to mp3.  Any help would be greatly appreciated.

Thanks,

Chris.

---

### Post by FLeiXiuS on 2005-12-29
I would emulate windows DLLS's with wine-hq.  Wine-hq is a linux program which makes using windows programs without windows a hell of a lot easier.  I don't see why it would be a problem..but that choice is yours.

I would hook up wine then create a shortcut to the binary and away I go.  I don't even realize it's running through wine.  Looks / Executes the same.

---

### Post by FLeiXiuS on 2005-12-29
[QUOTE=chris_andrew]I also need to do the same with *.wav or *.ogg to mp3.  Any help would be greatly appreciated.

Thanks,

Chris.[/QUOTE]

I wonder if this is possible with the audio ripper that comes with Ubuntu.  Check the Sound and Audio tab under Applications and see what you can find.  If not I'll respond when I get off work.

---

### Post by chris_andrew on 2005-12-29
FLeiXiuS,

Thanks for your help.  I'll have a look at the audio stuff.  Hope work isn't too busy.

Cheers,

Chris.

---

### Post by chris_andrew on 2005-12-29
Hmmm, Sound juicer is ripping the CD to *.flac, I guess the next stage is to identify a .flac > .mp3 converter.


Update:

Just read Sound Juicer's help file, it looks like it can do MP3's, i'll let you know if it works.

---

### Post by FLeiXiuS on 2005-12-29
You can configure it to encode as an MP3.

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

[http://ubuntuforums.org/showthread.php?t=22010&highlight=sound+juicer+mp3](http://ubuntuforums.org/showthread.php?t=22010&highlight=sound+juicer+mp3)

---

### Post by chris_andrew on 2005-12-29
Got this error:

Sound Juicer could not extract this CD.
Reason: Could not create GStreamer encoders for MP3

Will have a look at your URL's and post my findings.

Cheers.

---

### Post by az on 2005-12-29
[QUOTE=FLeiXiuS]
If anyone has any Linux solutions please inform me.  I'd rather have the GUI for this sort of transformation... 

I wonder if there is a front end for transcode?[/QUOTE]


Gtranscode is made with gtk1.  


emma@ubuntu:~$ apt-cache show gtranscode
Package: gtranscode
Priority: optional
Section: multiverse/x11
Installed-Size: 96
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 0.3-0.0
Depends: libc6 (>= 2.3.2.ds1-4), libglib1.2 (>= 1.2.0), libgtk1.2 (>= 1.2.10-4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), transcode
Filename: pool/multiverse/g/gtranscode/gtranscode_0.3-0.0_i386.deb
Size: 18896
MD5sum: c1ef7af4a410277f3243e642995c8033
Description: GTK front-end for transcode
 Is a GTK+ GUI (graphical use interface) front-end for transcode in order to
 make this powerful tool easier to use.
 .
 [http://fuzzymonkey.org/newfuzzy/software/gtranscode/](http://fuzzymonkey.org/newfuzzy/software/gtranscode/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by Haegin on 2005-12-30
wav or ogg to mp3 can be handled by gnormalize but it is not reccommended to convert one lossy format to another (i.e. mp3 to ogg or vice versa. wav is fine) for converting the videos take a look at ffmpeg. It seemed to work when I used it last.

---

### Post by binks on 2006-05-20
[QUOTE=Human Prototype]wav or ogg to mp3 can be handled by gnormalize but it is not reccommended to convert one lossy format to another (i.e. mp3 to ogg or vice versa. wav is fine) for converting the videos take a look at ffmpeg. It seemed to work when I used it last.[/QUOTE]
  ok so how did you get winavi to install in ubuntu / it just hangs at the loading screen for me 
i followed the wine install howto with no prob ie ok and so is media player 
cheers binks
thats after the register screen thatis

---

### Post by adamkane on 2006-05-20
There are very good Linux ways to convert to DVD or MP3.

Video conversion:
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

Audio conversion:
[http://www.ubuntuforums.org/showthread.php?t=82806](http://www.ubuntuforums.org/showthread.php?t=82806)
Be sure to see Post 61.

---

### Post by unnes on 2006-05-20
I have had great success burning DVD movies using the Tovid GUI interface. I think it's available from one of the multiverse repositories, assuming youve edited your sources.list file.

---

### Post by rubengs on 2006-05-21
All is needed is: 

- avidemux or tovid: to convert avi to mpeg2, subtitles are supported in avidemux via a plugin and in tovid via command line.  

- qdvdauthor or DeVeDe to create your dvd, this last can transcode avi files on the fly and creates an ISO to burn your dvd, so maybe you just need this last one ;) .

---

### Post by Dantrag on 2006-05-21
Hey rubengs,
I downloaded DeVeDe and it tells me I need mencode. I installed mplayer which I  though contained mencode but it still tells me I need mencode. How do I get mencode? :-k

---

### Post by kevin_hill54 on 2006-05-22
Avidemux seems to do anything with an AVI file.

---

### Post by rubengs on 2006-05-22
I'm in dapper, don't remember if mencoder is in breezy repositories, I only had to run: 

sudo apt-get install mencoder-686

---

### Post by rubengs on 2006-05-22
avidemux is the best for me too.

---

### Post by binks on 2006-05-24
ok ok thanks all but tovid seems to be ok for me now althou in cmd line not the gui so maybe i have to look  at building a more appealing gui as by the tovid sites own admission the gui is unnatended atm
cheers binks

---

