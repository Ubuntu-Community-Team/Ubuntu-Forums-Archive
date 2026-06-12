---
title: "Astromenace on Intrepid?"
date: 2008-11-23
forum: Gaming &amp; Leisure
---

### Post by mmcmonster on 2008-11-23
Anyone manage to get astromenace installed on Ubuntu 8.10 (Intrepid)?

I get the following:
```
$ sudo apt-get install astromenace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  astromenace: Depends: libopenal0a but it is not installable
E: Broken packages

```

---

### Post by Perfect Storm on 2008-11-23
[http://viewizard.com/forum/index.php?topic=159.0](http://viewizard.com/forum/index.php?topic=159.0)

---

### Post by mmcmonster on 2008-11-24
Bummer.  Hope he gets Ubuntu installed soon so that we get a fixed version. :-)

---

### Post by jabapyth on 2009-10-15
Just use the downloadable [.tar.gz file]("http://www.viewizard.com/download/amenace12.tar.bz2"). works totally fine on Jaunty/Karmic

---

### Post by doubtintom on 2009-11-06
I did try just that, downloaded the astromenace.tar.gz file. Game visuals work perfectly but no sound. On Karmic. I get this output from launching the game from the command line:

```
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: Device or resource busy
Default sound device not present!
Unable to open audio!
```

I checked to make sure I am in the audio group, which has group rw permissions on /dev/dsp

I need to test /dev/dsp at least. Hmm...how to do that?
hmmm...google...
```
cat /dev/dsp > test
cat: /dev/dsp: Device or resource busy

```

But Pulseaudio Sound Preferences/Applications tab tells me:
```
No application is currently recording or playing audio
```
And surely I had not started any sound programs.

Anyone else have any ideas?

txn in advance

Tom

---

