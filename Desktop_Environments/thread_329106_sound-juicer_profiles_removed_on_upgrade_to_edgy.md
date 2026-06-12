---
title: "sound-juicer profiles removed on upgrade to edgy"
date: 2006-12-31
forum: Desktop Environments
---

### Post by glenndavy on 2006-12-31
I just upgraded a machine from dapper to edgy and now sound juicer had no profiles?!? I've entered some manually, but sound-juicer just crashes when it starts to rip. Any idea how I can have the correct profiles automatically re-installed?

thx
glenn

---

### Post by nexu56 on 2007-01-13
I'm not sure if its exactly what you're after, but here's what I use to quickly add MP3 profiles via LAME, if they should happen to vanish.

```
mkdir ~/.gconf/system/gstreamer/0.10/audio/profiles/MP3@32@128Kb
gconftool-2 -t bool --set /system/gstreamer/0.10/audio/profiles/MP3@32@128Kb/active 1
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@128Kb/description "Encodes at 128Kb (variable bitrate) via LAME MP3 encoder"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@128Kb/extension "mp3"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@128Kb/name "LAME MP3 128Kb"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@128Kb/pipeline "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=128"
mkdir ~/.gconf/system/gstreamer/0.10/audio/profiles/MP3@32@192Kb
gconftool-2 -t bool --set /system/gstreamer/0.10/audio/profiles/MP3@32@192Kb/active 1
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@192Kb/description "Encodes at 192Kb (variable bitrate) via LAME MP3 encoder"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@192Kb/extension "mp3"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@192Kb/name "LAME MP3 192Kb"
gconftool-2 -t str --set /system/gstreamer/0.10/audio/profiles/MP3@32@192Kb/pipeline "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192"
gconftool-2 -t list --list-type string --set /system/gstreamer/0.10/audio/global/profile_list "[MP3@32@192Kb,MP3@32@128Kb,voicelossy,voicelossless,cdlossy,cdlossless]"
```

cheers

---

