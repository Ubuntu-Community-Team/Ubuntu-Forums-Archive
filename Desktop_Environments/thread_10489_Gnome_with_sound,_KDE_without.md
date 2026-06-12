---
title: "Gnome with sound, KDE without"
date: 2005-01-08
forum: Desktop Environments
---

### Post by Molot on 2005-01-08
I have small problem. I was using Gnome, and I was able to hear any sound that should be heared. Now i switched to KDE (uninstaling Gnome)... And I can't play any sounds... I can push sounds from microphone to headphones, I can adjust volume of it (on the microphone and headphones side separately - both in and out works somehow). But GLTron, Kaboodle and other programs don't play anything. Does anyone know if there is any quick-fix for it?

I'm using Ubuntu 4.10

---

### Post by varunus on 2005-01-08
Is the KDE sound server on?  Go to the control center, and the sound server module, and make sure its on and set to use ALSA or ESD (whichever you prefer for output).

---

### Post by tiiim on 2005-01-08
[QUOTE=varunus]Is the KDE sound server on?  Go to the control center, and the sound server module, and make sure its on and set to use ALSA or ESD (whichever you prefer for output).[/QUOTE]
 if not have you dl the right modules? if not its time for apt-get

---

### Post by iLemon on 2008-01-14
I am having this same problem.  I am running Ubuntu 7.10.  I used the physcocats directions to install KDE.  I have a Intel Q695 Motherboard with onboard SigmaTel HD Audio.  In Gnome, I am using ALSA and it works fine.  I opened System Settings and then Sound System.  In the Hardware tab, the "Select the audo device:" is set to Autodetect by default.  I tried changing the audio option to Advanced Linux Sound Architecture.  The sound system restarted, but I still don't have any sound.  My volume is set at 100%.

:confused:

---

### Post by anachreon_ on 2008-01-14
I'm a fairly long-term Kubuntu user, but honestly the implementation of sound in KDE 3.5 leaves a bit to be desired.  My impression is that it has something to do with using aRts as the sound server.  I have limited knowledge of this, but I believe KDE 4.0 discontinues use of aRts and uses Phonon as the sound back-end, which may solve a lot of problems.  Maybe someone with some more knowledge on this can clarify a bit further?  Sorry this doesn't help anyone in immediate need.

---

