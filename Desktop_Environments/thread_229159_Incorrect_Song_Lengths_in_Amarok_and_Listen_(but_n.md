---
title: "Incorrect Song Lengths in Amarok and Listen (but not xmms)"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Third Thoughts on 2006-08-04
I've got a bunch of songs that both Amarok and Listen are giving incorrect song lengths for, usually 4 or 5 times longer than the actual length. XMMS however, gets the song length correct, though it usually jumps around when I first start playing a file. Listen refuses to play these files, while amarok plays them with no problems, except that it is difficult to seek.

What is important is the source of these files. All of them are audio tracks that I seperated out from a number of music videos I ripped from a DVD. I got the tracks off the DVD using a little script I wrote that taps the power of that wonderful app mencoder to create avi files for each title on the DVD. This is the important command from that script
```

mencoder dvd://$i -o $proj_dir/$i.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4 

```

Then I used mencoder and mplayer in a new script again to seperate out the audio. Here are the important commands from that script.

```

mencoder "$file" -oac mp3lame -o "$file".audio -ovc frameno
mplayer "$file".audio -dumpaudio -dumpfile "$base_name".mp3

```

Also odd is the fact that all players (xmms, amarok, listen, mpg123) claim the files are encoded at 32kbit/s, which my ear tells me they are certainly not. I'm no audiophile, but I can tell when music is encoded at 64, let all 32, as I'm sure most folks can.  

checkmp3 gives me the correct information for the song, but all of the songs seem a little bigger than I would expect. A 4:39 song, takes up 7.2M, a 4:43 8.4M. Anyone have an idea what's caused this. Is there a different set of commands I should be using to seperate out the audio from the video. I tried just using mplayer --dumpaudio alone, but it gave me something very strange that wasn't an mp3 (mpg123 wouldn't play it) and couldn't be converted with lame (just output a few 100k file that was random noise when mpg123 played it.)

~Andrew S.

---

### Post by Third Thoughts on 2006-08-04
I solved my own problem. The mencoder step I was using to seperate out the audio was not meant to do that. So instead I found the command ffmpeg which worked quite well. Here's the full command I used for those who are interested.

```

ffmpeg -i "$file" -acodec mp2 -ab 192 -f wav "$base_name".mp3

```

~Andrew S.

---

