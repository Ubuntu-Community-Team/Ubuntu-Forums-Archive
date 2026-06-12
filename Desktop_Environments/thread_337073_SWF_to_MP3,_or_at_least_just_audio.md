---
title: "SWF to MP3, or at least just audio"
date: 2007-01-12
forum: Desktop Environments
---

### Post by Steve S. on 2007-01-12
I have some swf files that I want to convert just to the audio portion, preferably mp3 directly.

I know I can do this via Audacity, but I would rather it just straight extract the audio in some way, if that is possible, so I don't have to let it run and record it.  Besides, Audacity doesn't like me sometimes on Ubuntu (has issues with two seperate audio sources sometimes).

Anyone have any ideas?  Anything in synaptic that I missed?

---

### Post by dtfinch on 2007-01-13
I sometimes rip the audio from .flv (Flash video) files from sites like youtube and google video using "mplayer -dumpaudio", and it saves the raw .mp3 stream from the file without any transcoding.

I just tried the same method on a .swf file (a Happy Tree Friends episode) and it worked perfectly. I got all the audio as a single .mp3 file.

Example: mplayer -dumpaudio "Happy Tree Friends - Stayin Alive.swf" -dumpfile HappyTree.mp3

The resulting .mp3 files are usually a bit odd, in that players might guess the length wrong by a factor of 10 or so, but they're playable nonetheless.

I'm not sure if you need to install the win32 codecs just to strip out the audio without any real decoding. You might.

---

### Post by Steve S. on 2007-01-13
> **dtfinch said:**
> I sometimes rip the audio from .flv (Flash video) files from sites like youtube and google video using "mplayer -dumpaudio", and it saves the raw .mp3 stream from the file without any transcoding.

I just tried the same method on a .swf file (a Happy Tree Friends episode) and it worked perfectly. I got all the audio as a single .mp3 file.

Example: mplayer -dumpaudio "Happy Tree Friends - Stayin Alive.swf" -dumpfile HappyTree.mp3

The resulting .mp3 files are usually a bit odd, in that players might guess the length wrong by a factor of 10 or so, but they're playable nonetheless.

I'm not sure if you need to install the win32 codecs just to strip out the audio without any real decoding. You might.

I'll give it a try!  I already have the win 32 codecs...don't sweat it.  You typing that mplyaer line in command?  Never tried that, although I use mplayer all the time...

And I tried to pull the swf files off of Firefox, but I apparently did something wrong.  Know the best way to take an swf file off a site?

Thanks for the idea, either way..

---

### Post by dtfinch on 2007-01-13
I'd get the .swf url from the html source and download it using wget from the command line. It gets more difficult if the flash file references other files. For video sites like youtube there are sites to give you the correct url like _[this one](http://video.qooqle.jp/dl/)_.

---

### Post by SuperMike on 2007-01-13
[SIZE="2"]Try [**[COLOR="DarkOrange"]_this script_[/COLOR]**]("http://www.ubuntuforums.org/showpost.php?p=1949017&postcount=1").[/SIZE]

---

