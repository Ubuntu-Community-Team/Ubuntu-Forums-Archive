---
title: "converting video formats"
date: 2006-08-19
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-19
I used mencoder to convert a MOV quicktime movie to AVI format. The AVI format is huge, maybe 25 times bigger than the quicktime format. How can I convert it to a compressed format that will play in Window's media player? No, I am not using Window's media player. I need to put my movies on the web, and I want a format that will play in most web browsers without installing extra software.

---

### Post by Ubuntu Joe on 2006-11-15
Ba-BUMP-bump . . .

---

### Post by benp on 2006-11-15
The online manual for mplayer/mencoder is excellent. See the following:
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-selecting-codec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-selecting-codec.html)

You probably want something like

mencoder -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -o outfile.avi infile.mov

But I haven't tried that so I can't guarantee it works. You might need to fiddle with the bitrate to get the quality and file size reasonable. Look around the mplayer manual to figure out how to do that -- post back if you run into trouble. As another example, here's the command I use for converting divxes to DVD format:

mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,\
harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:\
vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:acodec=ac3:\
abitrate=192:aspect=16/9 -ofps 25 \
-o movie.mpg movie.avi

---

### Post by Marsolin on 2006-11-16
> **fakie_flip said:**
> I used mencoder to convert a MOV quicktime movie to AVI format. The AVI format is huge, maybe 25 times bigger than the quicktime format. How can I convert it to a compressed format that will play in Window's media player? No, I am not using Window's media player. I need to put my movies on the web, and I want a format that will play in most web browsers without installing extra software.

AVI is a wrapper, not a format. It's possible that you didn't use the best codec. I'd try Xvid since it's open source and can easily be run on any OS.

---

### Post by Aurdal on 2007-01-02
Sorry for digging this up, but is there anyway to convert from AVI to MOV?

---

### Post by Marsolin on 2007-01-02
> **Aurdal said:**
> Sorry for digging this up, but is there anyway to convert from AVI to MOV?

I haven't seen anything to indicate that any of the usual converters can creat MOV files, but I've heard that [Cinelerra]("http://linuxappfinder.com/package/cinelerra"), [Kino]("http://linuxappfinder.com/package/kino"), and [LiVES]("http://linuxappfinder.com/package/lives") can. Kino needs some special configuring though. All three of those programs are video editors.

---

