---
title: "Some applications not displaying their windows after update"
date: 2009-01-05
forum: General Help
---

### Post by CharonM72 on 2009-01-05
After upgrading, many applications like VLC and Konsole, plus others, when run do not pop up any window. However, the programs are listed in the System Monitor and usually hog CPU usage. Note though that by running music files with the vlc command, the music plays out of the vlc program but no window appears. Therefore, the only way to stop the music is by killing vlc.

---

### Post by lavinog on 2009-01-05
> **CharonM72 said:**
> After upgrading, many applications like VLC and Konsole, plus others, when run do not pop up any window. However, the programs are listed in the System Monitor and usually hog CPU usage. Note though that by running music files with the vlc command, the music plays out of the vlc program but no window appears. Therefore, the only way to stop the music is by killing vlc.

what was updated?
have you tried rebooting?

---

### Post by CharonM72 on 2009-01-06
I had left my computer for a long time so I had about 2500 updates when I came back... so probably about everything. Yes, I have rebooted many many times. Also, I tried purging and reinstalling, and I've just purged and am installing from source right now, but I assume it won't work unless I post again stating otherwise.
As for Konsole, I still have no idea.

---

### Post by CharonM72 on 2009-01-06
VLC seems to be running in what it calls "remote control mode" because it can't find an appropriate interface module.

```
[00000353] main interface error: no interface module matched "screensaver,none"
[00000353] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Remote control interface initialized. Type `help' for help.

```

Konsole just eats processor and does nothing.

---

### Post by lavinog on 2009-01-06
which version of ubuntu/kubuntu are you using?

---

