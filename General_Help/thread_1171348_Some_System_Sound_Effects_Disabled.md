---
title: "Some System Sound Effects Disabled"
date: 2009-05-27
forum: General Help
---

### Post by Daddyo-613 on 2009-05-27
Good Morning:[B]

The Problem:[/B] The sound effects for some system functions under the 'Sounds' tab in  System>Preferences>Sound are not working while others work normally. In particular, 'Login' and 'Logout' work normally but 'Empty trash' and 'New e-mail' do not work. All boxes under the 'Sounds' tab have been enabled and are marked with a check mark.

I have updated my libcanberra files from [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) for both Intrepid main and main (Source Code). The current version available in the Intrepid repository is 0.10 0ubuntu1~ppa1 (intrepid) and has been installed on my system. The corresponding associated files such as libcanberra-gtk-module were also updated and installed automatically and they all bear the same version number.

All other sound functions in Sound and Video programs appear to be functioning normally. The issue appears to be confined to the configuration of the system sound effects. 

**My System:** Intrepid[B]

$ uname -a[/B]
```
2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

```[B]
$ cat /proc/asound/cards[/B]
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd6000000 irq 23
```[B]
$ lsmod | grep snd:
[/B]```
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 63268 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm/
```As a test, I downloaded a custom .wav file and changed the default setting for 'Empty Trash' to point to the .wav file. The file does not play when the event occurs (ie when the trash is emptied) but the .wav file will play normally when the cursor hovers on the .wav file in its stored location.

Any guidance would be appreciated.

---

