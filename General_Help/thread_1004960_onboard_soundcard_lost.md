---
title: "onboard soundcard lost"
date: 2008-12-07
forum: General Help
---

### Post by kakyoism on 2008-12-07
I followed the most popular pulseaudio fix post for Hardy/Intrepid here and it works well until...

...I resumed from suspend and found that my onboard soundcard (hw:0) can't be found on pulseaudio. Or not exactly, the flash in Firefox is still working.

But when I direct audio stream to the device through pavucontrol, the players refused to play. 
See output of command "pulseaudio -vv"
```
me@me-laptop:$ pulseaudio -vv
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_41e_3040_noserial_if0_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround51:1...
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:1...
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:1...
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:1...
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:1...
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:1...
I: module-alsa-source.c: Successfully opened device front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 0 "alsa_input.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'front-right', falling back to software volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-alsa-source" (index: #0; argument: "device_id=1 source_name=alsa_input.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround51:1...
I: module-alsa-sink.c: Successfully opened device surround51:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:1
I: alsa-util.c: Unable to attach to mixer surround51:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master".
I: alsa-util.c: Using mixer control "PCM".
I: sink.c: Created sink 0 "alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0" with sample spec "s16le 6ch 44100Hz"
I: source.c: Created source 1 "alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 6ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 2640 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #1; argument: "device_id=1 sink_name=alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_41e_3040_noserial_if0_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_playback_6
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_capture_6
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: PCM device surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: PCM device surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: PCM device surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: PCM device surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: PCM device surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: PCM device surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: PCM device surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: PCM device surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: PCM device surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: PCM device surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 3 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_hw_specific_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=@DEFAULT_MONITOR@ loop=0' due to GConf configuration.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: source-output.c: Created output 0 "RTP Monitor Stream" on alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0.monitor with sample spec s16be 6ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=12, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174084, tlength=174084, base=12, prebuf=12, minreq=12
I: module-rtp-send.c: RTP stream initialized with mtu 1272 on 224.0.0.56:46066, SSRC=0x17985f14, payload=127, initial sequence #22069
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=kakyo 3437684383 0 IN IP4 192.168.1.103
I: module-rtp-send.c: s=PulseAudio RTP Stream on kakyo-laptop
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3437684383 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46066 RTP/AVP 127
I: module-rtp-send.c: a=rtpmap:127 L16/44100/6
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #7; argument: "source=@DEFAULT_MONITOR@ loop=0").
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 2 "combined" with sample spec "s16le 6ch 44100Hz"
I: source.c: Created source 4 "combined.monitor" with sample spec "s16le 6ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=12, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174084, tlength=174084, base=12, prebuf=12, minreq=12
D: resampler.c: Channel matrix:
D: resampler.c:        I00   I01   I02   I03   I04   I05 
D: resampler.c:     +------------------------------------
D: resampler.c: O00 | 1.000 0.000 0.000 0.000 0.000 0.000
D: resampler.c: O01 | 0.000 0.000 0.000 1.000 0.000 0.000
D: resampler.c: O02 | 0.500 0.500 0.000 0.000 0.000 0.000
D: resampler.c: O03 | 0.000 0.000 0.000 0.500 0.500 0.000
D: resampler.c: O04 | 0.000 0.000 1.000 0.000 0.000 0.000
D: resampler.c: O05 | 0.000 0.000 0.000 0.000 0.000 1.000
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on surround51:1 (USB Audio) via DMA" on alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0 with sample spec s16le 6ch 44100Hz and channel map front-left,side-left,front-center,front-right,side-right,lfe
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=12, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174084, tlength=174084, base=12, prebuf=12, minreq=12
D: resampler.c: Channel matrix:
D: resampler.c:        I00   I01   I02   I03   I04   I05 
D: resampler.c:     +------------------------------------
D: resampler.c: O00 | 0.675 0.100 0.375 0.000 0.000 0.375
D: resampler.c: O01 | 0.000 0.000 0.375 0.675 0.100 0.375
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 1 "Simultaneous output on ALSA PCM on front:0 (ALC268 Analog) via DMA" on alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 with sample spec s16le 6ch 44100Hz and channel map front-left,side-left,front-center,front-right,side-right,lfe
I: module-combine.c: Master sink is now 'alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+25
I: module.c: Loaded "module-combine" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #9; argument: "").
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #11; argument: "").
I: module-default-device-restore.c: Manually configured default sink, not overwriting.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #12; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #13; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #15; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on surround51:1 (USB Audio) via DMA"
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 1 "Simultaneous output on ALSA PCM on front:0 (ALC268 Analog) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.usb_device_41e_3040_noserial_if0_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
```

---

