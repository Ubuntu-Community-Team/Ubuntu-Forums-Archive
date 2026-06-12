---
title: "Sound stuck stuttering......"
date: 2009-06-07
forum: General Help
---

### Post by stoneage on 2009-06-07
How can I safely restart my sound system. I have other applications running and am unwilling to restart or log out.

I had sound running in Firefox and it started stuttering. Shutting down Firefox makes no difference.

I tried:-
organic@organic-desktop:~/blender$ killall pulseaudio
organic@organic-desktop:~/blender$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
organic@organic-desktop:~/blender$ 


Help....

Ubuntu 8.10 64 bit


EDIT - Found it, thanks...

I killed these:-
pulseaudi  6328     organic  mem       CHR             116,11               13045 /dev/snd/pcmC0D0p
pulseaudi  6328     organic   52u      CHR             116,11               13045 /dev/snd/pcmC0D0p

---

