---
title: "no sound in one user account yet sound in another?"
date: 2006-01-19
forum: General Help
---

### Post by lapsey on 2006-01-19
I had to reinstall and port over backups of /home/user


When I installed I wanted all the nice stuff I had before, some of which was:

gstreamer0.8-plugins-multiverse 
gstreamer0.8-plugins 
gstreamer0.8-ffmpeg 
vorbis-tools 
mozilla-mplayer 
sox audacity 
ffmpeg 
xmms 
xmms-skins 
gxmms

I also recall running "gst-register-0.8" after all this, which worked fine.

After all this installing I set up a "temp" account so i could adduser, chown the backups to the new user and copy them over to the new users home directory before I launched gnome as that user.

This worked ok for the most part, but most importantly sound is fine. 

A few mp3 files and a reboot or two later and I can't access the volume control applet in the gnome panel. I may be mistaken but this may have happened around the time I placed gxmms in the gnome panel.

the sound card is detected, but here is the output of "esd"
> ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return ed error: Permission denied
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er ror: Permission denied
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err or: Permission denied
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: Permission denied
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default


HELP! I have removed and reinstalled all non-essential sound packages (as listed above) and I have no sound whatever I do...

interestingly the "temp" account works fine.

---

### Post by Ducino on 2006-01-19
Is your new user in the audio group ?

If not... sudo adduser username audio

---

### Post by AndyCooll on 2006-01-19
Check also the properties for your new user and that they have permission to use audio.

:cool:

---

