---
title: "katapult amarok not playing music"
date: 2006-09-12
forum: Desktop Environments
---

### Post by dbd on 2006-09-12
Just discovered katapult, thanks to the fridge, and it looks amazing, but it doesn't work with amarok.

I can type the song name with no problems but when I press enter it doesn't play and I get this error message:

> 
Error Loading Media

No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.

./Music/Artists/Manic Street Preachers/Everything Must Go.ogg


(obviously the last bit of the error message changes dependant on the song).

This is strange, because everything plays fine when I don't select the song with amarok.

Any ideas?

---

### Post by 4tro on 2006-09-21
i believe it has something to with the fact that amarok seems to think it should play the file as a stream, probably you'll have noticed the fact that it adds a stream to the playlist. why it does this i don't quite understand

---

### Post by dbd on 2006-09-21
After posting this I saw this blog post:
[http://www.sourceguru.net/archives/42](http://www.sourceguru.net/archives/42)

Basically the problem is that amarok changed how it stored urls in the database, confusing katapult. But the katapult developer knows, so it should be fixed :)

---

