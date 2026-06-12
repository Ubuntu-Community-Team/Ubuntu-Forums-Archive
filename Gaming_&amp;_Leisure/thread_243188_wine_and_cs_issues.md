---
title: "wine and cs issues"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by Southeast First on 2006-08-24
I've been trying to play counter-strike cz but i have no sound. from start to finish:

to load steam:
matt@matt-desktop:~$ cd /home/matt/.wine/drive_c/Program\ Files/Steam
[email]matt@matt-desktop:~/.wine[/email]/drive_c/Program Files/Steam$ WINEDEBUG="fixme-all" wine Steam
err:systray:delete_icon invalid tray icon ID specified: 1d

steam is loaded.

after loading coundition zero:
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
No ctx->FragmentProgram._Current!!
No ctx->FragmentProgram._Current!!
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.

I load up winecfg:
matt@matt-desktop:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Any ideas? In winecfg OSS is checked, Acceleration is set at Emulation, Default sample rate is at 22050, Default bits per sample is at 16 and driver emulation is checked (all after playing around with different combinations of settings.)

---

### Post by Southeast First on 2006-08-25
bump

---

### Post by Southeast First on 2006-08-25
anyone?

---

### Post by Southeast First on 2006-08-27
...

---

### Post by maka on 2006-08-28
> **Southeast First said:**
> ...

try closing all other programs including browsers, music/video players, etc if they are open.  then try again.  also try a clean reboot.

---

### Post by firezip on 2006-08-28
Try this command in the terminal

"killall esd"

That stops all sound processes.

---

