---
title: "Help with espeak"
date: 2011-10-02
forum: Desktop Environments
---

### Post by xxfireboy on 2011-10-02
I am using 10.10 the Maverick Meerkat.
I was using espeak for months now and it was working just fine
with no hint of any problems. I was unable to use it for a couple of
weeks and then I needed it and it will not startup.  Applications>Sound and Video, nothing happens, nothing.

I un-installed and reinstalled so many times I lost count.

I try to start it using f2+alt and nothing. I open a terminal and enter:

    Code:
      Name:~$espeak
      Can't read data file: '/home/jar/espeak-data/phontab'
      Failed to load espeak-data

or

    Code:
      Name:~$ espeak --stdout 'words to speak' | aplay
      Can't read data file: '/home/Name/espeak-data/phontab'
      Failed to load espeak-data
      aplay: playback:2372: read error

I have searched: here at Ubuntu forums and nothing,
and on google and nothing,
at Ubuntu Documentation: [https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)
and nothing,
at eSpeak text to speech: [http://espeak.sourceforge.net/index.html](http://espeak.sourceforge.net/index.html)
and nothing,
gespeaker: [http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)
and nothing.

Please, if someone can tell me how to fix this, thanks in advance.fb

---

### Post by SecretCode on 2011-10-02
I haven't used espeak, but it's installed on my system and runs fine.

> **xxfireboy said:**
> 
      Can't read data file: '/home/jar/espeak-data/phontab'


I don't have any espeak-data folder ... in fact I don't have any *espeak* files in my home folder. Perhaps the file indicated is corrupted? You could try deleting it (or renaming the espeak-data folder perhaps).

---

### Post by xxfireboy on 2011-10-02
> **SecretCode said:**
> I haven't used espeak, but it's installed on my system and runs fine.



I don't have any espeak-data folder ... in fact I don't have any *espeak* files in my home folder. Perhaps the file indicated is corrupted? You could try deleting it (or renaming the espeak-data folder perhaps).
SecretCode, that did it! I deleted the file "espeak-data" and now espeak opens and works>!
Thanks, now I'm back in business. Thank you for taking the time to lend a hand.fb

---

### Post by mörgæs on 2011-10-02
Good, then please mark the thread 'solved'.

---

