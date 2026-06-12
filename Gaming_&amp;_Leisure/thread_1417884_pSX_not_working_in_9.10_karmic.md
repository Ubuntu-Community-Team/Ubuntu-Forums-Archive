---
title: "pSX not working in 9.10 karmic"
date: 2010-02-27
forum: Gaming &amp; Leisure
---

### Post by beliyyal on 2010-02-27
Hey guys, I am having a problem, and I was hoping you could help me out. I am trying to run pSX in 9.10 karmic, but am running into some problems. This is what I get in terminal:
> john@john-desktop:~/pSX$ ./pSX -r
Event rescheduling enabled...

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3623): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3623): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0

(pSX:3623): GdkGLExt-WARNING **: Cannot open \xb8\x86}	L.so
Segmentation fault
john@john-desktop:~/pSX$ 


Any ideas guys? Thanks in advance for your help.

---

### Post by beliyyal on 2010-02-28
bump

---

### Post by ShadowTek on 2010-02-28
I've always had to "sudo killall pulseaudio" before running pSX; otherwise, it would crash.

---

### Post by beliyyal on 2010-02-28
> **ShadowTek said:**
> I've always had to "sudo killall pulseaudio" before running pSX; otherwise, it would crash.

Oh ok, thanks. I will try it when I get home. It just sucks cause I run 8.04, and I have so many psx games and I really don't wanna lose my ability to play in the upgrade.

---

### Post by ShadowTek on 2010-02-28
Also, I just remembered that I had to run pSX as root in order for it to work.

---

### Post by beliyyal on 2010-03-02
I got it. sudo killall pulseaudio command makes it work. I also ran it in root as well. So I guess this is solved. Thanks for your help man.

---

### Post by beliyyal on 2010-03-02
[IMG]http://c1.ac-images.myspacecdn.com/images02/149/l_ae568577772344118de8190acd522d84.png[/IMG]

It is working fine.

---

### Post by rafe101 on 2010-03-23
Okay, I couldn't run pSX in Karmic until I changed the device from the default in the pSX.ini file (I was getting seg faults. I know it was the pulseaudio issue). It runs now, but there's no sound.

Before changing the device, I could only run pSX with sudo, but, even then, there was no sound.

Does anyone know how I can fix this?

---

