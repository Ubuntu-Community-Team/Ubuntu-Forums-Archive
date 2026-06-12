---
title: "Foreign Characters in Rhythmbox"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Farthing-or-less on 2006-01-27
Rhythmbox does not seem to want to display foreign (non-english, in this case) characters or letters, even though Sound Juicer does. I am referring to Japanese and Chinese Characters, and even letters from European languages with diacritics (å ä á ñ etc). I should also mention that the characters show up just fine beneath the file icons in Nautilus too. Rhythmbox seems to be the only offender.

Is there anyway to change the setting so that Rhythmbox will be a bit more graphically international?

---

### Post by doclivingston on 2006-01-28
Are the files that aren't displaying characters properly MP3s? If so, then it is probably because your files have tags that don't conform to the ID3 specification properly.

Unfortunately, virtually all of the Window tagging programs and quite a few Linux ones don't write ID3 tags properly. They use non-Latin characters, without indicating which character-set they are using for the encoding. A lot of players get around this by assuming that if the encoding isn't specified, then to use the current locale.

Rhythmbox doesn't do this for a couple of reasons:
1) Doing that will cause some conformant files to display the wrong characters
2) If you are using a UTF8 locale (which a lot of people are), then it won't work anyway.
3) If you're locale isn't set to exactly the same one as when the file was encoded, it won't work either.

---

### Post by Farthing-or-less on 2006-01-28
Yes. They're mp3s. I will try ripping a few with different rippers, then play around with easytag and see what comes up.

thanks

---

### Post by Farthing-or-less on 2006-01-28
OK. I think you've got it. I copied some mp3s from my wife's mac encoded with iTunes, and added them to my Rhythmbox library, and the characters display properly - Japanese, Chinese, Korean, Spanish, and French. So what you said about the encoding seems on target. The problem seems to be in the tags.

I also noticed that OGG files display the characters correctly. I believe that OGG encodes the tags as UTF-8 by default, so that would suggest that the goal is to get LAME to do the same, no?

That said, Any ideas how to solve the problem with MP3s?

---

### Post by aysiu on 2007-06-02
If the MP3 tags have already been encoded, is there a way to change the encoding after the fact?

---

