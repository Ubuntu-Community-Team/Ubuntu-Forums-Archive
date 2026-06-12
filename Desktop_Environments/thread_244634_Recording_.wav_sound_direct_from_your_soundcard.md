---
title: "Recording .wav sound direct from your soundcard"
date: 2006-08-26
forum: Desktop Environments
---

### Post by shamrock_uk on 2006-08-26
Hey everyone. 

There's a lovely little piece of unidentified music at the end of an .avi file which I want to keep as a separate audio track. The easiest way to do this I thought would be to record the soundcard output as it was playing the .avi.

My first stop was Sound Recorder which has nothing under "record from input:". 

I then tried Audacity, but get the following error:

> There was an error initializing the audio i/o layer. You will not be able to play or record audio. 

Error: Host error


To give a clearer idea of what I need, in Windows I would just bring up the volume properties and select "wav" under the 'recording' tab. 

My soundcard is ```
0000:05:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
``` and needless to say all the normal 'playback' things worked fine out of the box.

Unfortunately I don't have a clue about the Linux sound system. Am I right in thinking Dapper doesn't use alsa but esd instead? Can anyone poke me in the right direction? 

Cheers :)

---

### Post by galileon on 2006-09-01
hello, i had this prob with flash-inside-firefox, and for the time being, i found out i could do it if i ran firefox for windoze thru wine...i have to load audacity first tho, and set the recording to 'Vol' instead of 'Mic'

i'd suggest you try a media player inside wine? eg vlc for windowz?

---

