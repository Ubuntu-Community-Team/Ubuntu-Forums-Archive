---
title: "Sound Issues"
date: 2009-03-07
forum: General Help
---

### Post by Irishbmx on 2009-03-07
Ok my heads about to explode.

I don't know what info you need so just ask I will try to supply anything I can.

My problem is I have really choppy sound esp on teamspeak, I had this fixed for a wile I don't know what happened I was messing with sound setting and screwd it up again :(

I really have no Idea what I'm doing but I've try'd many terminal commands on other threads tryd to uninstall pulseaudio installed Pulse audio applet or device chooser whatever it's called try changing all my sound settings I don't know what I'm doing I'm a total Idiot to this stuff please please help me lol I'll love you forever.

:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)

I use xfx 8200 mother board AMD atholon 64 amd socket AMD2+

I'll try anything I may have to uninstall all the pulseaudio stuff and start from scratch if that's posible because of all the commands and stuff I've tryd ect.

---

### Post by Irishbmx on 2009-03-07
sorry for the fast bump still trying to get it to work on my own I just had this pop up

Refresh Advanced Linux Sound Architecture (ALSA) configuration presets

New Advanced Linux Sound Architecture (ALSA) configuration presets have been added.  Please execute the asoundconf(1) set-default-card macro in a Terminal now to refresh your user's configuration presets.  You may accomplish this task by executing the following command in a Terminal: asoundconf set-default-card

in a little litebulb thing.

anyone have any suggestions?

---

### Post by Irishbmx on 2009-03-08
still trying to figure this out on my own and created a new problem.

Followed walkthru [http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+static](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+static)
and now my internet stops working unless I go into system monitor and kill pulseaudio.

here is some more info

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pkill pulseaudio; sleep 2; pulseaudio -vv  displays

I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_774_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_774_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_774_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_774_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_10de_774_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_10de_774_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_10de_774_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_774_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_10de_774_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_10de_774_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_774_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_774_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-null-sink' with args 'sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"' due to GConf configuration.
I: sink.c: Created sink 1 "rtp" with sample spec "s16be 2ch 44100Hz"
I: source.c: Created source 2 "rtp.monitor" with sample spec "s16be 2ch 44100Hz"
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-null-sink" (index: #5; argument: "sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"").
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=rtp.monitor loop=1' due to GConf configuration.
I: source-output.c: Created output 0 "RTP Monitor Stream" on rtp.monitor with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46218, SSRC=0xe6595a41, payload=10, initial sequence #29868
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=sile 3445484425 0 IN IP4 12.201.36.34
I: module-rtp-send.c: s=PulseAudio RTP Stream on Pudding
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3445484425 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46218 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #6; argument: "source=rtp.monitor loop=1").
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 2 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 3 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ALC883 Analog) via DMA" on alsa_output.pci_10de_774_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_10de_774_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-combine" (index: #7; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args '' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #9; argument: "").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args '' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #10; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #11; argument: "").
I: module.c: Loaded "module-gconf" (index: #12; argument: "").
I: module-volume-restore.c: starting with empty ruleset.
I: module.c: Loaded "module-volume-restore" (index: #13; argument: "").
D: module-default-device-restore.c: Restored default sink 'rtp'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'rtp.monitor'.
I: module.c: Loaded "module-default-device-restore" (index: #14; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #15; argument: "").
D: module-suspend-on-idle.c: Sink rtp becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_10de_774_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_774_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #16; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #17; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_774_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_10de_774_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_774_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_774_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ALC883 Analog) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink rtp idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_774_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-suspend-on-idle.c: Sink rtp becomes idle.
D: module-suspend-on-idle.c: Sink rtp becomes busy.
I: sink-input.c: Created input 1 "RTP Stream (PulseAudio RTP Stream on Pudding)" on rtp with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=17641, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=17644, minreq=4
I: module-rtp-recv.c: New session 'PulseAudio RTP Stream on Pudding'
W: module-rtp-recv.c: Detected RTP packet loop!
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...

and then keeps doing that

---

### Post by networm1230 on 2009-03-08
hello!  I do not have a sound card on my PC. but anyway I will try to help you. what distribution are you using Linux/Unix? I am using Ubuntu 8.04 hardy. if you are using Ubuntu OS go to the system/preferences/sound options. for each sound device change it to your choosing of sound input/output. after you change a sating test the setting out you should hear a high pick sound the high pitch sound means that the sound sating you put it at works. after you are don sating sound. restart you computer.

note: when you install hardware. Be shore to chack you BIOS to see if you Motherboard know the device you installed

---

### Post by hello_kitty on 2009-03-08
If you are using Jaunty, beware!  The alpha currently (or did at least) have an issue with the pulseaudio sound server.  The workarounds involved killing pulseaudio or disabling the themed sounds in ubuntu.

---

### Post by networm1230 on 2009-03-08
hello again

Another possible sound fix for you mite be sound codec's. go to applications than add/remove (repository) when you are their search (all) for all gstreamer codec's and install theme all. The codec's lat you to play different formats of sound and video files

---

### Post by Irishbmx on 2009-03-08
> **networm1230 said:**
> hello!  I do not have a sound card on my PC. but anyway I will try to help you. what distribution are you using Linux/Unix? I am using Ubuntu 8.04 hardy. if you are using Ubuntu OS go to the system/preferences/sound options. for each sound device change it to your choosing of sound input/output. after you change a sating test the setting out you should hear a high pick sound the high pitch sound means that the sound sating you put it at works. after you are don sating sound. restart you computer.

note: when you install hardware. Be shore to chack you BIOS to see if you Motherboard know the device you installed
I'm using Ubuntu 8.04 I've already messed with all the sound settings and yes I get the sounds my problem is staticy/choppy sound that comes in and out and the sound card is integrated and bios detects it.

---

### Post by Irishbmx on 2009-03-08
> **hello_kitty said:**
> If you are using Jaunty, beware!  The alpha currently (or did at least) have an issue with the pulseaudio sound server.  The workarounds involved killing pulseaudio or disabling the themed sounds in ubuntu.
not sure what jaunty is.

---

### Post by hello_kitty on 2009-03-08
> **Irishbmx said:**
> not sure what jaunty is.

Jaunty=Ubuntu 9.04

---

### Post by Irishbmx on 2009-03-08
> **networm1230 said:**
> hello again

Another possible sound fix for you mite be sound codec's. go to applications than add/remove (repository) when you are their search (all) for all gstreamer codec's and install theme all. The codec's lat you to play different formats of sound and video files

didn't seem to change anything but ty.

---

### Post by Irishbmx on 2009-03-08
> **hello_kitty said:**
> Jaunty=Ubuntu 9.04
oh I use 8.04 32 bit edition

---

### Post by Irishbmx on 2009-03-08
Bump still havn't figured anything out anyone?

---

### Post by networm1230 on 2009-03-08
> **Irishbmx said:**
> Bump still havn't figured anything out anyone?

try to update you sound drivers or your BIOS completely of you motherboard

---

### Post by networm1230 on 2009-03-08
What motherboard do you have?. look on you manufacturer web site of your motherboard for BIOS drives update

---

### Post by Irishbmx on 2009-03-08
> **networm1230 said:**
> What motherboard do you have?. look on you manufacturer web site of your motherboard for BIOS drives update

it's the XFX Geforce 8200 board trying to find the bios update for it XFX site sux doesn't have ****.

---

### Post by networm1230 on 2009-03-09
Irishbmx! I have gone to the Gforce waeb site and did not find drivers for your Motherboard. maybe you can try Gforce support [http://www.xfxforce.com/en-us/Help/Support.aspx](http://www.xfxforce.com/en-us/Help/Support.aspx) I am still on the look out for your motherboard BIOS updates.


note:fun stuff  [http://video.mpora.com/bmx/](http://video.mpora.com/bmx/)

---

### Post by Irishbmx on 2009-03-11
> **networm1230 said:**
> Irishbmx! I have gone to the Gforce waeb site and did not find drivers for your Motherboard. maybe you can try Gforce support [http://www.xfxforce.com/en-us/Help/Support.aspx](http://www.xfxforce.com/en-us/Help/Support.aspx) I am still on the look out for your motherboard BIOS updates.


note:fun stuff  [http://video.mpora.com/bmx/](http://video.mpora.com/bmx/)

I ended up just putting a different sound card in and It works now the only problem I have is when pulseaudio is running it sux up all my bandwidth or something cause it won't let me get on the internet so I have to kill the proccess.

---

### Post by networm1230 on 2009-03-12
> **Irishbmx said:**
> I ended up just putting a different sound card in and It works now the only problem I have is when pulseaudio is running it sux up all my bandwidth or something cause it won't let me get on the internet so I have to kill the proccess.

check to see if the sound card is supered by you OS?. Get the latest drives for the sound card. What sound card is it?. this may help you [http://tldp.org/HOWTO/Sound-HOWTO/x96.html](http://tldp.org/HOWTO/Sound-HOWTO/x96.html)
 
note: I never used a sound card except the motherboards integrand one's.

---

