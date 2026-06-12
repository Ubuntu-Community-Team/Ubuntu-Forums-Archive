---
title: "MP3 ID tags"
date: 2005-12-09
forum: General Help
---

### Post by xmastree on 2005-12-09
I have a bunch of files, which had no tags. Since they were all named similarly, I decided to <very small voice> reboot into windows and use misikcube </vsv> to tag them. Select all, tell it that they're $TRACK - $ARTIST - $TITLE and it does the rest. Then Ctrl-Shift W and it auto capitalises and removes extra whitespace. Very slick.

Anyway, to the point. Playing the files in Beep, the playlist shows the correct data (i.e. not just the filename) but Alt-I doesn't show the tag (screenshot 1).

Xmms does (screenshot 2). So does Rhythmbox.

Command line programs also show it correctly:
```
chris@ubuntu:/mnt/windisk/MP3/Top 500 rock - cd 1 (1-100)$ id3 -l 063\ -\ Fleetwood\ Mac\ -\ Rhiannon.mp3
063 - Fleetwood Mac - Rhiannon.mp3:
Title  : Rhiannon                        Artist: Fleetwood Mac
Album  : Top 500 rock CD1                Year: 0   , Genre: Unknown (255)
Comment:                                 Track: 63

chris@ubuntu:/mnt/windisk/MP3/Top 500 rock - cd 1 (1-100)$ id3ed -i 063\ -\ Fleetwood\ Mac\ -\ Rhiannon.mp3
063 - Fleetwood Mac - Rhiannon.mp3: (tag v1.1)
songname: Rhiannon
artist: Fleetwood Mac
album: Top 500 rock CD1
year: 0
comment:
tracknum: 63
genre: unknown(255)

```What's up with beep?

---

