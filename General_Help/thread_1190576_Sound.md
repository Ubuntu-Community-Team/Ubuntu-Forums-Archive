---
title: "Sound"
date: 2009-06-18
forum: General Help
---

### Post by Jenzuko on 2009-06-18
I'm getting no sound out of my Ubuntu 9.04
I just installed it over Windows XP And am now kinda depressed that I can't listen to music.
Any help please?

---

### Post by ~sHyLoCk~ on 2009-06-18
What's the output of:
```
lsmod | grep snd
```

---

### Post by Jenzuko on 2009-06-18
What do you mean?

---

### Post by Awaneendra on 2009-06-18
> **Jenzuko said:**
> I'm getting no sound out of my Ubuntu 9.04
I just installed it over Windows XP And am now kinda depressed that I can't listen to music.
Any help please?

Hi,
How did you install Ubuntu on Windows XP?? Using VMware Server/workstation??

Open the Shell/Terminal and type the following command and let us know the output --

lsmod | grep snd

Cheers,
Awaneendra

---

### Post by ~sHyLoCk~ on 2009-06-18
> **Jenzuko said:**
> What do you mean?

Applications -> Accessories -> Terminal

```
lsmod | grep snd
```

Also maximize the Volumes by typing:
```
alsamixer
```

and with your arrows keys make them full. then do:

```
sudo alsactl store
```

---

### Post by Jenzuko on 2009-06-18
```
snd_hda_intel         435636  8 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  22 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
```

---

### Post by Jenzuko on 2009-06-19
Can anybody help?

---

### Post by Jenzuko on 2009-06-22
Hello?

---

### Post by mynot on 2009-06-22
This may give you some ideas:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
Tony

---

### Post by Jenzuko on 2009-06-22
Sadly, none of that worked.

---

### Post by Jenzuko on 2009-06-24
Any other suggestions?

---

### Post by Jenzuko on 2009-06-26
any at all?

---

### Post by Jenzuko on 2009-06-28
Somebody help me please?

---

### Post by QIII on 2009-06-28
Could you post the specs of your system?

Might be easier to go to the terminal and type 

lspci  (that's a small "el", not a one)

Post the results.

---

### Post by Jenzuko on 2009-06-29
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
```

There you go

---

### Post by Jenzuko on 2009-06-29
Any help?

---

### Post by Jenzuko on 2009-06-30
Hello?

---

