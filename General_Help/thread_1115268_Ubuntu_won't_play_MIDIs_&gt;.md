---
title: "Ubuntu won't play MIDIs &gt;:"
date: 2009-04-03
forum: General Help
---

### Post by Ben Crisford on 2009-04-03
I have installed a variety of music programs just now and none of them work.

With score editors when I press play there is no sound :O.

And with DJplay it dont make a sound either :'(...

Yes, my headphones are plugged in and my sound is on full.

And I *am* using the programs properly.

Lil' Help?

---

### Post by Rallg on 2009-04-03
Playing MIDI files can be tricky. The MIDI file only contains instructions for using "virtual instruments," the way that a real music score (on paper) contains instructions for using real instruments. The instrument themselves -- digital or real -- are separate.

It is possible to install a digital music database, and configure it to work with Linux MIDI players. But it will not work on all machines due to hardware issues (for example, it will not work on my machine, or I would tell you more).

Do you have WINE installed? If so, try this: There is a non-free music program for Windows/Mac that contains its own instrument database, and will work even on my machine. I believe there is a free player-only version that will work with MIDI, if you don't need to edit scores.

[http://www.myriad-online.com](http://www.myriad-online.com)

Look for "Melody Player." If you can install it, but it doesn't work for you, then your setup has some other difficulty.

---

### Post by Ben Crisford on 2009-04-03
A little update:

I have kept trying and have just edited ***/etc/modprobe.d/alsa-bade*** to try and make it work but it still don't :'(.  I tried rebooting and everything :(.

This is what I edited:

**_Before:_**
```
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
```

**_After_**
```
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2 mpu_port=0x330
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
```

Please tell me how I can get this to work :(.

---

### Post by Ben Crisford on 2009-04-03
> **Rallg said:**
> Playing MIDI files can be tricky. The MIDI file only contains instructions for using "virtual instruments," the way that a real music score (on paper) contains instructions for using real instruments. The instrument themselves -- digital or real -- are separate.

It is possible to install a digital music database, and configure it to work with Linux MIDI players. But it will not work on all machines due to hardware issues (for example, it will not work on my machine, or I would tell you more).

Do you have WINE installed? If so, try this: There is a non-free music program for Windows/Mac that contains its own instrument database, and will work even on my machine. I believe there is a free player-only version that will work with MIDI, if you don't need to edit scores.

[http://www.myriad-online.com](http://www.myriad-online.com)

Look for "Melody Player." If you can install it, but it doesn't work for you, then your setup has some other difficulty.

Ah, cheers, I do have WINE installed yeah.  I'll check it out.

Thanks ;).

---

### Post by Ben Crisford on 2009-04-03
b
bu
bum
bump
bum
bu
b

---

### Post by Rallg on 2009-04-04
Didn't work for you?

For a start, can you get sound other than MIDI? That is, can you play Flash with sound, MP3, and other types of audio?

Second, can you try the MIDI files on some other computer that is known to play MIDI? There are a variety of reasons why a MIDI file might be in audible, even on a good system.

As I recall from a computer I had a couple of years ago, on Ubuntu I needed to use the freepats and timidity packages (can be obtained via Synaptic Package Manager) then do some configuration. It wasn't obvious how to do it. But alas, my current system is incompatible (for sound card reasons) so I cannot re-trace what was needed. In any case, Ubuntu has changed in the intervening time.

---

### Post by CatKiller on 2009-04-04
In general, you need something to turn MIDI instructions into actual sounds. Some sound cards can do this in hardware, since they have built in sound fonts that automatically play when the sound card is sent MIDI instructions. I believe that ALSA also has the functionality to do this, but it's possible that this doesn't get used any more with the move to PulseAudio. FluidSynth and TiMIDIty are other options. FluidSynth, IIRC, works as a sound server for MIDI output, doing in software what higher-end sound cards do in hardware.

You would start FluidSynth loaded with a sound font (there are some available in Synaptic, I believe) and then point your MIDI-generating program's MIDI output at FluidSynth, which would then play your sound. It's been quite a long time since I did this, so I can't remember all the details, but hopefully this will point you in the right direction.

---

### Post by Ben Crisford on 2009-04-04
> **Rallg said:**
> Didn't work for you?

For a start, can you get sound other than MIDI? That is, can you play Flash with sound, MP3, and other types of audio?

Second, can you try the MIDI files on some other computer that is known to play MIDI? There are a variety of reasons why a MIDI file might be in audible, even on a good system.

As I recall from a computer I had a couple of years ago, on Ubuntu I needed to use the freepats and timidity packages (can be obtained via Synaptic Package Manager) then do some configuration. It wasn't obvious how to do it. But alas, my current system is incompatible (for sound card reasons) so I cannot re-trace what was needed. In any case, Ubuntu has changed in the intervening time.

My computer does play radio, and MP3.

I have timidity and freepats...  Not sure about configuration.


> **CatKiller said:**
> In general, you need something to turn MIDI instructions into actual sounds. Some sound cards can do this in hardware, since they have built in sound fonts that automatically play when the sound card is sent MIDI instructions. I believe that ALSA also has the functionality to do this, but it's possible that this doesn't get used any more with the move to PulseAudio. FluidSynth and TiMIDIty are other options. FluidSynth, IIRC, works as a sound server for MIDI output, doing in software what higher-end sound cards do in hardware.

You would start FluidSynth loaded with a sound font (there are some available in Synaptic, I believe) and then point your MIDI-generating program's MIDI output at FluidSynth, which would then play your sound. It's been quite a long time since I did this, so I can't remember all the details, but hopefully this will point you in the right direction.

The thing is, that its not one particular file I am trying to play (apart from in DJplay) I want to play music I have made in some programs I downloaded, including:
[I]-DJplay
-NoteEdit
-MuseScore
-NtEd[/I]

---

### Post by CatKiller on 2009-04-04
> **Ben Crisford said:**
> The thing is, that its not one particular file I am trying to play (apart from in DJplay) I want to play music I have made in some programs I downloaded, including:
[I]-DJplay
-NoteEdit
-MuseScore
-NtEd[/I]

As I say, it's been a long time since I've done it. If you don't have hardware support, you need a software synth. Timidity is well-supported as an output by many applications. Some will let you specify the output directly, in which case you can use FluidSynth.

There's probably more information on the Ubuntu Studio project's website, although I haven't been there for some time.

Don't forget that just because a program can play MIDI files, that doesn't mean that that's **all** it can do. Most of them will also accept MIDI information from the Standard Input (stdin), which is how they receive data from other applications.

---

