---
title: "pulseaudio not loading...any help?"
date: 2009-06-09
forum: General Help
---

### Post by MimziM on 2009-06-09
Last night I had an unexpected shutdown (power cut) then I could not log in.
Inside a failsafe terminal, I discovered that permision was denied to anyone for
/tmp . so no problem I changed permissions and was able to log in again
but I'd lost my 5.1 sound.  
When I try run pulseaudio from from terminal i get this:
```

damian@Badass:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:0
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0"): initialization failed.
E: authkey.c: Failed to open cookie file '/home/damian/.esd_auth': Permission denied
E: authkey.c: Failed to load authorization key '/home/damian/.esd_auth': Permission denied
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```

Can anyone help me?

---

### Post by MimziM on 2009-06-09
okay if i cant fix
can i do a repair installation 
without hurting data
and settings eg. firefox tabs/history etc.

---

