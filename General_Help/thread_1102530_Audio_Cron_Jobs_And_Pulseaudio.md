---
title: "Audio Cron Jobs And Pulseaudio"
date: 2009-03-21
forum: General Help
---

### Post by Patriot1776 on 2009-03-21
Okay, I've got several cronjobs that serve as alarms that have not been working since I decided to get pulseaudio fully working in my system.  What sort of things can I use to get them working again, and what are some programs I can run from the terminal and properly use PulseAudio?

My cronjobs look like this usually:

```
0 1,13 * * * padsp mp3blaster /home/noah/WestminsterChimes/Westminster-Hour-1.mp3
```

Can I swap 'mplayer' for 'mp3blaster' to get this to work?

---

### Post by preserve on 2009-12-26
I also have an alarm script that no longer works with pulseaudio. I've tried to use aplay -Dpulse and mplayer -ao pulse to play the .wav alarm clock file but no sound. It may have to do with the fact that the pulesaudio running process (daemon) belongs to me rather than to crontab. I'm not quite sure if there is a work around - maybe start pulseaudio as user crontab or as root???

---

### Post by Patriot1776 on 2009-12-27
Actually, I did get around this problem in that the audiofiles I am playing are MP3 recordings of timidity output.  The audio recordings and original MIDI files I made serve to turn my computer into a digital chiming clock that chimes the quarter hours and strikes the hours.

Now the typical entries in my crontab files look like this:

```

0 1,13 * * * padsp timidity /home/noah/ChimeSequences/Whittington/Whittington-Hour-1.mid
```

Thanks to this, my computer is back to happily serving as the house's master clock against which the numerous mechanical clocks and timepieces I have are set against and continually compared against for accuracy when it chimes and sounds the hours with these midi sequences in a traditional grandfather clock fashion.

Only thing I just need to know now, that is off-topic, is how to set this thread to [SOLVED].

---

### Post by dcstar on 2009-12-27
> **Patriot1776 said:**
> 
.....
Only thing I just need to know now, that is off-topic, is how to set this thread to [SOLVED].

Use the Thread Tools.

---

