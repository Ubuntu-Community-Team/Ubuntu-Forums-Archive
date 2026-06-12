---
title: "Looking for a .psf player for Linux"
date: 2008-08-11
forum: Gaming &amp; Leisure
---

### Post by chicobo329 on 2008-08-11
I have a bunch of Playstation Sound Format (.psf/.psf2) soundtracks on my hard drive here, although I haven't found a .psf player to play them yet. Does anyone know where I can find a good player for this?

---

### Post by tuxxy on 2008-08-11
This lnik may be useful

[http://ubuntuforums.org/showthread.php?t=272859](http://ubuntuforums.org/showthread.php?t=272859)

---

### Post by chicobo329 on 2008-08-11
I did try XMMS but there seems to be a '2' version now and no longer the old XMMS (the Highly Experimental plugin doesn't seem to work for XMMS2, unless I'm missing something). Is there another option?

---

### Post by FranMichaels on 2008-08-11
Yes. [Audacious]("http://audacious-media-player.org/"). It is in the repos, make sure to install the audacious-plugins-extra package as well as upse.

Also, the next release has support for psf2 (if you are impatient you can build the svn release...)

---

### Post by chicobo329 on 2008-08-11
Audacious works like a charm! There's just one thing though, it's small however. Is there a way I can make the .psfs play forever? Highly Experimental on Winamp allows this, although this psf plugin doesn't seem to have any preferences.

---

### Post by FranMichaels on 2008-08-11
No problem.

Press R or click the little repeat button logo.

---

### Post by hessiess on 2008-08-11
why not re-encode them into FLAC or something, ffmpeg may be able to do this.

---

### Post by FranMichaels on 2008-08-11
> **hessiess said:**
> why not re-encode them into FLAC or something, ffmpeg may be able to do this.

My reasons against such a thing:

One, no ffmpeg can't. 
Two, audacious could, using its disc writer plugin. 
Three, for example, the entire sound track of FFVII, which is 4 CD's worth of audio is 821kb (less than 1 megabyte in psf format! If this is hard to imagine, the music is sequenced, like that of a midi. A FLAC recording of a midi would be hundreds or thousands of time larger at identical quality. Even encoding to lossy wouldn't be that much better.) 

More about [psf]("http://en.wikipedia.org/wiki/Portable_Sound_Format")

Formats both streamed and sequenced that [audacious can play]("http://audacious-media-player.org/index.php?title=Features")

If you want to use these formats on a portable player, look into [rockbox]("http://www.rockbox.org/twiki/bin/view/Main/SoundCodecs#Other_Codecs")

- my 2 cents :popcorn:

---

### Post by chicobo329 on 2008-08-11
I didn't mean for Repeat, I meant having the track go on and on. .psfs can do this, I know Highly Experimental let you have a track play forever (it'll play on and on longer than its intended length). I guess an example of what I mean is playing an .spc file on Totem, as it'll just keep playing with no end. That's what I mean right there. I guess that's a stream right? How can I make Audicious play .psfs like that?

---

### Post by FranMichaels on 2008-08-11
> **chicobo329 said:**
> I didn't mean for Repeat, I meant having the track go on and on. .psfs can do this, I know Highly Experimental let you have a track play forever (it'll play on and on longer than its intended length). I guess an example of what I mean is playing an .spc file on Totem, as it'll just keep playing with no end. That's what I mean right there. I guess that's a stream right? How can I make Audicious play .psfs like that?

If you load one psf file, repeat would do you what you want. AFAIK there is no option to ignore the song length for psf's in audacious. You could request the feature if you think repeat or adding the same song to the playlist isn't enough... 

Funnily enough, spc playback under Audacious has the option to ignore song lengths (game audio console music decoder, under Preferences -> Plugins...

---

### Post by disturbedite on 2008-08-11
yeah, there is a plugin for audacious that will meet this need.

also, there is AudioOverload. it is actively developed by richardbannister & rbelmont. (it isn't open source yet though).
it is an audio player geared towards playing game audio formats of all kinds.

---

### Post by wingnux on 2008-08-11
The latest version of AudioOverload is pretty cool, I higly recommend it.

---

### Post by FranMichaels on 2008-08-11
Audioverload...
They have released some source code, part of which was used to make a psf2 plugin for the next Audacious. 
The only thing I have against Audioverload is the intefrace and the sound quality. Compare for example the Chocobo Racing psf. 

On the other hand, installing both players isn't a problem.

---

### Post by disturbedite on 2008-08-12
i have to remind everyone of what i already said in my first post. AO is geared/focused toward playing game audio formats and *nothing else!* that is why the GUI leaves much to be desired.

that is what i was told by rbelmont himself when i commented about it in it's forum.

---

### Post by chicobo329 on 2008-08-13
I gave AO a whirl for kicks but it doesn't seem to be playing any sound for me, and there's no real options menu or anything; very disappointing. I don't have problems with the interface at least, I like a simple design.

---

