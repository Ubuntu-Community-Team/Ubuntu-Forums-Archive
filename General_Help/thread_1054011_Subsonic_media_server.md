---
title: "Subsonic media server"
date: 2009-01-29
forum: General Help
---

### Post by zerofxC on 2009-01-29
My problem is that i can't get it to play  ogg/flac/wma etc.

It will only play mp3's..

I have installed transcode, lame and ffmpeg and still have no luck?

I was just wondering if any of you guys have had the same problem or know of a solution.

Thanks!
:popcorn:

---

### Post by nlz on 2009-01-29
[http://subsonic.sourceforge.net/transcoding.php](http://subsonic.sourceforge.net/transcoding.php)

---

### Post by nlz on 2009-01-29
>  Transcoding is the process of converting music from one format to another. Subsonic's transcoding engine allows for streaming of media that would normally not be streamable, for instance lossless formats. The transcoding is performed on-the-fly and doesn't require any disk usage.

The actual transcoding is done by third-party command line programs which must be installed in c:\subsonic\transcode (on Windows), /var/subsonic/transcode (other operating systems), or in a directory present in the PATH environment variable.

Up to three transcoders can be chained together. For instance, to convert FLAC to MP3 you would typically use a FLAC decoder which converts to WAV, and chain it with a WAV to MP3 encoder. 

from [http://subsonic.sourceforge.net/transcoding.php](http://subsonic.sourceforge.net/transcoding.php)

---

### Post by xjgnsdof on 2009-09-20
The answer is here: [http://www.activeobjects.no/subsonic/forum/viewtopic.php?t=1915](http://www.activeobjects.no/subsonic/forum/viewtopic.php?t=1915)

When you need Subsonic help, you go to the Subsonic forums, where the devs themselves answer queries.

---

