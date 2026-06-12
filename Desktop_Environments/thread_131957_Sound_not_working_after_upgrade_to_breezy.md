---
title: "Sound not working after upgrade to breezy"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Jaymoid on 2006-02-17
Hi,

My sound worked fine in hoary, but I upgraded to breezy a couple of months ago and since then ALSA has not been working. In fact I can't get any sound at all from OSS or ALSA.

lspci reports that my card is:
0000:01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

lsmod | grep snd results:
snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

And when I try and restart ALSA I get this:

 sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...  * /etc/init.d/alsa-utils: Warning: 'alsactl store' failed with error message 'alsactl: save_state:1163: No soundcards found...'.
                                                                                                                     [fail]
 * Setting up ALSA...                                                                                                [ ok ]

Which suggests that it no longer knows about the soundcard.

I have tried everything on here: [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

But still no luck... if anyone has any ideas - it would be greatly appreciated.

Many Thanks
James

---

