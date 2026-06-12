---
title: "Please help solve a pSX problem"
date: 2009-03-24
forum: Gaming &amp; Leisure
---

### Post by alejobar on 2009-03-24
Hi there, I just installed pSX in my pc under Ubuntu Intrepid, when I tried to open it it just show the window to choose the language and the it closes. I run it from terminal and I got this error:

(pSX:7280): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
alejo@Ubuntu-desktop:~$ 

could someone please help me to solve the problem?

---

### Post by rick08 on 2009-03-26
It sounds like you do not have the playstation BIOS.  This is usually the problem when pSX closes like that.

---

### Post by benmoran on 2009-03-26
Its a problem with Pulse Audio. You can either kill Pulse Audio and then run pSX, or just use this awesome frontend: [http://psxemulator.proboards54.com/index.cgi?action=display&board=news&thread=1080](http://psxemulator.proboards54.com/index.cgi?action=display&board=news&thread=1080)

---

### Post by dfreer on 2009-03-26
> **benmoran said:**
> Its a problem with Pulse Audio. You can either kill Pulse Audio and then run pSX, or just use this awesome frontend: [http://psxemulator.proboards54.com/index.cgi?action=display&board=news&thread=1080](http://psxemulator.proboards54.com/index.cgi?action=display&board=news&thread=1080)

Does Ultima's Frontend kill pulseaudio now? If not, how does using the frontend (which is indeed awesome) help with this issue?

---

### Post by rick08 on 2009-03-27
Try this:
I also posted with a similar problem.
This script should do it.
[http://ubuntuforums.org/showpost.php?p=6127662&postcount=246](http://ubuntuforums.org/showpost.php?p=6127662&postcount=246)

---

