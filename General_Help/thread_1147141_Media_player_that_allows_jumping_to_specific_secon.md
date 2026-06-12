---
title: "Media player that allows jumping to specific second"
date: 2009-05-03
forum: General Help
---

### Post by andreseso on 2009-05-03
Hello,

I have two interviews I want to transcribe.  One in video and one in audio.  I will need a media player that allows me to jump to a specific time in the media file.  Say I transcribe a line and this line finishes 10 minutes and 49 seconds into the file.  I would like something that allows me to jump 10 minutes and 50 seconds into the file so I can continue transcribing.

Love,
Andres

---

### Post by akoskm on 2009-05-03
VLC media player (available in synaptic).
It has an option Playback-> Go to Specific Time.
Hope that helps.

---

### Post by geirha on 2009-05-03
I'm fond of [mplayer](apt:mplayer)

You can jump to a specific point in the file from the command-line

```

# Jump to 10 minutes and 50 seconds into the file
mplayer -ss 10:50 audiofile.ogg
# Jump to 10 minutes and 50 seconds into the file, and play 20 seconds
mplayer -ss 10:50 -endpos 20 audiofile.ogg

```

---

### Post by soro2005 on 2009-05-03
You may want to consider real transcription software. For audio, you might look into [Express Scribe](http://www.nch.com.au/scribe/) (free as in beer, not speech). For video, it's a little tricky. I use [Transana](http://www.transana.org), but it's not packaged for Linux and works only more or less so far. It requires some heavy tweaking. There is other software out there, most of it, I guess, for serious academic business. Perhaps it's worth the extra step to extract the audio and transcribe it with Express Scribe.

The point is that, what you seem to describe you want to do (use a regular media player to jump back and forth in the file) is the definition of "a pain in the butt." Depends, of course, how meticulous you want to be, but if your transcript is supposed to be more than what you pick up on the first go, then you need software which lets you halt and jump back a little on a keystroke.

---

### Post by andreseso on 2009-05-03
> **soro2005 said:**
> You may want to consider real transcription software. For audio, you might look into [Express Scribe](http://www.nch.com.au/scribe/) 

The point is that, what you seem to describe you want to do (use a regular media player to jump back and forth in the file) is the definition of "a pain in the butt." 

Thanks a lot.  I have no experience in transcribing stuff.  At once I am looking into Express Scribe.

Love,
Andres

---

