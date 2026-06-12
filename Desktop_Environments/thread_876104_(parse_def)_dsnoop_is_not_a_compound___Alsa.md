---
title: "(parse_def) dsnoop is not a compound  : Alsa"
date: 2008-07-31
forum: Desktop Environments
---

### Post by ash12345 on 2008-07-31
Hi,
I am not able to use my sound card on my system.  I tried dubbing using various commands relating to sound/alsa and everytime i get the following error
(parse_def) dsnoop is not a compound
*********
ALSA lib conf.c:1177: (parse_def) dsnoop is not a compound
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:24:32:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /root/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration
************
I would appreciate if someone can help me on this topic
Thanks,
Ash

---

### Post by ash12345 on 2008-07-31
problem is the configuration file in my root login.  I removed it and it works.  Debugged this by trying the commands(aplay -l) in some other login and they work fine.

---

