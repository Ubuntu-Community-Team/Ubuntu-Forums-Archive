---
title: "ubuntu is running in low graphics mode"
date: 2009-09-11
forum: Desktop Environments
---

### Post by ankur9118 on 2009-09-11
after " dpkg-reconfigure -a " my ubuntu box starts giving the message 
" ubuntu is running in low graphics mode "
" GARTinit: unable to open /dev/agpgart "
" videoRAM set too low "
etc etc...
and after that message it hangs...

every thing is working in single user mode...i have tried " dpkg-reconfigure xserver-xorg " it does reconfigure it...but the problem still persist.

when i " dpkg-reconfigure gdm " it says :-
invoke-rc.d: initscript gdm, action "reload" failed

now from web serarch i added the two module :-
# modeprob agpgart
# modeprob intel-agp
after this when i " /etc/init.d/gdm start " it goes to the login screen but in that the keyboard and mouse do not work...

can anyone tell what is the cause of the problem...

---

### Post by Spongeloaf on 2009-09-12
I'm not an expert, but " videoRAM set too low " catches my attention. How much ram do you have? What type of GPU do you have? (ati? nvidia?) Is the graphics card integrated? If so, check the amount of system ram dedicated to graphics from the bios.

---

### Post by ankur9118 on 2009-09-14
> **Spongeloaf said:**
> I'm not an expert, but " videoRAM set too low " catches my attention. How much ram do you have? What type of GPU do you have? (ati? nvidia?) Is the graphics card integrated? If so, check the amount of system ram dedicated to graphics from the bios.

i have 1GB ram, 2GB swap area, integrated graphics card, all are well supported by ubuntu...and there is no problem in BIOS setting...

from last two days of experience it came into my notice that i have in :-
# lsmod
1915 drm appgart input_polldev video output lp parport r8169 mii floppy fbcon tileblit font bitblit softcursor

only...(runlevel 2)

on comparison with newly installed system the following modules are missing :-

{ binfmt_misc bridge stp bnep  snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iTCO_wdt ppdev iTCO_vendor_support snd_timer snd_seq_device psmouse serio_raw pcspkr intel_agp parport_pc  snd  soundcore snd_page_alloc }

now can anyone figure out what could be the reason for this...
when i # modeprobe all these modules the problem resolves. but why these modules are not loading automaticly ...

---

### Post by ankur9118 on 2009-09-23
somebody please explain why modules are not loading automatically...and how to fix it...?

there are many active servers on that i dont want to reinstall...:confused:

---

