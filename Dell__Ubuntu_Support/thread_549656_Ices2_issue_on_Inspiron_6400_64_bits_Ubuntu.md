---
title: "Ices2 issue on Inspiron 6400 64 bits Ubuntu"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by mgurreta on 2007-09-12
Hi all,
I'm trying to configure Icecast2 and ices2 in my notebook, a Dell Inspiron 6400 with 64 bits ubuntu 7.04, when i start ices i get these messages:
mariano@maquinita:~$ ices2 /usr/share/doc/ices2/examples/ices-alsa.xml 
[2007-09-12  22:27:49] INFO ices-core/main IceS 2.0.1 started...
[2007-09-12  22:27:49] INFO input-alsa/alsa_open_module Opened audio device hw:0,0
[2007-09-12  22:27:49] INFO input-alsa/alsa_open_module using 2 channel(s), 44100 Hz, buffer 371 ms 
[2007-09-12  22:27:49] INFO input-alsa/alsa_open_module Starting metadata update thread
[2007-09-12  22:27:49] INFO signals/signal_usr1_handler Metadata update requested
[2007-09-12  22:27:49] WARN metadata/metadata_thread_signal Failed to open file "test" for metadata update: No such file or directory
[2007-09-12  22:27:49] INFO audio/resample_initialise Initialised resampler for 2 channels, from 44100 Hz to 44100 Hz
[2007-09-12  22:27:49] INFO encode/encode_initialise Encoder initialising in VBR mode: 2 channel(s), 44100 Hz, quality 0.000000
[2007-09-12  22:27:50] INFO stream/ices_instance_stream Connected to server: localhost:8000/radio_mariano.ogg
[2007-09-12  22:27:59] EROR input-alsa/alsa_read snd_pcm_readi failed: Input/output error
[2007-09-12  22:28:00] INFO input/input_loop All instances removed, shutting down...
[2007-09-12  22:28:00] INFO metadata/metadata_thread_signal metadata thread shutting down
[2007-09-12  22:28:00] INFO ices-core/main Shutdown complete

Any help about the error input/alsa line?

---

### Post by mgurreta on 2007-09-17
No ideas?? Any help?? Where I can look for help?

---

### Post by neptho on 2007-09-18
Check your device permissions and ensure you have read/write access to them.  I've never used icecast in a 64 bit environment, but that may have a few issues.  The Intel HDA in my 6400 only supports simplex (record or play) modes, but this probably won't affect you, unless you're trying to use the speakers as a 'monitor'.

---

