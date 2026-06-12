---
title: "Sound in Win partition thru Ubuntu no audio in Ubuntu"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Almighty on 2006-02-14
Hey everyone,

Got another seemingly impossible problem here. I have noticed that I do not have audio in Ubuntu. I don't have any system sounds, and I don't have audio from any MP3, MPeg,WMV, or AVI files.

My system has been updated, I have gone through the multimedia systems selector menu, and all codecs are the newest that I am aware of. I do not see the volume Icon that once called my task bar home. I cannot open the volume control menu through the GUI (Don't know the command to try it in terminal). Other problems that I see is, when I launch any video player, the crash imediately or hang for a few moments and then crash. Mplayer seems to fair better than others because it will play a video but without audio. 

The biggest clue I have to what is going on is the fact that when I attempt to view or listen to any media in my 2 windows partition. It seems that every thing works there. No real problems that I see. 

So.. yeah, any help will be needed and greatly appreciated.

---

### Post by grinchy on 2006-02-15
do you have alsa loaded?

sudo /etc/init.d/alsa force-reload

---

### Post by Almighty on 2006-02-15
Looks like it loaded sucessfully.. still no audio though.

---

### Post by Almighty on 2006-02-15
When I try to launch Totem in terminal I get this:

```
(totem:9336): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9336): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Unknown option pcm.snd_card {.
Unknown option type hw.
Unknown option card 0.
Unknown option }.
Unknown option pcm.dmixer {.
Unknown option type dmix.
Unknown option ipc_key 1024.
Unknown option slave.pcm "snd_card".
Unknown option slave {.
Unknown option period_time 0.
Unknown option period_size 2048.
Unknown option buffer_size 32768.
Unknown option }.
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
Unknown option pcm.dsnooper {.
Unknown option type dsnoop.
Unknown option ipc_key 2048.
Unknown option slave.pcm "snd_card".
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
Unknown option pcm.duplex {.
Unknown option type asym.
Unknown option playback.pcm "dmixer" [esd].
Unknown option capture.pcm "dsnooper".
Unknown option }.
Unknown option pcm.!default {.
Unknown option type asym.
Unknown option playback.pcm "dmixer".
Unknown option capture.pcm "dsnooper".
Unknown option }.
Unknown option pcm.dsp0 {.
Unknown option type plug.
Unknown option slave.pcm "dmixer".
Unknown option }.
Unknown option ctl.dsp0 {.
Unknown option type plug.
Unknown option slave.pcm "snd_card".
Unknown option }.
Unknown option ctl.mixer0 {.
Unknown option type plug.
Unknown option slave.pcm "snd_card".
Unknown option }.
Unknown option pcm.snd_card {.
Unknown option type hw.
Unknown option card 0.
Unknown option }.
Unknown option pcm.dmixer {.
Unknown option type dmix.
Unknown option ipc_key 1024.
Unknown option slave.pcm "snd_card".
Unknown option slave {.
Unknown option period_time 0.
Unknown option period_size 2048.
Unknown option buffer_size 32768.
Unknown option }.
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
Unknown option pcm.dsnooper {.
Unknown option type dsnoop.
Unknown option ipc_key 2048.
Unknown option slave.pcm "snd_card".
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
Unknown option pcm.duplex {.
Unknown option type asym.
Unknown option playback.pcm "dmixer" [esd].
Unknown option capture.pcm "dsnooper".
Unknown option }.
Unknown option pcm.!default {.
Unknown option type asym.
Unknown option playback.pcm "dmixer".
Unknown option capture.pcm "dsnooper".
Unknown option }.
Unknown option pcm.dsp0 {.
Unknown option type plug.
Unknown option slave.pcm "dmixer".
Unknown option }.
Unknown option ctl.dsp0 {.
Unknown option type plug.
Unknown option slave.pcm "snd_card".
Unknown option }.
Unknown option ctl.mixer0 {.
Unknown option type plug.
Unknown option slave.pcm "snd_card".
Unknown option }.
- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
Creating link /home/duane/.kde/socket-Almighty.
can't create mcop directory

```

---

### Post by Almighty on 2006-02-15
OK I have gotten the media players to not hang or crash when I try to play a file. It seems that all my problems were caused when I tried this HOWTO :

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=ALSA+lib+unable+o](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=ALSA+lib+unable+o) pen+slave

So does anyone have any ideas on how undo these changes? I forgot to back up the files before I edited them.

---

### Post by Almighty on 2006-02-16
*UPDATE*

Well I installed the newer version of ALSA and it helped a little more. Now video sometimes plays but there is still no audio. 

Any input?

---

