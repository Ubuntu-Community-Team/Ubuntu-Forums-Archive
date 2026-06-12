---
title: "Stepmania sound problems"
date: 2004-12-24
forum: Gaming &amp; Leisure
---

### Post by Night Chaos on 2004-12-24
I am a new Ubuntu user, and I am having a bunch of problems regarding the game Stepmania. It's a DDR clone, but that dosen't really have much relevence here.

I try to run the program, it starts up and exits. Here is the log file

```

00:00.158: StepMania 3.9 rc2a

00:00.186: Log starting 2004-12-23 19:35:45

00:00.187:  

00:00.187: Reading 'Data/Defaults.ini' failed: No such file or directory

00:00.187: Reading 'Data/StepMania.ini' failed: No such file or directory

00:00.187: Reading 'Data/Static.ini' failed: No such file or directory

00:00.445: Loading window: gtk

00:00.447: OS: Linux ver 020608

00:00.448: Crash backtrace component: x86 custom backtrace

00:00.448: Crash lookup component: dladdr

00:00.449: Crash demangle component: cxa_demangle

00:00.450: Runtime library: glibc 2.3.2

00:00.450: Threads library: NPTL 0.60

00:00.451: TLS is available

00:00.452: AnnouncerManager::AnnouncerManager()

00:00.452: Reading 'Data/GamePrefs.ini' failed: No such file or directory

00:00.452: Reading 'Data/Static.ini' failed: No such file or directory

00:00.453: ThemeManager::SwitchThemeAndLanguage: "default", ""

00:00.505: Initializing driver: ALSA

00:00.558: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.4 (Mon May 17 14:31:44 2004 UTC).

00:00.560: ALSA Driver: 0: ICEnsemble ICE1724 [ICE1724], device 0: ICE1724 [ICE1724], 1/1 subdevices avail

00:00.561: ALSA Driver: 0: ICEnsemble ICE1724 [ICE1724], device 1: IEC1724 IEC958 [IEC1724 IEC958], 1/1 subdevices avail

00:00.609: ALSA: dsnd_pcm_hw_params_set_format: Invalid argument

00:00.611: Couldn't load driver ALSA: SetHWParams failed

00:00.612: Initializing driver: ALSA-sw

00:00.629: OS: Linux ver 020608

00:00.631: ALSA: dsnd_pcm_hw_params_set_format: Invalid argument

00:00.633: Mixing 0.000000 ahead in 0 Mix() calls

00:00.634: Couldn't load driver ALSA-sw: SetHWParams failed

00:00.634: Initializing driver: OSS

00:00.637: Mixing 0.000000 ahead in 0 Mix() calls

00:00.638: Couldn't load driver OSS: RageSound_OSS: ALSA detected.  ALSA OSS emulation is buggy; use ALSA natively.

00:00.639: 

00:00.639: //////////////////////////////////////////////////////

00:00.639: Exception: Couldn't find a sound driver that works

00:00.639: //////////////////////////////////////////////////////

00:00.639: 

00:00.640: Language: english

00:00.640: Theme: default

```

Any suggestions? I have no idea what to do.

---

### Post by tidalwav1 on 2005-02-20
I have the same problem, and haven't been able to figure out how to fix it. Go figure. :(

---

### Post by MaX on 2005-03-17
[QUOTE=Night Chaos]I am a new Ubuntu user, and I am having a bunch of problems regarding the game Stepmania. It's a DDR clone, but that dosen't really have much relevence here.

I try to run the program, it starts up and exits. Here is the log file

```


00:00.634: Couldn't load driver ALSA-sw: SetHWParams failed

00:00.634: Initializing driver: OSS

00:00.637: Mixing 0.000000 ahead in 0 Mix() calls

00:00.638: Couldn't load driver OSS: RageSound_OSS: ALSA detected.  ALSA OSS emulation is buggy; use ALSA natively.

00:00.639: 

00:00.639: //////////////////////////////////////////////////////

00:00.639: Exception: Couldn't find a sound driver that works

00:00.639: //////////////////////////////////////////////////////

```

Any suggestions? I have no idea what to do.[/QUOTE]

There's your error right there, you probably haven't got an ALSA that's correct.

Linux: ALSA device can be changed via the SoundDevice option in StepMania.ini. ..

---

### Post by valadil on 2005-03-17
Are you running an AMD64 by any chance?  Stepmania will not run on one of those.  The programmers behind stepmania are mostly windows people, so the linux version (which I'm grateful for despite my tone) is hacked up and fugly.  Rather than use SDL they do some very low level stuff with alsa that simply won't work with an amd64.

---

### Post by leif_thande on 2005-04-26
If this can help, I managed to run Stepmania by using the root account (sudo will work too). You also need a working OpenGL compatible video card and the correct drivers installed (Nvidia or ATI). Note that I run stepmania with a Radeon 9800 with the ATI drivers (fglrx) and it's a bit laggy. However I don't know which one is to blame ( I would guess both... ). 

So running Stepmania on Linux is cool, by far from usable at this time.

---

### Post by zor0 on 2005-05-20
[QUOTE=valadil]Are you running an AMD64 by any chance?  Stepmania will not run on one of those.  The programmers behind stepmania are mostly windows people, so the linux version (which I'm grateful for despite my tone) is hacked up and fugly.  Rather than use SDL they do some very low level stuff with alsa that simply won't work with an amd64.[/QUOTE]
there are so many great programs out there that just have no/bad linux support.  I think we should start a reality show.  We get a bunch of 1337 linux programers, and go arround hacking their sites and fixing/creating linux branches.  They'll think their forums are broken because no one needs help all of a sudden 

Also, rc2a is the only version that i've ever gotten to work, rc3 from sf dosn't work worth a crap, keeps complaining about a missing liblua.so library even though i grabbed every liblua package I could find off apt

---

### Post by Ashims on 2005-05-21
[http://prdownloads.sf.net/stepmania/StepMania-3.9-rc2a-linux.tar.gz?use_mirror=heanet](http://prdownloads.sf.net/stepmania/StepMania-3.9-rc2a-linux.tar.gz?use_mirror=heanet)

This one works out of the box for me... sound is fine... I'm running i386 Hoary, and I've currently got the esd process killed-- I think. 

The one think you'll find with sound on ubuntu, is esd likes to not allow ALSA or OSS or any other sound system for that matter to use the sound device while its active... so anything that cant use ESD will die, or not play sound (doom3, cedega etc.-- cedega might, but I havent bothered switching). I just kill esd most of the time. Amarok with the Xine engine also doesn't work while ESD is running... I dont think... 

I get the same problem with liblua with rc3.

---

### Post by tidalwav1 on 2005-05-26
I managed to fix the liblua problems with RC3 by making some symlinks to the lua files that Stepmania was looking for in the /usr/lib directory. However, now stepmania is complaining about a file called "libavplugin.so", which I know has something to do with the program FFMPEG. I installed FFMPEG, as well as the libavplugin dev pakage, and neither of them include this file. Anyone know where I might find it?

---

### Post by Glenn Maynard on 2005-06-03
(It's rather late for advice about the original problem, but responding to it for completeness ...)

> ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
That's the actual problem.  It looks like your card doesn't support SND_PCM_FORMAT_S16_LE.  Try changing "SoundDevice" to "default" in StepMania.ini; this will force ALSA conversions to be used.

> Are you running an AMD64 by any chance? Stepmania will not run on one of those. The programmers behind stepmania are mostly windows people, so the linux version (which I'm grateful for despite my tone) is hacked up and fugly. Rather than use SDL they do some very low level stuff with alsa that simply won't work with an amd64.
The Linux port is solid.  It doesn't use SDL for audio because SDL's audio is trivial, not intended for any serious use: it lacks tight synchronization (which StepMania requires, of course) and hardware mixing and resampling support, which StepMania will take advantage of.  Nothing about the ALSA support inherently won't work on AMD64.

Constructive criticism and specific complaints are welcome and useful, but calling code "hacked up and fugly" falls just short of that. :)

-- Glenn Maynard (StepMania team)

---

### Post by jherm on 2005-06-16
[QUOTE=zor0]there are so many great programs out there that just have no/bad linux support.  I think we should start a reality show.  We get a bunch of 1337 linux programers, and go arround hacking their sites and fixing/creating linux branches.  They'll think their forums are broken because no one needs help all of a sudden 

Also, rc2a is the only version that i've ever gotten to work, rc3 from sf dosn't work worth a crap, keeps complaining about a missing liblua.so library even though i grabbed every liblua package I could find off apt[/QUOTE]

Compiling rc3 from source at the moment, was checking out what people needed to get to be able to install StepMania. The liblua problem you seemed to have can be alleviated by getting:

liblualib50
liblualib50-dev

If you're using Synaptic (which I did), it told me that I needed some more packages to install the above two packages (I'm guessing the framework for Lua 5) so I clicked 'OK' and got through the configure process!

In case this doesn't work, I also installed these packages...

liblua40-dev
liblualib40-dev

---

### Post by alphonce on 2005-08-08
about the avplugin (i didn't got the plugin but libavformat and libavcodec), try install libavcodeccvs, and go into /usr/lib and link the libraries properly with 'sudo ln -s <target> <linkname>'. worked with my rc3.

PS. you only need liblua50 and liblualib50, not the devs.

---

### Post by valadil on 2005-08-15
I was giving sm another try, so naturally I googled for stepmania and ubuntu.  It was somewhat disconcerting to see that my previous post, which was kinda indignant, got the attention of one of the devs.

I gave sm another try on my amd64 and it worked fine, despite my previous bitching about alsa.  I maintain that whatever old version I had used before wasn't going to work with alsa on an amd64, but the devs have done what they should and it compiles and runs (mostly) fine for me now.

---

