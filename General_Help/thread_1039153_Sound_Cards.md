---
title: "Sound Cards"
date: 2009-01-14
forum: General Help
---

### Post by Jodha on 2009-01-14
Hi All,

I have a sound card I would like to get working on my Ubuntu equipped desktop machine; its a Terratec Phase 88 pci card with a break-out box holding audio 8in/8out plus MIDI in and out.

Its not working, although in the audio preferences it lists the hardware.

There has been no response to my initial inquiry about this sound card in the Hardware section. Further to this, on a more extensive search (than before I posted) I have found another post where somebody was considering the same card and wanted some advice. They also had had no response... not even to the secondary question - "what other card can I use instead of this for the same purposes?" (ie multi-track audio work).

My new question is -

Where can I find Ubuntu audio geeks?

I would like to converse with a bunch of people who can supply me with advice on how to get my audio hardware working, or at least offer some other suggestions. On the strength of my previous post and the search result, it seems there is a lack of Ubuntu audio geeks in at this specific site.

Many thanks for your help.

Ex-Windows audio geek/wannabe Ubuntu audio geek.

---

### Post by kostkon on 2009-01-14
I am not an expert, but let's see if I will be able to help you.

For a start:

what version of Ubuntu do you have?

Also, could you open a terminal, give the following command
```
aplay -l
```
and post the output here.

Thanks

---

### Post by Jodha on 2009-01-18
Kostkon,you are some kind of a saint, given you are the first person on this forum to actually take an interest. I hereby award you ...

[IMG]http://www.rafweb.org/Uniform_etc/Gcross.jpg[/IMG]

A George Cross :)

Ubuntu version = 8.10

Now, opening Terminal and using the command line you suggest this is the output:

[quote="Terminal"]
**** List of PLAYBACK Hardware Devices ****
card 0: Phase88 [TerraTec Phase88], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Phase88 [TerraTec Phase88], device 1: ICE1712 consumer [ICE1712 consumer]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Phase88 [TerraTec Phase88], device 2: ICE1712 consumer (DS) [ICE1712 consumer (DS)]
  Subdevices: 6/6
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #
[/quote]

See, to me it looks like it should just 'werk'. If the Alsa mixer didn't pick up on it, or if the speaker remained with a red cross through it regardless of what I did with the mixer panel, I'd be more inclined to think there was a big big problem of compatibility. However, it pops up in the options of playback device. Plus, when I raise the fader levels in the mixer window the speaker icon changes from 'muted' to a speaker without a big red cross through it.

Me = confused.

Whats your verdict matey?

---

### Post by Jodha on 2009-01-21
Erm... *bump*

---

### Post by Jodha on 2009-01-22
C'mon guys, give me a hand please

---

