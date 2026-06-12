---
title: "Converting M4A, preserving sound and tags?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by Sephiriz on 2005-08-15
As many of you probably know, amaroK has NO support for m4a tags, and as such, any m4a songs will not be added into the collection.  Many other music players do support m4a songs and their tags, but none of these players, in my opinion, rival amaroK in quality and comfort of use.

So, I was wondering, is there a way to convert my m4a songs into another encoding, while preserving sound quality and meta information?

Thank you in advance.

---

### Post by Bo Rosén on 2005-08-16
I'm definitetly not an expert on these things, but converting between **any** lossy file formats will reduce sound quality. Perhaps you could convert to FLAC somehow?

---

### Post by nwillis on 2005-08-16
I'd like to point out that everyone knows converting between lossy formats may involve some quality loss; that was not the question.

This ain't a perfect world.  Not all devices play all audio types.  Not all software plays all audio types.  Telling the original poster that he shouldn't ask the question is unhelpful; he needs to convert the audio, if you can't help him do that then telling him you don't think he should is worse than offering no answer at all.

Besides, when people give me audio in some unplayable format that I have to convert to MP3 for car usage or whatever, the format change is easily worked-around by upsampling to a much higher bitrate; any quality loss from double-encoding is minimized in this process and when you have no other choice the extra space is an excellent trade-off.

To the original poster; I hope you get a real answer, I'm sorry I don't have one.  I've been searching the archives recently myself and no one seems to have anything constructive to add.

Right now, it looks like my choices for playing some M4A's are recompiling Muine -- and by extension, Mono -- for myself on AMD64 since there's no package, waiting around with crossed fingers for the new version of Rhythmbox in case they actually made an improvement to it (there's a first time for everything), or finding a conversion process.  No luck yet.  Some chatter suggests that Mplayer can play them -- and thus might be able to extract them to raw audio format -- but Mplayer is a horrific interface that I swear was designed by illiterate sadists who seek thrills by preventing people from playing their media files.

Sorry; been one of those days, and those "that's stupid, why would you want to" replies to honest support-forum questions *really* get under my skin.  I'll post something better when I find out more.

n

---

### Post by Sephiriz on 2005-08-16
Thank you for the reply.  I also have Rhythmbox installed, and it can play and read m4a files perfectly fine, but it really isn't as comfortable to use as amaroK, and it also has various irritating aspects to it.

When you speak of extracting raw audio (I'm not very knowledgeable on matters concerning music and such), does that mean that if you can actually play the m4a song, you can store the output and just save it as another format?  It certainly sounds doable, I just wouldn't know how.

But once again, thanks for taking the time for this thread.  Although I'm no audiophile, I still enjoy getting the most out of my songs.  As a result, I'm willing to take minimal loss in sound quality, but a huge cut is something I wish to avert at all costs.

---

### Post by nwillis on 2005-08-16
Yeah, I meant "raw" as in uncompressed WAV or the like.  Here's a link I found that actually more or less works to do that:
[http://gimpel.gi.funpic.de/Howtos/convert_aac/](http://gimpel.gi.funpic.de/Howtos/convert_aac/) 

Good ol' straightforward MPlayer, huh.

Of course, this doesn't help with the tags.  There may be a way to write a shell script to do that (assuming mplayer can read the tags), like doing the AAC-to-WAV-to-MP3 and them pasting them at the last step, but I'm no scripter and like I alluded to before, MPlayer's default behaviour in every scenario is to crap out and quit, omitting all helpful debug information if possible.

I may try this then use a FLAC encoder just to keep the "hey you shouldn't transcode two lossy formats" whiners at bay.

Have you found anything that *reads* the tags in your files?  I don't even have something to do that yet.  That's probably because I'm on AMD64, which has more holes in it than Bonnie & Clyde.

N

---

### Post by Sephiriz on 2005-08-16
Well, like I said, Rhythmbox can read the m4a files, but if I recall correctly I had to go through hell and back to set that up.  It involved various gstreamer plugins, which I believe is the engine Rhythmbox uses (as well as amaroK), except Rhythmbox, unlike amaroK, had the capability to actually read the tags.

Thanks for the link, I suppose I might as well get cracking on the conversion.  If I stumble across anything, I'll let you know.

---

### Post by Bo Rosén on 2005-08-17
I'm sorry if my reply sounded offensive, that certainly wasn't my intention. But you are right nwillis, it could definitely have been more helpful than just suggesting converting to FLAC.

---

### Post by heimo on 2005-08-17
I haven't tried any of these, but maybe these are helpful?

[http://www.togaware.com/linux/survivor/m4a_mp3.shtml](http://www.togaware.com/linux/survivor/m4a_mp3.shtml)
[http://www.pangalactic.co.uk/downloads/m4a2mp3](http://www.pangalactic.co.uk/downloads/m4a2mp3)
[http://gimpel.gi.funpic.de/Howtos/convert_aac/](http://gimpel.gi.funpic.de/Howtos/convert_aac/)

---

### Post by nwillis on 2005-08-17
BoRosen,
 Nah, it didn't -- I was just (a) letting off a little steam and (b) hoping to prevent the discussion from getting derailed into a lossy-codec debate that would leave the original question unanswered.

---

### Post by nwillis on 2005-08-17
Heimo,

Hmm.  Well, I tried both of those new links (the third one was the same one I posted just above).  Neither of them worked.  Here's what happened --

The first, which uses faad and lame, spills out the warning
[INDENT]Warning: Pulse coding not allowed in short blocks[/INDENT] 

again and again.  I don't know what that means, nor whether it is output generated by faad or lame.  It does create an empty MP3 file corresponding to each M4A file in the current directory, though.

The second, which uses mplayer and lame, reports a lot more information and is obviously reading the tags right -- creates empty files again, although with EasyTag I can see that it does create ID3 tags properly for the empties (just no sound).

Maybe I will see if I can modify the second one to use oggenc and work right....

---

### Post by nwillis on 2005-08-17
Okay, I need a shell script doctor here.

Exploring m4a2mp3 script #2 from above, we have this section:
```

#attempt to convert m4a to wav.
                if mplayer -ao pcm "$fname" -aofile "$fname.wav" >/dev/null 2>&1
                then

                        #Convert WAVE to MP3 using lame
                        if lame -h -b 256 "$fname.wav" "$fname.mp3" >/dev/null 2>&1
                        then

``` ...etc, etc....

Can somebody tell me what the >/dev/null is supposed to be redirecting?  'Cause it sure looks like piping the output of these two conversions to /dev/null is generating an empty file.  What the crap good is that?

But the 2>&1 I recognize as being a stderr redirect; presumably taking this out would help debug the output.

Thoughts?  Divination?  Night school classes I can audit?
N

---

### Post by sciurus on 2006-01-05
[QUOTE=nwillis]Can somebody tell me what the >/dev/null is supposed to be redirecting?  'Cause it sure looks like piping the output of these two conversions to /dev/null is generating an empty file. 
[/QUOTE]

The output of the mplayer conversion goes to "$fname.wav" The output of the lame conversion goes to "$fname.mp3" The i/o redirection simply prevents any messages/errors from being displayed on the console.

---

### Post by sciurus on 2006-01-05
This script will convert all m4a in a folder to mp3, preserving tags. You need to install faad, lame, and id3v2 or id3. If you prefer id3 tags, uncomment that line and comment out id3v2. If anyone can improve my method for extracting the tags, please do. I stuck this in /usr/local/bin/m4a2mp3 and changed the permissions to 755. Put it in ~/.gnome2/nautilus-scripts and you'll able to execute it with a right-click in nautilus.

```

#!/bin/bash
for i in *.m4a
do
base=`basename "$i" .m4a`
info=`faad -i "$i" 2>&1`
artist=`echo "$info" | grep artist: | sed s/artist:\ //g`
album=`echo "$info" | grep album: | sed s/album:\ //g`
song=`echo "$info" | grep title: | sed s/title:\ //g`
track=`echo "$info" | grep track: | sed s/track:\ //g`
year=`echo "$info" | grep date: | sed s/date:\ //g`
genre=`echo "$info" | grep genre: | sed s/genre:\ //g`
faad -w "$i"| lame -h -b 128 - "$base.mp3"
#id3 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
id3v2 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
done

```

---

### Post by encompass on 2006-01-06
if you can play a file in gstreamer... can't anything that runs gstreamer play the m4u file?

---

