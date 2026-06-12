---
title: "problem playing wmv's and streaming video"
date: 2006-05-09
forum: Desktop Environments
---

### Post by DarkManX4lf on 2006-05-09
ok i used automatix to install all the video codecs and the video players on ubuntu, all of them intstalled ok with no problems....but when i downloaded a wmv file i couldnt play it using any of the players installed (totem, mplayer), when i try to play it in totem it gives me this error:

Totem could not play "file://...."
Video codec 'MS WMV9 (win32)' is not handeld.  You might need to install additional plugins to be able to play some types of movies:\

..i thought i have all the codecs installed....
when i try to play it in mplayer it gives me this error:

MPlayer interrupted by signal 11 in module: decode_video
-MPlayer crashed by bad usage of CPU/FPU/RAM
Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and dissaembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash


can anyone help me out?

---

### Post by enopepsoo on 2006-05-09
You can't play a wmv3 at all.  There is no codec, because it is a proprietary format that was designed for DRM purposes.  It is tough to play these because if anyone can play them, the DRM is useless.
I have heard of people stripping the DRM from these files, but I have no clue on how that is done.  It may be even to play the file on a PC that is allowed and to reencode the audio / video as it is played.
Sorry for what may be bad news.

---

### Post by DarkManX4lf on 2006-05-09
i got it to work... i went to this link

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

and followed "the codecs" sectin and it works...now the only problem is streaming video...when i go into firefox and tryto play a streaming video (like the ones in gamespot.com) its really choppy how do i fix that?

---

