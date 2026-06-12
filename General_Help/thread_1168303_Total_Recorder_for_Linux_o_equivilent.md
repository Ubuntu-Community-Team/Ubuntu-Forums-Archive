---
title: "Total Recorder for Linux o equivilent?"
date: 2009-05-23
forum: General Help
---

### Post by Barmaleychik on 2009-05-23
Is there a free equivalent for Total Recorder for Ubuntu? I am looking for one which does not distort quality of recording

thank you in advance

Barmaley

---

### Post by Barmaleychik on 2009-05-24
BTW, I would appreciate if somebody suggest a free equivalent of Total Recorder for windlws as well.

Thanx

---

### Post by Barmaleychik on 2009-06-05
Is there ANY way to record audio coming through a sound card in Linux?

Any answer will be appreciated :)

---

### Post by Cedders on 2009-12-29
> **Barmaleychik said:**
> Is there ANY way to record audio coming through a sound card in Linux?

Any answer will be appreciated :)

If you're talking about recording the outgoing mix (CD, synth, audio from arbitrary applications) into an audio file, it's not immediately apparent in Ubuntu Karmic.  You might expect something like
  amixer set Mix 100 unmute cap
to work.  Well, it doesn't seem to on the snd_intel8x0 driver.

There are instructions for recording an audio stream at the level of PulseAudio in [https://wiki.ubuntu.com/PulseAudio#Recording%20example%20using%20PulseAudio%20and%20Audacity](https://wiki.ubuntu.com/PulseAudio#Recording%20example%20using%20PulseAudio%20and%20Audacity) - so that should work independent of the sound card capabilities.

It seems helpful to install audacity, rosegarden, pavucontrol, paprefs and padevchooser.

---

### Post by Spicywoo on 2011-06-21
I would also welcome an alternative to Total Recorder. In my config, an early audio  TRSE 4.3 (they're now at 8.1, I think) version works, but on XP, not W7. Fine, but what about newbees liike me who are utterly hookied on Kubuntu Natty? I'll give Windows the kiss of death if someone can find a workaround for TR, which I need as a teacher. Thanks in advance for any advice.

---

### Post by mike555 on 2011-06-21
For recording video of desktop there is Kazam or RecordMyDesktop , for audio maybe Audacity.

---

### Post by Habitual on 2011-06-22
> **Barmaleychik said:**
> Is there ANY way to record audio coming through a sound card in Linux?

Any answer will be appreciated :)

Yep, sure is.
[How to Record what comes out of your speakers](http://ubuntuforums.org/showpost.php?p=10191836&postcount=8)

---

