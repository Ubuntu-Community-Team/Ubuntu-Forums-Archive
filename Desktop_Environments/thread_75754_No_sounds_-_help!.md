---
title: "No sounds - help!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Loony on 2005-10-14
:razz: [FONT="Century Gothic"][SIZE="3"][/SIZE][/FONT]

I am a very new user of ubuntu and a computer novice.  Although I am not very experienced with computers I am getting on fine except for one thing - I am having difficulties getting the sound to work.  There is a sound card attatched.
I have tried "sound Preferences" and "multimedia" but no luck. 
Has anyone got a suggestion to help me?  I am far from a programmer so it would have to be spelled out to me in easy terms.
I do hope someone can help!

---

### Post by tehwa on 2005-10-14
First check:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

If this shows you no love, make sure that Ubuntu has detected and setup your card correctly with this command: ```
aplay -l
``` View the output and make sure that all is well.

If all is well and you still have no sound, reply with progress that you have made, and include the output of aplay- l.

---

### Post by denkedran on 2005-10-14
you could bring up a console and try the following:

1.
type 'alsamixer' into the console.
perhaps your channel are only mutedt, so that you can't here anything.
if there are no driver loaded for your soundcard the programm will complain.

2. ( if 1. doesn't work )
type 'lsmod | grep snd' into the console
if the drivers were loaded they should appear after that command

2a.
you see no output from that command - > there are no drivers loaded
if you have an old computer perhaps with an old isa-sound-card you should install isapnp by typing 'sudo apt-get install isapnptools'. After that reboot your computer and see what happens

2b.
show us the output of 'lsmod | grep snd' and the model and vendor of your soundcard and tell us whcih programm(s) you used for the sound-test

---

### Post by bionnaki on 2005-10-14
I am also having having problems with sound. I have an soundblaster audigy 2 soundcard.

bill@ubuntu:~$ aplay -l
aplay: device_list:218: no soundcards found...


bill@ubuntu:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

bill@ubuntu:~$ lsmod | grep snd
(no output)

any ideas?

---

### Post by denkedran on 2005-10-14
the hotplug system doesn't recognise your card.
according to [alsa-dirver-page]("http://alsa.opensrc.org/AlsaDrivers")
there is no support for soundblaster audigy 2, but that's only for the pcmcia-card. The driver for other audigy cards is the following> emu10k1 - Creative SBLive! (EMU10K1), Audigy, Audigy 2 and Audigy 2 Value
the modulename of the driver is "snd-emu10k1". I think a "sudo modprobe snd-emu10k1" should bring up the driver. then try changing the volume with "alsamixer"

PS: [http://alsa.opensrc.org/emu10k1]("http://alsa.opensrc.org/emu10k1") ; this is a good place to get informations on linux-support for your card

---

### Post by greengrass on 2005-10-14
I am having sound problems too.  I have a creative tech sound card  Not detected.  No sound whatsoever.

---

### Post by bionnaki on 2005-10-14
thanks for the reply denkedran.
when I "sudo modprobe snd-emu10k1" I get this:

> bill@ubuntu:~$ sudo modprobe snd-emu10k1
Password:
FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1


any ideas?

surely this card can work - it worked perfectly under hoary following these instructions: [http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211)

>  AUDIGY 2 USERS:
Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10

cd /usr/src
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2)
tar xvjf alsa-driver-1.0.8.tar.bz2
cd alsa-driver-1.0.8
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss

Then reboot your pc you should have sound. You might have to run alsamixer after you reboot to turn on the analog/digital output jack if you are an Audigy 2 user.

---

### Post by denkedran on 2005-10-17
please do the following:

> find  /lib/modules/`uname -r`/  | grep emu10k1

the result has to be:

> /lib/modules/2.6.12-9-k7/kernel/drivers/input/gameport/emu10k1-gp.ko
/lib/modules/2.6.12-9-k7/kernel/sound/oss/emu10k1
/lib/modules/2.6.12-9-k7/kernel/sound/oss/emu10k1/emu10k1.ko
/lib/modules/2.6.12-9-k7/kernel/sound/pci/emu10k1
/lib/modules/2.6.12-9-k7/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.12-9-k7/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.12-9-k7/kernel/sound/pci/emu10k1/snd-emu10k1x.ko

except for the kernel-number

---

### Post by aham925925 on 2005-10-17
I have a Creative SoundBlaster Audigy LS and i have a similar problem.  My problem is that the music player plays as if sound is playing although there is no sound coming out

there seems to be drivers installed and everything

any thoughts?

---

### Post by denkedran on 2005-10-17
do you have unmuted your channels ? Both "master" and "pcm" has to be unmuted. you can do that with either alsamixer ( type in at console ) or  using the volume panel applet. Stupid question, but did you put your speakers in the correct jack.

---

### Post by evilmrt on 2005-10-17
I'm having problems suddenly as well, so I'll jump in here ;) 

I have a emu10k1 card, a Live 5.1 pci card. It worked fine in Hoary...I upgraded today, and now it does not. However...

The sound works partially. I can play music in BMP, XMMS, Xine,  but not in Rhythmbox, Sound Recorder, or other Gnome apps. Also, the system sounds dont work, **and **the volume control applet doesn't appear on the desktop panel. 

Under Sound Prefs, "SB Live [Unknown]" shows up as my only option. 

Whats going on?

---

### Post by denkedran on 2005-10-17
what kind of outputplugins do you use in beep-media-player, xmms and xine ?
rhythmox uses gstreamer. you can set the gstreamer-output with gstreamer-properties (type in console).
What about the volume control applet. It doesn't show up when you want to add it ? Or isn't it there by default. Can you open voulume-control from the apps-menu ?

---

### Post by evilmrt on 2005-10-18
Thanks! :)  gstreamer was set to ESD, I switched it over to ALSA and it (Rhythmbox) works fine now. System sounds still do not work, neither does previewing system sounds in the Sound Preferences menu. Any reason I need ESD? 

Yes, volume-control will run if I launch it manually from the apps menu. The applet just refuses to add to my menubar. Is there a way to manually (non gui) add it in?

---

### Post by denkedran on 2005-10-18
does esd starts when you log into gnome ?
Means: is the option "start sound server on start up" enabled in system sounds.

What does a "ps ax | grep esd" shows ?
What does a "cat /etc/libao.conf" shows ?
What does a "lsmod  | grep oss" shows ?

---

### Post by evilmrt on 2005-10-18
[I]does esd starts when you log into gnome ?
Means: is the option "start sound server on start up" enabled in system sounds.[/I]

Yes, it is enabled. 

*What does a "ps ax | grep esd" shows ?*

19322 pts/0    R+     0:00 grep esd

*What does a "cat /etc/libao.conf" shows ?*

default_driver=esd

*What does a "lsmod  | grep oss" shows ?*

```
snd_seq_oss            33664  0
snd_seq_midi_event      7040  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51024  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_pcm_oss            53152  0
snd_mixer_oss          19392  2 snd_pcm_oss
snd_pcm                89032  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd                    55172  23 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

```

---

### Post by denkedran on 2005-10-19
> *What does a "ps ax | grep esd" shows ?*

19322 pts/0    R+     0:00 grep esd

Ok this means, that esd is not startet

try to start it manually and look why esd fails to start
( type 'esd' on console )

> *What does a "cat /etc/libao.conf" shows ?*

default_driver=esd

You could set this to 'alsa' instead of 'esd'

> *What does a "lsmod  | grep oss" shows ?*

```
snd_seq_oss            33664  0
snd_seq_midi_event      7040  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51024  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_pcm_oss            53152  0
snd_mixer_oss          19392  2 snd_pcm_oss
snd_pcm                89032  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd                    55172  23 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

```


Ok oss-emulation is turn on.

---

### Post by evilmrt on 2005-10-19
trying to start ESD at the console does nothing...it shows no message, and it does not seem to be running either. :confused:

---

### Post by denkedran on 2005-10-19
try starting esd with the following command
```
esd -vt -vc -vm
```
this will give you some information on what went wrong on startup

---

### Post by curd on 2005-10-24
I seem to have the exact same problem. Sound was working fine before upgrade, and now in Breezy no joy...

It seems that alsa never quite seems to start up.
When I do esd -vt -vc -vm I get this :

- enabling trace diagnostic info
- enabling comms diagnostic info
- enabling mixer diagnostic info
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

this is also comes up while trying aplay:
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
aplay: main:533: audio open error: No such file or directory

Hth...

---

### Post by davebgimp on 2005-10-24
I had the same problem. SoundBlaster Audigy 2 installed. Everything should be working, but no sound. Checking the sound preferences, I noticed it was still set to send sound to the built-in card on my Dell pc, not the SoundBlaster that I had manually installed. Adjusting this fixed the issue. I also had to set this in other sound programs like xmms. Everything works great now.

---

### Post by Michael Matthews on 2005-10-27
With audigy 2 you have to use alsamixer. If you are using just stereo speakers you
must turn up pcm-front, analog-mix which are not available with volume control app.

Once you do this volume control should work.

This was confusing to me also.

For surround sound I don;t know because I don't have that setup.

---

### Post by ThirdWorld on 2005-10-31
i have audio problems. the system sound works sometimes, and sometimes it stops. However, application like XMMS always work after I configure it in preferences to use Alsa. When i open the multimedia system selector in system it said "failed to construct pipeline for alsa" 

all my problems started when i tried to install my plantronics USB headset. 

wen i type this in console: cat /proc/asound/modules

it shows: 1 snd_emu10k1

it used to be: 0 snd_emu10k1

can somebody knows how i can return my sound card to default 0?

---

### Post by iNerdSure on 2005-11-01
Dear Ubuntu experts,

Allow me to join in. I have been trying to get the sound working on my laptop since the release of Breezy Badger, without any success.

ins@inerdsure:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ins@inerdsure:~$

I've also tried running ALSA and unmuted all the controls. But no success.

Can some experts from the forum help me. Many thanks.

---

### Post by brucemilne on 2005-11-26
[QUOTE=iNerdSure]Dear Ubuntu experts,

Allow me to join in. I have been trying to get the sound working on my laptop since the release of Breezy Badger, without any success.

ins@inerdsure:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ins@inerdsure:~$

I've also tried running ALSA and unmuted all the controls. But no success.

Can some experts from the forum help me. Many thanks.[/QUOTE]

I'm no expert, but I've had this issue too:

Toshiba A70, had lots of sound issues.  Followed the ubuntu 'how tos', setup asound as directed, looked at permission issues, looked at alsamixer levels, killed off esd when it shows up (tempted to write blah, blah, blah) and my sound works: well sometimes.  I can boot up, hear sound on the login page, but then when I log in my sound disappears and I don't hear the nice little login sound.  And, when using xmms, xine or whatever, I get the message that the sound card is busy.
bruce@bpmLaptop:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Then, on another reboot, the sound might work.  Or perhaps on the 3rd try.

Just now, I did a 'killall aplay' since they were hung from the login sound and starting a terminal, then did a:

sudo aplay /usr/src/alsa/alsa-utils-1.0.9a/speaker-test/samples/Side_Right.wav
Playing WAVE '/usr/src/alsa/alsa-utils-1.0.9a/speaker-test/samples/Side_Right.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

and it worked!!  now xmms and all sound works fine!!  Perhaps if I could explain this, I would be an expert!  ;)

---

