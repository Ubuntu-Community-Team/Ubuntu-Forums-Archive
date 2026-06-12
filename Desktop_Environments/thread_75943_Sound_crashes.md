---
title: "Sound crashes"
date: 2005-10-14
forum: Desktop Environments
---

### Post by DutchR_PW on 2005-10-14
I have a problem with sound in Ubuntu Breezy with my Creatve Audigy 4 Pro (emu10k1 driver):

-GDM, realplayer, gnome-volume-control and amarok (probably others) hang when they try to access sound: The first 1/2 second of sound repeats over and over. When I do a sudo fuser -k /dev/snd/* the hanging sound stops and the apps are killed.

-I also installed kubuntu-desktop because GDM can't log in because of the sound problem (unless I use fuser), and KDE works, but it doesn't produce ANY system sounds. I tried every single option in the list.

-Sound worked in Hoary, as did the remote control (using LIRC).
-The remote control doesn't work in Breezy as well
-cat /dev/urandom > /dev/dsp works: It produces random noise.
-I chmodded the /dev/dsp and /dev/snd/* devices to 666, and I can do cat /dev/urandom > /dev/dsp as normal user.
-When I do killall esd && esd the sound hangs again and it says:

Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

As I said before, it all works perfect in Hoary. Anyone knows what the problem is? Thanks in advance!

---

### Post by DutchR_PW on 2005-10-15
I installed Kubuntu instead of Ubuntu today, and I can play MP3s with amaroK and the gStreamer engine, but system sounds still don't work and the mp3 skips sometimes (it repeats a little piece a few times and continues playing...).

---

### Post by DutchR_PW on 2005-10-19
(First of all, sorry to post 3 times in a row, but since this forum is like quicksand, this seems to be the only way to get a bit attention ;) )

What worked in my 2nd post was still far too less, so I decided to start all over again from a clean Hoary (not Breezy!) on another partition to check if the sound works in a fresh Hoary (with the idea of upgrading it to Breezy later), but it doesn't! This is really weird, because as I said before, my current Hoary (which I don't want to update) runs fine with sound, but the fresh Hoary doesn't!

I did some research using the aadebug script and this are the results:

Hoary with working sound on hda10:
```
ALSA Audio Debug v0.1.0 - Wed Oct 19 14:50:43 CEST 2005
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux aziza 2.6.10-5-k7 #1 Mon Oct 10 11:52:21 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1_synth       7616  0 
snd_emu10k1            98116  7 snd_emu10k1_synth
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  1 
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_emux_synth         36992  1 snd_emu10k1_synth
snd_seq_virmidi         7424  1 snd_emux_synth
snd_seq_midi_emul       7808  1 snd_emux_synth
snd_hwdep               9476  2 snd_emu10k1,snd_emux_synth
snd_util_mem            4480  2 snd_emu10k1,snd_emux_synth
snd_seq_midi            8608  0 
snd_rawmidi            24928  4 snd_emu10k1,snd_seq_virmidi,snd_seq_midi
snd_seq_oss            34240  0 
snd_seq_midi_event      7616  3 snd_seq_virmidi,snd_seq_midi,snd_seq_oss
snd_seq                52752  8 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_timer              25156  3 snd_pcm,snd_seq
snd_seq_device          8524  7 snd_emu10k1_synth,snd_emu10k1,snd_emux_synth,snd_seq_midi,snd_rawmidi,snd_seq_oss,snd_seq
snd                    55268  20 snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_emux_synth,snd_seq_virmidi,snd_hwdep,snd_rawmidi,snd_seq_oss,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Oct 10 2005 for kernel 2.6.10-5-k7.
0 [Audigy2        ]: Audigy2 - Sound Blaster Audigy2
                     Sound Blaster Audigy2 (rev.4) at 0xa000, irq 10
  1:       : sequencer
  0: [0- 0]: ctl
  4: [0- 0]: hardware dependent
  9: [0- 1]: raw midi
  8: [0- 0]: raw midi
 18: [0- 2]: digital audio playback
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  6: [0- 2]: hardware dependent
 10: [0- 2]: raw midi
 11: [0- 3]: raw midi
 33:       : timer
00-00: EMU10K1 (FX8010)
00-02: Emux WaveTable
00-00: emu10k1 : EMU10K1 : playback 32 : capture 1
00-01: emu10k1 mic : EMU10K1 MIC : capture 1
00-02: emu10k1 efx : EMU10K1 EFX : playback 8 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 63:0
Client  63 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
  Output pool :
    Pool size          : 1024
    Cells in use       : 0
    Peak cells in use  : 0
    Alloc success      : 0
    Alloc failures     : 0
Client  64 : "Audigy MPU-401 (UART)" [Kernel]
  Port   0 : "Audigy MPU-401 (UART)" (RWeX)
  Port  32 : "Audigy MPU-401 #2" (RWeX)
Client  65 : "Emu10k1 WaveTable" [Kernel]
  Port   0 : "Emu10k1 Port 0" (-We-)
  Port   1 : "Emu10k1 Port 1" (-We-)
  Port   2 : "Emu10k1 Port 2" (-We-)
  Port   3 : "Emu10k1 Port 3" (-We-)

Dev Snd ---------------------------------------------------
controlC0  hwC0D2    midiC0D1  midiC0D3  pcmC0D0p  pcmC0D2c  seq
hwC0D0	   midiC0D0  midiC0D2  pcmC0D0c  pcmC0D1c  pcmC0D2p  timer

CPU -------------------------------------------------------
model name	: AMD Athlon(tm) XP 2000+
cpu MHz		: 1666.622

RAM -------------------------------------------------------
MemTotal:       516348 kB
SwapTotal:     1044184 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)


```

Hoary without working sound on hda11 for / and hda12 for /home:
```
ALSA Audio Debug v0.1.0 - Wed Oct 19 14:31:22 CEST 2005
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux aziza 2.6.10-5-k7 #1 Tue Apr 5 12:56:05 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_emu10k1            98116  2 
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  0 
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               9476  1 snd_emu10k1
snd                    55268  12 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Apr  5 2005 for kernel 2.6.10-5-k7.
0 [Audigy2        ]: Audigy2 - Sound Blaster Audigy2
                     Sound Blaster Audigy2 (rev.4) at 0xa000, irq 10
  0: [0- 0]: ctl
  4: [0- 0]: hardware dependent
  9: [0- 1]: raw midi
  8: [0- 0]: raw midi
 18: [0- 2]: digital audio playback
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
00-00: EMU10K1 (FX8010)
00-00: emu10k1 : EMU10K1 : playback 32 : capture 1
00-01: emu10k1 mic : EMU10K1 MIC : capture 1
00-02: emu10k1 efx : EMU10K1 EFX : playback 8 : capture 1

cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  midiC0D0  pcmC0D0c  pcmC0D1c  pcmC0D2p
hwC0D0	   midiC0D1  pcmC0D0p  pcmC0D2c  timer

CPU -------------------------------------------------------
model name	: AMD Athlon(tm) XP 2000+
cpu MHz		: 1666.642

RAM -------------------------------------------------------
MemTotal:       516348 kB
SwapTotal:     1044184 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)


```

Also note that I loaded snd-seq-midi and snd-emu10k1-synth for MIDI support in the Hoary with working sound, but sound was working before.

Maybe it has to do with the hda10 <--> hda11/12 difference?

The line
```

cat: /proc/asound/seq/clients: No such file or directory

```
in the non-working Hoary could also point to the problem?

Any help really appreciated and sorry for the long post!

---

