---
title: "Problems with pSX 1.13"
date: 2009-10-03
forum: Gaming &amp; Leisure
---

### Post by Vorsplummi on 2009-10-03
Hi!
I have the following problem with pSX 1.13 playstation emulator: 
When I try to run pSX I get a error message:
```
mikko@mikko-laptop:~$ pSX

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Virheellinen argumentti'
pad=0
/usr/bin/pSX: line 4: 10599 Muistialueen ylitys     ./pSX
``` 
 I really don't have a clue what to do about it, so can anyone help me out?

---

### Post by Saghaulor on 2009-10-09
Please browse the forums for an answer to your question before starting a new thread. Your answer was already posted.

Your problem.
[http://ubuntuforums.org/showpost.php?p=7723179&postcount=6]("http://ubuntuforums.org/showpost.php?p=7723179&postcount=6")

And what I would assume is the answer.
[http://ubuntuforums.org/showpost.php?p=7723360&postcount=7]("http://ubuntuforums.org/showpost.php?p=7723360&postcount=7")

---

### Post by Vorsplummi on 2009-10-18
Thanks for that. I thought I viewed all psx threads but apparently no.
I let you know if I get psx working

---

### Post by Vorsplummi on 2009-10-18
Seems to be quite complicated problem. Killing pulseaudio didn't do the thing

---

