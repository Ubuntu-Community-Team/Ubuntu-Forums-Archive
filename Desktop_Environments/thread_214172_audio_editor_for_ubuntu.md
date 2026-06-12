---
title: "audio editor for ubuntu"
date: 2006-07-12
forum: Desktop Environments
---

### Post by derakhshani on 2006-07-12
Hi,

I need an audio editor for ubuntu, I need something like cool edit pro in windows which has noise removal effect. I try audacity but I found its noise removal quality very low (I am not professional in audacity maybe I do it in a wrong way). Any way, I am looking for some applications for removing noise from a mp3 file which completely is a speech. In cool edit pro first I choosed some seconds of pure noise then Cool edit removed this noise from all of audio file.
Also, I try to run cool edit pro via wine but it does not work at all ](*,), and I tried some other audio editors in ubuntu but they did not have noise remove option like cool edit :-k. 

By considering that, I only have Ubuntu at this time, do you have any suggestion?

---

### Post by BuffaloX on 2006-07-12
I'm surprised Audacity dosn't have that. 
It has a ton of plugins.

But this one should have what you are looking for.
ReZound
[http://sourceforge.net/docman/?group_id=5056]("http://sourceforge.net/docman/?group_id=5056")

Its installable from repository. ;) 

Have fun. :p

---

### Post by DeadEyes on 2006-07-12
Audacity does have noise removal but it's a bit awkward to use.

---

### Post by derakhshani on 2006-07-12
Well, I didn't say that audacity does not have that feature.
infact, audacity has that feature but the quality as I tested was bad.
about rezound: I tested it before I only saw an option called noise gate that was very different from noise remove in cool edit and also audacity, it ignores sound less than a threshould. Suppose there was a continous noise by using this action on it this noise will be removed only when the speaker is silent but when he speaks the noise will not be removed.

Also I find this at rezound site at sf.net as a feature request:

>  
Adding audacity noise filter
Hi.

There's a noise filter in audacity that I find very
useful because its simplicity and good results. It
let's you select a region of noise, then it computes a
filter that you can apply to a entire sound affected by
that noise. It works really good to eliminate noises
like the tape hiss.

[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

I don't know of any other gpl code that implements that
kind of filter.


thank you any way.
again any suggestion?

---

### Post by BuffaloX on 2006-07-12
> Audacity does have noise removal but it's a bit awkward to use.

Oh I guess I also kinda jumped from not good enough to not available.

In ReZound
Look in LDSPA menu for Nonband limited single sample impulses....

Does it get any more userfriendly than that? :p 
You can select use sound, and use that sound as your noise sample (example)

I guess you need to have saved it previously?

Haven't tried it, but the feature seems to be there.;) 

Best of luck.

---

### Post by derakhshani on 2006-07-12
I tried to install some different audio editor apps. I found gnome wave cleaner [http://gwc.sourceforge.net/]("http://gwc.sourceforge.net/") very good at removing noise from audio files.
but the bad part of news is that after installing some new softwares, plugins, and some working on them, all of my audio editor report an error.
for example:
> $rezound
using path '/usr/share/rezound' for share data directory
Error occurred while initializing audio output method 'oss' -- virtual void COSSSoundPlayer::initialize() -- error opening OSS device '/dev/dsp -- Device or resource busy
Error occurred while initializing audio output method 'jack' -- virtual void CJACKSoundPlayer::initialize() -- error connecting to jack server -- jackd not running?

it seems something happened for /dev/dsp.
but, my audio player like mplayer or rhythmbox can play music files without any problem.
any idea?

---

### Post by derakhshani on 2006-07-13
> **BuffaloX said:**
> Oh I guess I also kinda jumped from not good enough to not available.

In ReZound
Look in LDSPA menu for Nonband limited single sample impulses....

Does it get any more userfriendly than that? :p 
You can select use sound, and use that sound as your noise sample (example)

I guess you need to have saved it previously?

Haven't tried it, but the feature seems to be there.;) 

Best of luck.

Well, I did not understand how it works. it only deletes selected sound.

---

