---
title: "Hi!! Real player keeps Loading the stream, no sound"
date: 2006-04-30
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-04-30
Hi,
I installed RealPlayer10Gold the same way mentioned in the FAQ guide and it does work but not for evrything. i could play an mp3 and even stream video from [www.bbc.co.uk](www.bbc.co.uk) but i had other issues as well

i have plenty of queries

1. Where is the playlist
2.Whenever i try to stream from 
[http://www.raaga.com/channels/hindi/top10.asp](http://www.raaga.com/channels/hindi/top10.asp) 
the player gets stuck "Loading" the song.
3. i cant play XMMS when Real is working. XMMS throws a message saying that Sound card is not configured or Blocked by some program. My default sound driver is ALSA


Regards 
-
Dc

---

### Post by raovq on 2006-05-01
from my understanding, only one program can use ALSA at once.

that site seems to have its own player for playing music, i wouldn't be surprised if they mucked with the stream for some reason or other.

---

### Post by louis_nichols on 2006-05-01
I think the issue with sound is because RealPlayer uses OSS instead of alsa, and oss really does take over your sound card and can't mix several sources. I don't think you can avoid this...

EDIT: try installing alsa-oss! It might solve the issue.

---

