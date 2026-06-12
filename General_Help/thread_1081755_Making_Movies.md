---
title: "Making Movies"
date: 2009-02-26
forum: General Help
---

### Post by Silvernail on 2009-02-26
I need some help. I don't find a forum for 'mplayer' to ask questions.
I  have read:
> 

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html) til I'm blue in the face and completely confused.

I have downloaded some cassette tapes using this command
>  cat /dev/video0 > test.mpg 

When I play it using 'mplayer' this line is displayed.

> VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)

Then I use 'gimp' to create a title page. Use 'gimp-GAP' duplicate frame to make a hundered copies.
Then I use
> mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc copy -oac copy -o output.mpg
to make them into a movie clip.

When I play it using 'mplayer' this line is displayed.

VIDEO:  [MPNG]  720x480  24bpp  25.000 fps  72696.9 kbps (8874.1 kbyte/s)

Then I try to join them using

> mencoder -ovc copy -oac copy -o out.mpg file1.mpg file2.mpg

I get errors telling me the bitrate, fps, resolution, format must be the same.
I have played around with -vbitrate but seem to make matters worse and no joy.

Is there a howto somewhere that is more understandable for the lay person than the one on the 'mplayer' website?

TIA
Dave

---

### Post by mb_webguy on 2009-02-26
What exactly are you trying to do?  While you say what you're *doing*, you never say what you *want* to do.

---

### Post by Silvernail on 2009-02-26
You're right. Thats what happens when you think about something too long. Loose focus.

I have ripped the tapes. Now I want to create a title page and an ending page for them and connect all three together and burn a DVD.

---

### Post by mb_webguy on 2009-02-26
Okay, now that I have some context let's see what I can do...

So your problem is joining the title clip and the credits clip to the main video, because the bitrate, fps, resolution, and/or format don't match.

Well, the first thing I notice is that the command you're using to convert the jpg files into a video is specifying 25 fps, while the original video is 29.970 fps.  So try changing the fps option to 29.970, and if that doesn't work try 30 (which I think may be how you'd specify 29.970).

The bitrates also don't match, but that could be fixed with the change of the framerate.  If not, you'll need to use something like the "-mpegopts" option with a value for vbitrate.

Personally, though, I'd use Avidemux to splice the videos together.  It will do a lot of this sort of thing for you, and it's easier than sorting through page after page of mencoder documentation for the specific options you need to do what you want to do.

---

### Post by Silvernail on 2009-02-28
Thanks for the reply.

I spent some  time yesterday playing with Avidemux.  It wants to index the videos and then later can not load the video it indexed.

I am ripping today, Will work with mencoder tomorrow.

Reports later in the week.

Thanks again.
Dave

---

### Post by ad_267 on 2009-02-28
You could also try kino.

---

### Post by Silvernail on 2009-03-01
On a side note to  this thread, I used the command line
```
cat /dev/video0 > test.mpg
``` to download from tape to disk.

I used the extension 'mpg' because that is the only way I have seen this example. WHY? Is that the format that the video recorder uses and the tape is saved with?

---

