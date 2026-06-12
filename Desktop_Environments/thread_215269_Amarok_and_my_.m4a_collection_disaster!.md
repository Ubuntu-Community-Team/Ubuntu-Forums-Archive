---
title: "Amarok and my .m4a collection disaster!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by tartarian on 2006-07-13
Well, I'm running the latest version of Amarok - 1.4.1, and having just ported from windows to kubuntu, my media collection from iTunes is in .m4a format. Now, Amarok plays the tracks just fine, but when it comes to scanning my collection, it totally ignores all the tracks, coming back and telling me that I have absoloutly no music! I've tried inserting the tracks file by file but amarok wont even do that! Please Help! Thanks!

---

### Post by Dubbayoo on 2006-07-13
.m4a files have no id3 info on them.

---

### Post by tartarian on 2006-07-14
What does that mean?

---

### Post by philippe_carlo on 2006-07-14
> **tartarian said:**
> Well, I'm running the latest version of Amarok - 1.4.1, and having just ported from windows to kubuntu, my media collection from iTunes is in .m4a format. Now, Amarok plays the tracks just fine, but when it comes to scanning my collection, it totally ignores all the tracks, coming back and telling me that I have absoloutly no music! I've tried inserting the tracks file by file but amarok wont even do that! Please Help! Thanks!

Try running amarok from a terminal window and see if it prints some errors.

---

### Post by meatbop on 2006-07-14
> **tartarian said:**
> What does that mean?

IDv3 tags are the method of storing the file metadata (Artist, Album etc) for mp3's.  While m4a files have similar metadata the format differs from mp3 and is therefore not readable by an application which does not have specific support for them.

Amarok 1.4 and up supposedly support read only access to the m4a tags through Taglib, however a quick google reveals that you're not alone in having problems with it.

I don't have a solution for you I'm afraid.

---

### Post by tartarian on 2006-07-15
The stupid thing is that I ran Amarok in Ubuntu and it worked fine! Added them no problem. But now I've moved over to kubuntu it doesn't work! god this is frustrating!

---

