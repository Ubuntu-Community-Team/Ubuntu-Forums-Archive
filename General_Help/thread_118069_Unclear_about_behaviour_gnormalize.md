---
title: "Unclear about behaviour gnormalize"
date: 2006-01-16
forum: General Help
---

### Post by robenroute on 2006-01-16
Hi there,

I've successfuly installed normalize 0.7.7 (=latest version) and gnormalize 0.47 (converted .rpm into .deb and installed without a hitch). According to the gnormalize documentation, when normalizing MP3 files (and the input format is the same as the output format, e.g. MP3), there will be no decoding and subsequent re-encoding, to prevent quality loss. This requires the MAD library, which happens to be installed on my system (libmad0).

Now, when I select a directory of MP3 files (and have set the output format to MP3 as well), I hit the normalize button and then.... right, gnormalize starts to decode the MP3 to WAV, normalizes the WAV file and re-encodes to MP3.

Anyone out there knows what I'm doing wrong? Perhaps gnormalize can't find the MAD library? I can't see any settings for location of needed libs/progs in gnormalize. Am I overlooking something?

Help much appreciated. Thanks in advance.

Rob

---

### Post by robenroute on 2006-01-16
Still unable to figure out what's going on. Are there people out there with similar problems? Or, hopefully, with some hints for what direction to look for clues/solutions? Would really be great to get it to work....

Thanks a lot,
Rob

---

### Post by robenroute on 2006-01-16
Ba-ba-ba-ba-bump

---

### Post by robenroute on 2006-01-17
Just recieved word from Claudio Rodrigues (the author of ***gnormalize***): unfortunately, gnormalize isn't able to make use of the direct normalization adjustments offered by Chris Vaill's ***normalize***. He said he would consider putting this in a future release; he's very busy with his studies at the moment....

Well, that's awfully unfortunate for all of us since it means, we have to normalize our MP3 files via ***normalize*** (command line only!).

Perhaps there are (will be?) other front-ends for ***normalize***?

Regards,
Rob

---

### Post by robenroute on 2006-01-20
Just for those who want to use 'normalize' to do direct normalization of MP3 files: make sure you have madlib0-dev (the development library) installed, when you compile 'normalize'; just having libmad0 won't cut the mustard.

It's not mentioned in the 'normalize' documentation, but it's needed.

Oh yeah, anyone know of another front-end to 'normalize', one that makes use of the direct normalization functionality ('gnormalize' can't do this!).

Cheers,

Rob

---

### Post by chaumurky on 2006-01-20
LOL. I googled 'gnormalize' and blindly followed this link. Don't worry, it's quite safe, but for a while I thought the site has been hack'd - arrr...!

[http://adactio.com/extras/talklikeapirate/translate.php?filename=http://freshmeat.net/releases/186939/]("http://adactio.com/extras/talklikeapirate/translate.php?filename=http://freshmeat.net/releases/186939/")

---

### Post by robenroute on 2006-01-21
[QUOTE=chaumurky]LOL. I googled 'gnormalize' and blindly followed this link. Don't worry, it's quite safe, but for a while I thought the site has been hack'd - arrr...!

[http://adactio.com/extras/talklikeapirate/translate.php?filename=http://freshmeat.net/releases/186939/]("http://adactio.com/extras/talklikeapirate/translate.php?filename=http://freshmeat.net/releases/186939/")[/QUOTE]


And your point is....?

---

### Post by chaumurky on 2006-01-21
Um, right. I was searching for some information on normalize and found this thread (by the way, thank you very much). After stumbling across something that made me laugh out loud while searching further and thinking the ubuntu forums are as much helpful as friendly I couldn't contain myself from spoiling your 5 post monologue. Is that what you want to hear? No there was no point and if you are offended by my gratuitous spamming I apologize. Really. Now.... your point was?

---

### Post by robenroute on 2006-01-21
[QUOTE=chaumurky]Um, right. I was searching for some information on normalize and found this thread (by the way, thank you very much). After stumbling across something that made me laugh out loud while searching further and thinking the ubuntu forums are as much helpful as friendly I couldn't contain myself from spoiling your 5 post monologue. Is that what you want to hear? No there was no point and if you are offended by my gratuitous spamming I apologize. Really. Now.... your point was?[/QUOTE]

No, not offended, I was just wondering what you were contributing to my quest for a front-end to 'normalize', where 'gnormalize' is pretty useless as far as the direct normalization of MP3 files is concerned.

I too had already noticed that it was evolving into a monologue, but I'm used to that, no one ever listens to me.... :p 

So, you know of a front-end to 'normalize' that offers the by me requested functionality? Much obliged.

Rob

---

### Post by chaumurky on 2006-01-22
Unfortunately I have got as far as you. If I find something else I'll post here. The commandline version works very well though. I might have to just learn that ;-)

---

