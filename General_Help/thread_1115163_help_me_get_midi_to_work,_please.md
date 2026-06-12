---
title: "help me get midi to work, please"
date: 2009-04-03
forum: General Help
---

### Post by adamgram on 2009-04-03
I've been using ubuntu for a while now, but only really at the user level for web browsing and word processing. I'm no expert for sure. I still use windows on my desktop because I have a lot of software for recording music on that computer. I'd like to get into some of the Ubuntu programs for music on my laptop, which has Ubuntu 8.04 on it, but I'm having trouble getting midi to work.

All I really want to be able to do for now is write out music in rosegarden and hear sound when I hit play.

I downloaded Jack and QSynth, but I'm a little confused as to what exactly these things are supposed to do. From what I understand Jack is what routes your sounds from various programs to your soundcard? Am I right about that? What about QSynth though? Does this provide sounds from MIDI signals it imports from another program, or should this be able to make sounds by itself?

I followed a how-to I found here [http://ubuntuforums.org/showthread.php?t=8736](http://ubuntuforums.org/showthread.php?t=8736) and ran into some problems. I copied and pasted the whole thing below, things with an 'x' beside it worked, and things with a *** beside it are the error messages I got while trying to get it to work. Any help is appreciated, thanks.






HOWTO: Getting MIDI to work fully in Ubuntu
MIDI: Getting to Create, Play, Anything with Ubuntu!

Intro
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult; you just need the right packages and a loaded GM Soundfont.

Prerequisites
- A MIDI enabled sound card (most people have a SoundBlaster Audigy or Live! card-- if you have onboard sound, meaning the motherboard does the MIDI work, you'll need to use FluidSynth, which I'll talk about later).
*** I have ATI IXP AC97 onboard sound

- A fully working ALSA sound system.
*** ALSA shows up under system--> preferences--> sound and the test sound plays for everything EXCEPT sound capture

- A fully working OSS sound system. (in case the upper doesn't work, you can use this and then do a sudo modprobe snd-seq-oss)
*** OSS shows up under system--> preferences--> sound but I get an error message when I hit the 'test' button:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

- The following ALSA packages installed (get these through apt-get/synaptic/aptitude):
x alsa-base,
libasound,
*** E: Couldn't find package libasound, I do have libasound2
alsa-headers,
***
heather@heather-laptop:~$ sudo apt-get install alsa-headers
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package alsa-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
libasound2-dev
E: Package alsa-headers has no installation candidate

x libasound-dev,
alsa-modules-2.4.26-1-686 (replace the 686 with 586, 386, k6, k7, etc. according to your system),
*** E: Couldn't find package alsa-modules-2.4.26-1-686

x alsa-oss,
x alsa-source.

- A program that plays MIDI files. (KMid is a nice one)
*** E: Couldn't find package KMid

x The awesfx package if you are not using FluidSynth. (get this through apt-get)

Blood, Sweat, and Tears time (not really)
You've gotten past most of the work which took me the most time. Some of the packages you install may seem like overkill, but for people who use FluidSynth and have to compile it and other things, those packages are good to have just in case.

Do an lsmod in the terminal. It should return something like this

Quote:
snd_seq_midi 8096 1
snd_emu10k1_synth 6784 4
snd_emux_synth 33408 5 snd_emu10k1_synth
snd_seq_virmidi 7296 1 snd_emux_synth
snd_seq_midi_emul 7680 1 snd_emux_synth
snd_seq_oss 29440 0
snd_seq_midi_event 7552 3 snd_seq_midi,snd_seq_virmidi,snd_seq_oss
snd_seq 46608 19 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_se q_midi_emul,snd_seq_oss,snd_seq_midi_event
nls_iso8859_1 4352 2
nls_cp437 6016 2
vfat 13312 2
fat 41792 1 vfat
i830 68644 6
proc_intf 3968 0
freq_table 4356 0
cpufreq_userspace 5336 0
cpufreq_powersave 2048 0
button 6936 0
ac 5132 0
battery 9740 0
ipv6 230020 8
af_packet 20872 2
8139too 23936 0
8139cp 19072 0
mii 4864 2 8139too,8139cp
crc32 4608 2 8139too,8139cp
emu10k1_gp 3840 0
gameport 4736 1 emu10k1_gp
snd_emu10k1 80776 11 snd_emu10k1_synth
snd_rawmidi 23232 3 snd_seq_midi,snd_seq_virmidi,snd_emu10k1
snd_pcm_oss 48168 0
snd_mixer_oss 16640 3 snd_pcm_oss
snd_pcm 85540 3 snd_emu10k1,snd_pcm_oss
snd_timer 23172 2 snd_seq,snd_pcm
snd_seq_device 7944 7 snd_seq_midi,snd_emu10k1_synth,snd_emux_synth,snd_ seq_oss,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec 59268 1 snd_emu10k1
snd_page_alloc 11144 2 snd_emu10k1,snd_pcm
snd_util_mem 4608 2 snd_emux_synth,snd_emu10k1
snd_hwdep 9120 2 snd_emux_synth,snd_emu10k1
snd 50660 27 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_se q_oss,snd_seq_midi_event,snd_seq,snd_emu10k1,snd_r awmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer ,snd_seq_device,snd_ac97_codec,snd_util_mem,snd_hw dep
soundcore 9824 3 snd
pci_hotplug 30640 0
ehci_hcd 27780 0
uhci_hcd 29328 0
usbcore 104292 4 ehci_hcd,uhci_hcd
intel_agp 20512 1
agpgart 31784 3 intel_agp
pcspkr 3816 0
rtc 12216 0
floppy 54996 0
md 44744 0
dm_mod 51068 1
capability 4872 0
commoncap 7168 1 capability
parport_pc 32064 1
lp 10436 0
parport 37320 2 parport_pc,lp
tsdev 7168 0
ide_cd 38276 0
cdrom 35872 1 ide_cd
evdev 9088 0
mousedev 10124 1
psmouse 17800 0
ext3 109544 1
jbd 54552 1 ext3
ide_generic 1664 0
piix 12576 1
ide_disk 16768 5
ide_core 125272 4 ide_cd,ide_generic,piix,ide_disk
unix 25904 762
fan 4236 0
thermal 13200 0
processor 17712 1 thermal
font 8576 0
vesafb 6688 0
cfbcopyarea 3968 1 vesafb
cfbimgblt 3200 1 vesafb
cfbfillrect 3712 1 vesafb
If you don't see any MIDI related modules (the important ones are
x snd_seq_midi,
snd_emu10k1_synth,
*** E: Couldn't find package snd_emu10k1_synth
snd_emux_synth,
*** E: Couldn't find package snd_emux_synth
x snd_ seq_oss,
x snd_seq,
snd_emu10k1,
*** E: Couldn't find package snd_emu10k1

x snd_rawmidi
),
then that means ALSA hasn't been configured properly. Try sudo modprobe for these modules, and see what results.

Now, that you have MIDI devices working, go over to [http://www.hammersound.net](http://www.hammersound.net), go to Sounds -> Soundfont Library -> Collections (this is over at the bottom). Now, find a GM library which you think will sound good, etc. I am using the Ultimate GM/GS Soundfont collection, which can be downloaded through [http://www.hammersound.net/cgi-bin/s...d=Ultimate.zip](http://www.hammersound.net/cgi-bin/s...d=Ultimate.zip)

Now, download it to your home directory. This one should be in a ZIP file (note: if it is in sfArk form, continue reading), so simply unzip it and there should be a sf2 file inside it. Go to the terminal and do a sfxload thenameofthefile.sf2. It should return to a new $ line, and that is good. Go into KMid and open up a MIDI and it should work. You can use Rosegarden 4 (apt-get install rosegarden4) to create MIDIs with ease and a bit of musical knowledge.

FLUIDSYNTH
FluidSynth is a software synthesizer, meaning there is no hardware involved since your card doesn't support SoundFont synthesis (otherwise, you shouldn't be doing this, hehe). It obviously doesn't relay as much quality as hardware does, but that's a small price to pay. You can find their homepage at [http://www.fluidsynth.org/](http://www.fluidsynth.org/).

It can also be easily installed through apt-get. Once it is installed, open up your terminal and do this: fluidsynth -m alsa_seq ./thenameofthefilehere.sf2. This will load the soundfont into your computer's memory.

Now, that wasn't difficult was it? Open up whatever MIDI program and you should be able to listen to your MIDIs.

SFARK
sfArk is a common compression method composers use to zip up their SoundFonts, and luckily, the company behind it has a Linux version of their utility. Download it at [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). It is a command-line based utility, but again, easy to use. Just do this: sfarkxtc ./thenameofthefilehere.sfArk

That should decompress the sfArk and give you a .sf2 file. If it gives you any other kind (such as an EXE), that means you'll have to move onto another soundfont since this one won't be usable.

CONCLUSION
This hasn't been 100% tested, but it worked just fine for me and I hope it does for you as well. Post all of your errors, suggestions, comments, and I'll be happy to edit them into this. May your musical talent flourish with Ubuntu
Last edited by Quest-Master; December 20th, 2004 at 02:41 PM..

---

