---
title: "&quot;Double voice&quot; in festival"
date: 2006-04-14
forum: Desktop Environments
---

### Post by Tomlin on 2006-04-14
Hey all,

I'm playing around with festival and with the help of these forums, solved the " can't open /dev/dsp" problem by starting the session:

esddsp festival

That works, but now, when inputting a long (50 or more words) textfile, like:

(tts "/home/username/file.txt" nil)

OR using **text2wave** /home/username/file.txt -o file.wav

and playing it back with XMMS, I get a "double voice" i.e. there are 2 voices speaking different parts of the file at the same time.

Anyone know what's up?

TIA

Tomlin

---

