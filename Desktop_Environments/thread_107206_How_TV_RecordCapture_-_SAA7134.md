---
title: "How TV Record/Capture - SAA7134"
date: 2005-12-22
forum: Desktop Environments
---

### Post by Beuntje on 2005-12-22
I want to capture/record from my tv card (Pinnacle PCTV Stereo) some tv shows.
I use TVTime to view, and this work ok. :) 

but how can a record/capture my TV Signals? :confused: 

I've tryed to use Zapping TV Tuner, but i'm only getting sound in that application, but no Picture.
Is there some setting for Zapping TV Tuner, or is there another easy to use program, for a linux n00b. :cool: 

TIA

---

### Post by Beuntje on 2005-12-22
mencoder -tv driver=v4l2:width=640:height=480:norm=pal:channel=43 -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 30 -o outfile.mpg tv://

This was the command which recorded my tv to a file.
But now how can I delay recording, because after 5 sec. the audio starts to play?

How can I delay the start of the recording? it must kick in after min 5 sec. because then the audio is recorded/played with this card.

---

### Post by egodust on 2006-01-31
I don't think you can :( mencoder options such as -ss or -sb don't work, I think the only option is to edit the file after the capture, with avidemux2 or some such.

---

