---
title: "Rhythmbox mutes when playing a certain song"
date: 2006-01-23
forum: Desktop Environments
---

### Post by Breepee on 2006-01-23
I've a weird problem: I've Rhythmbox setup with a 7725 song database. Indexing took a while but works perfectly (only problem: it gives an error on a 300MB MP3 audiobook of about 10 hrs).

The files are mostly FLAC, a lot of MP3, some Ogg Vorbis and a few Musepack (~110GB total). My audiocard is a Hercules Fortissimo 4, which is based on a VIA Envy24HT chip. Works fine, apart from software volume control (that's no problem, I use my amp).

When I select a certain Ogg Vorbis file (11 minutes, Q6 or something) to playback to sound of Rhythmbox sorta mutes. It does play, and when I turn the volume (with my amp) all the way up, I can hear it very softly. If I select a different song, they're also 'muted'. Ubuntu system sounds play like normally and if I restart Rhythmbox it's 'fixed', until I play that specific song again.

Anyone knows what's going on and possibly how to fix it? Thanks.

---

### Post by doclivingston on 2006-01-23
[QUOTE=Breepee]When I select a certain Ogg Vorbis file (11 minutes, Q6 or something) to playback to sound of Rhythmbox sorta mutes. It does play, and when I turn the volume (with my amp) all the way up, I can hear it very softly. If I select a different song, they're also 'muted'. Ubuntu system sounds play like normally and if I restart Rhythmbox it's 'fixed', until I play that specific song again.[/QUOTE]

Do you know if the file(s) contain ReplayGain tags? If so, Rhythmbox will adjust the volume of the track according to them, which usually makes it quieter.

If that is what is causing it, then your two options are a) give the others replaygain tags, so they are all the same volume, or b) remove them from the ones that have them.

---

### Post by Breepee on 2006-01-24
The entire collection has ReplayGain tags. The specific song has normal tags; no extreme dB-values.

---

### Post by Breepee on 2006-01-25
It plays fine with foobar under Windows.

---

### Post by Breepee on 2006-01-26
Can someone help me?

---

### Post by doclivingston on 2006-01-26
I've just remembered about a Rhythmbox bug, which was in the version that shipped with Breezy (it was fxed in 0.9.2). If the song needs to be made over four times louder, it won't get made louder at all (and so it will be *really* quiet).

Aside from upgrading, about all you can do lower Rhythmbox's volume slider, and turn up the system volume/external speaker volume to compensate.

---

### Post by Breepee on 2006-01-27
replaygain_track_gain = -1.14 dB
replaygain_track_peak = 1.028782
replaygain_album_gain = -7.60 dB
replaygain_album_peak = 529.137817

This is the replaygain info on the file. The volume slider in RB does not work. Compensating with the external amp is not possible, all the way up it's still very soft.

---

### Post by doclivingston on 2006-01-27
[QUOTE=Breepee]replaygain_track_gain = -1.14 dB
replaygain_track_peak = 1.028782
replaygain_album_gain = -7.60 dB
replaygain_album_peak = 529.137817[/quote]

Ah, this is a quiet song on a relatively loud album. Rhythmbox uses album-gain if it is present, which makes it really quiet. Aside from removing the album-gain tag, I'm not really sure how to fix it.

---

### Post by Breepee on 2006-02-05
I've discoverd yet another file, an MP3 this time, which exhibit's the same behaviour. It too has relatively low replaygain settings. Strange that it doesn't 'reset' when playing another file (shutting down and starting up rhythmbox with 7731 files on a P3 450 isn't fun). Anyway to completely disable replaygain?

---

### Post by Breepee on 2006-02-10
Any idea?

---

