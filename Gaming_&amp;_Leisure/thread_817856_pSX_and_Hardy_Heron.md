---
title: "pSX and Hardy Heron"
date: 2008-06-04
forum: Gaming &amp; Leisure
---

### Post by Venko on 2008-06-04
I searched around the forums a lot for this but all I really discovered is that the dating is messed up on forum topics (topics lasted posted at in 2005 show up as "2 weeks ago").

There's an issue with pSX and pulse audio. That much I know. But I was wondering what methods people have used to get it to work in Hardy Heron as I'd like to employ one of them.

---

### Post by acoustibop on 2008-06-04
Might be an idea to tell us what the problem is is, Venko.  Most of us using pSX in Hardy aren't having any problems with sound.

That said, there are some people having problems with starting pSX, and investigation has shown that it's a sound problem, though there's no indication it's necessarily due to PulseAudio, and there are no fixes as yet.  If you're having a problem like this, I presume you've installed libgtkglext1; try installing the -dev package as well.  This may not fix anything, but should clear up any error messages to give a better idea what the fault is.

**Edit:** I would have thought it was obvious, but try starting pSX from a terminal - that way, if pSX crashes, you'll still have the terminal output for diagnosis.

---

### Post by wingnux on 2008-06-04
You can try going to menu Preferences -> Sound on Gnome and setting everything to ALSA instead of Autodetect.

---

### Post by Venko on 2008-06-04
> **acoustibop said:**
> Might be an idea to tell us what the problem is is, Venko.  Most of us using pSX in Hardy aren't having any problems with sound.

That said, there are some people having problems with starting pSX, and investigation has shown that it's a sound problem, though there's no indication it's necessarily due to PulseAudio, and there are no fixes as yet.  If you're having a problem like this, I presume you've installed libgtkglext1; try installing the -dev package as well.  This may not fix anything, but should clear up any error messages to give a better idea what the fault is.

**Edit:** I would have thought it was obvious, but try starting pSX from a terminal - that way, if pSX crashes, you'll still have the terminal output for diagnosis.

The reason I said it was a pulse audio problem because I did run it in a terminal and then checked the official forums where I found a topic which states it does not work with PulseAudio. Which makes it odd that some seem to have got it working in Hardy. I thought that they'd removed PulseAudio entirely to get it to work but that seems not to be the case.

For the record I do have libgtkglext1 and the the actual error I get is:
```
venko@Natalie:~/.pSX/pSX$ ./pSX 
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'No such file or directory'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

---

### Post by acoustibop on 2008-06-04
This is a similar error message to what the other people are getting, Venko.  I don't know what the solution is.

Something that might help, but can't be sure because I probably did it anyway after installing Hardy but before installing pSX, is to install libsdl1.2debian-all.  Don't worry if it removes libsdl1.2debian-alsa, because ALSA support will be reinstated with the libsdl1.2debian-all package.  But this installs several SDL sound drivers, as well as just the ALSA one, and it seems to help where an application may need an alternative sound driver.  It's a good strategy if you're going to be running games on your system.

What sort of soundcard do you have?

---

### Post by Venko on 2008-06-04
> **acoustibop said:**
> This is a similar error message to what the other people are getting, Venko.  I don't know what the solution is.

Something that might help, but can't be sure because I probably did it anyway after installing Hardy but before installing pSX, is to install libsdl1.2debian-all.  Don't worry if it removes libsdl1.2debian-alsa, because ALSA support will be reinstated with the libsdl1.2debian-all package.  But this installs several SDL sound drivers, as well as just the ALSA one, and it seems to help where an application may need an alternative sound driver.  It's a good strategy if you're going to be running games on your system.

What sort of soundcard do you have?

I already have libsdl1.2debian-all installed, actually. As for my sound card it's an on-board one. Not sure of the exact specifics but it's an Acer Travelmate 4150 LMi if that helps.

---

### Post by hessiess on 2008-06-04
I get a simmaler error if I run pSX while rythembox or something else is playing sound. have you tryed closing everything before running?

---

### Post by Venko on 2008-06-04
> **hessiess said:**
> I get a simmaler error if I run pSX while rythembox or something else is playing sound. have you tryed closing everything before running?

Yes, I have tried rebooting my system and there's (AFAIK) nothing that uses sound set for system launch other than Ubuntu system sounds.

---

### Post by Venko on 2008-06-05
> **wingnux said:**
> You can try going to menu Preferences -> Sound on Gnome and setting everything to ALSA instead of Autodetect.

I just tried that and it seems to not work on my system as I get the error
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

This is after a system reboot so nothing should be using the sound.

I took a look in /usr/lib/alsa-lib/ and there's definitely no libasound_module_pcm_pulse.so there. All that is in there is libasound_module_ctl_bluetooth.so and libasound_module_pcm_bluetooth.so.

I tried installing libasound2 in case my system was missing it but apt-get reports that "libasound2 is already the newest version".

So I did a system-wide search for libasound_module_pcm_pulse.so and it doesn't exist anywhere on my system!

**[edit]** I fixed my ALSA problem (following a PulseAudio guide on these forums). If I select ALSA from the sound menu now and test it it works fine.

Also the error I now get is like that of others with PulseAudio inflicted pSX problems whilst before it was slightly different. (See below:)
```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
```

I'm still curious about those Hardy users who have managed to get pSX working. I'd love them to share how they did it.

---

### Post by theaquarian on 2008-06-20
I download pSX from the website, however, when I extract the files and try to run it, I get a simple error:

pSX: 1: Syntax error: "(" unexpected

Anyone have any clue as to what that means?  Also, I'm running Hardy AMD64, and I tried trying to verify that I have the named packages installed that are described in the readme.  However, half of them aren't available in the package manager.

Thanks for your help!

---

### Post by acoustibop on 2008-06-21
Post the line you used to try to run it, theaquarian.

For 64bit systems, you may have to install 32bit versions of the libraries needed.  See [dfreer's thread]("http://ubuntuforums.org/showthread.php?t=394097") on this.

---

### Post by rfrayer on 2008-10-27
I would love to figure out a way to get pSX to run with pulse. Im testing out the new version intreped ubuntu and finally pulse runs wonderfly but alas pSX only works with alsa and i get the same error as the other guy. If there was a way to at least start pSX muted then maybe.....

---

### Post by dfreer on 2008-10-27
Just now stumbled across this thread. Haven't run Hardy ever since release, so I haven't gotten to test this yet, YMMV:
[http://ubuntuforums.org/showpost.php?p=5977268&postcount=238](http://ubuntuforums.org/showpost.php?p=5977268&postcount=238)

---

### Post by rfrayer on 2008-10-27
yeah i allready tried that and it didnt work this way. still getting the 
```

george@george-desktop:~/Desktop/psxfrontendv111linx86$ pSX
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0

```

Not sure what else to do ...on the brite side i managed to find a decent video plugin for epsxe but it still dont hold a candle to the smooth graphics of psx

---

### Post by Clericman on 2008-11-02
sudo killall pulseaudio

That worked for me :)

---

### Post by Lee83 on 2008-11-02
not really an answer to your question about sound but i do have a problem with psx in hardy,small as it is when i click file on the emu i cant see the menu so i have to cycle of option to see what i need,does anyone else have this problem?? not major but an annoyance really

---

