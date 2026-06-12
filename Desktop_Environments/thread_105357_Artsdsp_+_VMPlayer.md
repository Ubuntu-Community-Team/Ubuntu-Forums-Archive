---
title: "Artsdsp + VMPlayer"
date: 2005-12-18
forum: Desktop Environments
---

### Post by ace2005 on 2005-12-18
I'm tryin to get VMware to use arts so i can have sound in the guest and the host but only one will work at any one time.

ace@Linux:~$ artsdsp vmplayer
artsdsp works only for binaries

Can anyone help

---

### Post by mlomker on 2005-12-18
Hmm.  I don't use the player (I have full VMWare), but audio does work for me from both sides.  I have an occassional glitch but it's generally fine.  

The VMWare side plays directly through the /dev/dsp device and doesn't go through the sound system in KDE.  I have the KDE side set to 'autodetect' for the sound subsystem so I'm not entirely sure what it is using.

---

### Post by ace2005 on 2005-12-18
Sound works in VMware and it uses /dev/dsp and i hear it fine but Ubuntu (host) KDE is also set to autodetect won't also play sound, i've set juk to arts sound output and it won't work (i'm guessing that autodetect sets arts too since it a KDE app) so what do i have to do to make juk and vmware play audio at the same time?

---

### Post by mlomker on 2005-12-19
[QUOTE=ace2005]i have to do to make juk and vmware play audio at the same time?[/QUOTE]

They generally can't at the same time (mixing).  I've heard that the esound server can accomplish it, but I haven't looked into it.

You can try adjusting the 'auto-suspend if idle' setting to a lower number (on the Sound page in System Settings).  I've had people say that helps with some of their apps.

---

### Post by ace2005 on 2005-12-19
[QUOTE=mlomker]You can try adjusting the 'auto-suspend if idle' setting to a lower number (on the Sound page in System Settings).  I've had people say that helps with some of their apps.[/QUOTE]


Already done, its set to 1 second. The reason i want them to work together is that i always have music in the background, radio, personal colletion whatever its always on in juk. So when i go into VMplayer i get errors saying /dev/dsp is in use every time an app plays music (and also an error about the stupid floppy drive, i can't even turn that error off, VMware should realise that some people do not have a floppy drive)

I'll have a look at esound server

Thanks

---

### Post by ace2005 on 2005-12-21
Still not working, /dev/dsp is in use error is still there

---

