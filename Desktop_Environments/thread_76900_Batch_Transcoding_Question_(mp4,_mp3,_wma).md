---
title: "Batch Transcoding Question (mp4, mp3, wma)"
date: 2005-10-15
forum: Desktop Environments
---

### Post by sinbad782 on 2005-10-15
I have quite a large and very messy collection of various wma, mp3, and mp4 files which comprise my CD collection that I ripped using various programs under Win XP. I recently copied the data from my XP partition into my home directory in my Ubuntu partition. 

I would like to standardise this lot into one format, say mp3 or ogg. I am not particularly sensitive to issues around lossless vs lossy codecs, sound quality etc.

What I need is for the transcoded music files to be widely supported on as many portable music players as possible and so realistically, I am probably looking at converting to mp3 over ogg. 

Do any of you know of a  good app that would do this under linux? - it will need to be quite intelligent as there is a ton of other stuff in the music folders along with the actual audio files themselves (cd covers, thumbs.db files, playlist files etc.) and should be able to recursively work through the directories transcoding everything.

I know there is DBPowerAmp Music Converter that will do this under Windows, but I'd love to hear recommendations for an equivalent app for Linux. 

Many thanks, PJS

---

### Post by ewtesterman@cox.net on 2005-12-02
I am facing the same problem here. I have about 1.5 gig of Video I shot while in the service and about 2 gig of music all in wma, avi, and other Windows file formats. I have been able to play these in Ubuntu with once I installed the codec (in which I found several viruses), but I would like to move these to an open file format and preferable without spending hours of point and click, I am hoping that there is something that can find and covert these files with little effort on my part.

---

### Post by tarheelcoxn on 2006-02-07
Howdy guys. First post here. :) I'm in the same boat, but I've got some suggestions. It looks like people have already built some tools [like this audio converter]("http://freshmeat.net/projects/audio-convert/").

You had mentioned that you wanted something that would traverse directories recursively. I think it would be fairly trivial to take an existing script like [this space replace script]("http://www.spinningstone.com/spacereplace.php") as a model and write a wma-to-ogg script.

If I manage it I'll post back here. If somebody else gets there first, please do post here.

---

### Post by tarheelcoxn on 2006-02-08
Just found "soundconverter" in the repo. The manpage says it has a batch mode. Hasn't worked for me yet, but might be worth a shot.

---

