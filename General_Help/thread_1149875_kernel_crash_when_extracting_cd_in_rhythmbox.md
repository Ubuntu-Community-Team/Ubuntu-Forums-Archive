---
title: "kernel crash when extracting cd in rhythmbox"
date: 2009-05-05
forum: General Help
---

### Post by ciaovos on 2009-05-05
I keep getting a grey screen freeze up when extracting cd's in rhythmbox.  I assume this is a kernel crash.  Recently I installed 9.04 after a d-ban boot and nuke.  It has a 2.6.28-11-generic kernel. 

```
~$ tail /var/log/messages
May  5 12:47:24 ciaovos kernel: [12622.832719] rhythmbox[29888]: segfault at 736e6157 ip b70fb31f sp bfaa21b0 error 4 in libgobject-2.0.so.0.2000.1[b70d2000+3c000]
May  5 14:35:27 ciaovos pulseaudio[13528]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May  5 14:35:27 ciaovos pulseaudio[13532]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May  5 14:35:27 ciaovos pulseaudio[13536]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
May  5 14:35:27 ciaovos pulseaudio[13542]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.

```Can anyone help?

---

### Post by ciaovos on 2009-05-12
Here is another output:

```
~$ tail /var/log/messages
May 19 09:19:04 ciaovos pulseaudio[3426]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 19 09:19:04 ciaovos pulseaudio[3426]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
```

---

