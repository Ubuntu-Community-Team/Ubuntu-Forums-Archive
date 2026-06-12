---
title: "installing mocp (moc-2.4.0) under 6.06"
date: 2006-09-18
forum: Desktop Environments
---

### Post by starpause on 2006-09-18
hello, i'm trying to install moc-2.4.0 from source because the latest version has features which i require. as far as i can tell, moc-2.3.3-1 is the latest version in the package manager for kubuntu 6.06 (please point me at a repo that says otherwise :KS ). 

the steps i have taken so far:

1) download and extract moc from [http://moc.daper.net/download](http://moc.daper.net/download)

2) run from cli: "./configure" in the moc-2.4.0 directory, get this spit out at the end

```

----------------------------------------------------------------
MOC will be compiled with:
Decoder plugins:    mp3 vorbis flac
OSS:               yes
ALSA:              yes
JACK:              no
DEBUG:             yes
ICONV:             yes
RCC:               no
Network streams:   no
Resampling:        no

----------------------------------------------------------------

```

3) run from cli: "sudo make install" in the moc-2.4.0 dir

seems to go well enough, but when i run mocp i get the following error:

```
mocp: interface_elements.c:3267: iface_set_mixer_value: Assertion `value >= 0 && value <= 100' failed.
```

any ideas? thanks!

---

### Post by croak77 on 2006-09-18
Moc has a default config file. You might have to edit it and put in your values for alsa/oss, mixer, etc. There should be a config.example.

---

### Post by starpause on 2006-09-19
croak, thanks for the information. 

mocp 2.3.3 ran fine with the default config file and a modified config.example where i had made no changes to the commented out SoundDriver line.

not that i know what i'm doing, but messing around with that line and the ALSA and OSS settings don't change the error message i get with moc 2.4.0 ... do you have any idea what i would be looking to change to see a difference?

i also installed the libsamplerate0-dev package in case resampling was the problem, running ./configure now reads

```
----------------------------------------------------------------
MOC will be compiled with:
Decoder plugins:    mp3 vorbis flac
OSS:               yes
ALSA:              yes
JACK:              no
DEBUG:             yes
ICONV:             yes
RCC:               no
Network streams:   no
Resampling:        yes

----------------------------------------------------------------

```

---

### Post by croak77 on 2006-09-19
Nope... I used moc for a little while but I found [Cmus]("http://onion.dynserv.net/~timo/cmus.html") and MPD with ncmpc-svn more to my liking for console based players. 

Maybe libjack0.100.0-dev is needed?

---

### Post by starpause on 2006-09-20
the problem is fixed (wasn't missing dependencies)! there is a patch to apply which fixes the error. it was a known problem via some debian kids. see details @ the moc thread:

[http://moc.daper.net/node/178](http://moc.daper.net/node/178)

thanks for the help! :KS

---

