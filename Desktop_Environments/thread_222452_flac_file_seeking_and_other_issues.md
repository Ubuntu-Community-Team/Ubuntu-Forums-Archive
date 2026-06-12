---
title: "flac file seeking and other issues"
date: 2006-07-25
forum: Desktop Environments
---

### Post by jsma on 2006-07-25
Hello,
I've had a few issues since converting my WMA Lossless music libary to FLAC. Some files were given id3v2 tags, which for whatever reason makes the files appear to Linux as MIME type mp3. 

Does anybody know why this is? I assumed that the tags were just some sort of text/xml-ish wrapper around a binary file, I didn't think that the tag would determine MIME type.

I use Amarok 1.4.1 from the KUbuntu repos with the xine engine, xine-extracodecs and w32codecs installed. MP3's play back fine, but FLAC's with id3v2 tags do not playback at all. Does anyone know why this is the case? I seem to remember these same files playing fine in XP. For now, I used EasyTag to strip all the tags off my FLAC files and replace them with barebones FLAC vorbis tags (what a handy tool EasyTag is for a chore like that!). 

Now playback works fine. However, somewhere in this process these files are not seekable (maybe they never were). If I try to skip forward, sometimes it restarts from the beginning and other times playback stops altogether. 

After doing some research at [http://flac.sourceforge.net/documentation.html#metaflac]("http://flac.sourceforge.net/documentation.html#metaflac") I found that the 'metaflac' command line utility allows you to add seekpoints. I installed the 'flac' package from synaptic to get this utility. So far I've been able to get this command to work succesfully on individual files. 

I would like some help writing a shell script to automate this process as I have thousands of flac files I'll need to do this for. I tried several different scripts (knowing next to nothing about the syntax or keywords). My music folder hierarchy follows a consistent pattern "/music/Artist/Album/01.track.flac" and I can get the metaflac command to work from within any /Artist directory (adding seekpoints to all files in each of the /Album directories):
```
metaflac --add-seekpoint=1s */*.flac
```
This adds a seekpoint at 1 second intervals. This may be overkill, the example at flac.sourceforge.net used 3.5s intevals. But this setting works just fine and seeking is fairly smooth. Besides, I like putting my dual core cpu to work.
I'd like to make a shell script that will cd into each artist directory and then run the above command, cd back out and then cd into the next artist directory. Any tips? I have spaces in artist names rather than underscores (eg, 'Yo La Tengo' rather than 'Yo_La_Tengo') and this appears to matter. Some of my attempts at making a script complained that the first word before the space (eg 'Yo') wasn't a directory, so apparently I need to account for this in the script. I've seen others have had problems seeking with flac files, so maybe this sort of script could be useful to others...it would be nice if the various flac enabled rippers or tag editors had '--add-seekpoint' enabled (with sensible defaults), but that's another issue.

Thanks for any and all tips, and I hope that this benefits others who've had similar issues.

Cheers

---

### Post by simonn on 2006-07-25
KDE is for girls, so I don't know Amerok. However, flac is my codec flavour of choice.

Basically I suspect the seek thing is a bug with AmaroK or xine.

Actually, what do you mean by seek exactly? Fast forward? Seek next track?

Try using XMMS with the flac plugin, I have found this to have the best flac support.

In answer to you question...

```

find -name "*.flac" -printf "[command] \"%P\"\n" | sh

```

Replace [command ] with the command you want to use. \"%P\" will expand to the path and filename of each file that matches the pattern *.flac in the tree starting from the current directory.

---

### Post by jsma on 2006-07-25
by 'seek' I mean drag the progress slider forward or backwards to skip to a different point in the song...not something I use all the time, but sometimes i want to listen to a passage more closely or whatever. i'll give your command a try. and it's not a bug in amarok, but it looks like xine is the one having the problem...vlcplayer seeks just fine on file x.flac but gxine or amarok both can't seek on x.flac until I do the metaflac --add-seekpoint trick. Hmm, curious and annoying. I'm sticking with Amarok for now, as it is the only media player with a good library manager I've found in Linux.

---

### Post by jsma on 2006-07-25
UPDATE:
I just got home from work, I left my machine running the command based on your suggestion and it worked for everything except one directory. This directory structure is like /Orlando "Cachaito" Lopez/Cachaito/*.flac and it gave me the following error:
```
The FLAC file could not be opened.  Most likely the file does not exist or is not readable.
Orlando Cachaito Lopez/Cachaito/03.Mis Dos Pequeñas.flac: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"
```
However, I just manually cd into the album directory and ran metaflac for *.flac and it didn't complain. So I'm assuming there was a problem with the quotes around "Cachaito" or something. Whatever the case, my flac files are now in fine form and work perfectly in Amarok/xine-engine. Thanks for the tip.

---

### Post by aay on 2006-09-11
JSMA, thanks for the tip on metaflac.  I was having trouble getting flac to work at all in Amarok and then I discovered the patched version of xine floating around out there that fixes playback.  I was still having problems with seeking until I found your post.  Metaflac to the rescue.  Still, I hope this problem is fixed in future versions of xine.  Other engines seem to have no problem seeking flac files.

Thanks again.

Adam

> **jsma said:**
> Hello,
I've had a few issues since converting my WMA Lossless music libary to FLAC. Some files were given id3v2 tags, which for whatever reason makes the files appear to Linux as MIME type mp3. 

Does anybody know why this is? I assumed that the tags were just some sort of text/xml-ish wrapper around a binary file, I didn't think that the tag would determine MIME type.

I use Amarok 1.4.1 from the KUbuntu repos with the xine engine, xine-extracodecs and w32codecs installed. MP3's play back fine, but FLAC's with id3v2 tags do not playback at all. Does anyone know why this is the case? I seem to remember these same files playing fine in XP. For now, I used EasyTag to strip all the tags off my FLAC files and replace them with barebones FLAC vorbis tags (what a handy tool EasyTag is for a chore like that!). 

Now playback works fine. However, somewhere in this process these files are not seekable (maybe they never were). If I try to skip forward, sometimes it restarts from the beginning and other times playback stops altogether. 

After doing some research at [http://flac.sourceforge.net/documentation.html#metaflac]("http://flac.sourceforge.net/documentation.html#metaflac") I found that the 'metaflac' command line utility allows you to add seekpoints. I installed the 'flac' package from synaptic to get this utility. So far I've been able to get this command to work succesfully on individual files. 

I would like some help writing a shell script to automate this process as I have thousands of flac files I'll need to do this for. I tried several different scripts (knowing next to nothing about the syntax or keywords). My music folder hierarchy follows a consistent pattern "/music/Artist/Album/01.track.flac" and I can get the metaflac command to work from within any /Artist directory (adding seekpoints to all files in each of the /Album directories):
```
metaflac --add-seekpoint=1s */*.flac
```
This adds a seekpoint at 1 second intervals. This may be overkill, the example at flac.sourceforge.net used 3.5s intevals. But this setting works just fine and seeking is fairly smooth. Besides, I like putting my dual core cpu to work.
I'd like to make a shell script that will cd into each artist directory and then run the above command, cd back out and then cd into the next artist directory. Any tips? I have spaces in artist names rather than underscores (eg, 'Yo La Tengo' rather than 'Yo_La_Tengo') and this appears to matter. Some of my attempts at making a script complained that the first word before the space (eg 'Yo') wasn't a directory, so apparently I need to account for this in the script. I've seen others have had problems seeking with flac files, so maybe this sort of script could be useful to others...it would be nice if the various flac enabled rippers or tag editors had '--add-seekpoint' enabled (with sensible defaults), but that's another issue.

Thanks for any and all tips, and I hope that this benefits others who've had similar issues.

Cheers

---

### Post by jsma on 2006-09-11
Glad the post was of some help. I refer to it myself on occassion as I have to 'metaflac' -ize any new flac files I add to my library. An annoyance, but easy to work around. I like the gapless audio support of xine + amarok. Unfortunately it always cuts off the last couple of seconds if it's the last song in the playlist. Other than that, it's been a perfect combo for me (listening right now...)

j-s

---

