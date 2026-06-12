---
title: "what's wrong with my script"
date: 2008-12-30
forum: General Help
---

### Post by sn0m on 2008-12-30
This is my script:

#!/bin/sh
#-------------------------------------------------------------
# A very simple script to capture tar from Top Albania Radio:
#-------------------------------------------------------------
# Most of the variables:

DATE1=$(date +%d-%m-%Y)
DATE2=$(date +%Y)
FILE=/home/sn0m/Music/wake_up.$DATE1.mp3 # Where to save it
STREAM=http://tar.serverroom.us:9078/
DURATION=2h
MUSIC_DIR=/home/sn0m/Music

# For the id3v2 Tags
AUTHOR= "Top Albania Radio"
ALBUM= "tar stream rip"
TITLE= "wake_up-$DATE1"
COMMENT= "Morning show"

#-------------------------------------------------------------
cd $MUSIC_DIR

# Download the stream and convert it to wave format
#it needs to have -really-quiet option for cron to execute:

/usr/bin/mplayer -really-quiet -vc null -vo null -ao pcm:fast:waveheader:file=stream.wav "http://tar.serverroom.us:9078/" &

sleep $DURATION # Length of the program being recorded as background. 
kill $!         # End the most recently backgrounded job = mplayer

# Find the best volume adjustment and apply this to the wav file.

sox stream.wav -n stat > stats 2>&1 || exit 1
VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
sox -v $VOL stream.wav wake_up.wav || exit 1
rm stream.wav

# Convert to mp3
/usr/bin/lame -S -h -t -V 6 wake_up.wav wake_up.$DATE1.mp3 

# remove old tags from the resulting captured .mp3
/usr/bin/id3v2 -D wake_up.$DATE1.mp3

#new tags: 
   /usr/bin/id3v2 -a "$AUTHOR" \
  -A "$ALBUM"  \
  -t "$TITLE"  \
  -y "$DATE2"  \
  -c "$COMMENT" \
   wake_up.$DATE1.mp3 \
-------------------------------------------------------------------------------------    
# Clean up:

rm stats wake_up.wav



id3v2 dosen't want to write tags....
?any ideas...
ta
Sokol

---

### Post by dcstar on 2008-12-30
> **sn0m said:**
> This is my script:

......
#new tags: 
   /usr/bin/id3v2 -a "$AUTHOR" \
  -A "$ALBUM"  \
  -t "$TITLE"  \
  -y "$DATE2"  \
  -c "$COMMENT" \
**   wake_up.$DATE1.mp3 \**
-------------------------------------------------------------------------------------    
# Clean up:

rm stats wake_up.wav



id3v2 dosen't want to write tags....
?any ideas...
ta
Sokol

Why is there a continuation after the final line?

---

### Post by sn0m on 2008-12-30
> **dcstar said:**
> Why is there a continuation after the final line?

I've tried without a continuation, still dosen't work.

---

### Post by dcstar on 2008-12-30
> **sn0m said:**
> This is my script:
..........
id3v2 dosen't want to write tags....
?any ideas...
ta
Sokol

So what output is there when you run it in a terminal?

---

### Post by IcemanV9 on 2008-12-31
Try to remove "\" after mp3 & add "#" (see **bold**)

```
[snip]

wake_up.$DATE1.mp3

**#**-------------------------------------------------------------------------------------
# Clean up:

[snip]
```

---

### Post by sn0m on 2008-12-31
Oh I worked it out, so simple....
Apparently there should be no space after the equal sign in variables, now works as a charm.
thanks guys for all your help.
Sokol

---

