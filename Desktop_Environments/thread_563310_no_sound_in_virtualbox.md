---
title: "no sound in virtualbox"
date: 2007-09-29
forum: Desktop Environments
---

### Post by shayke on 2007-09-29
Hi
I installed virtualbox 1.50 on my Ubuntu 7.04, and it **works great** except that the guest windows xp doesn't give any sound.
I enabled the audio of the xp's settings, and i tried to run all the 3 audio options (alsa, oss, null), non of them helped.
I have external-usb-soundcard which works ok (and from what i understand it doesn't suppose to matter for virtual machine, since it works against alsa, which is ok).

When I run the virtual xp before booting it fives me the message: 

"No audio devices could not be opened. Selecting the NULL audio backend with the consequence that no sound is audible..
   Error ID: HostAudioNotResponding
   Severity: Warning"

Does anybody know how I can fix it?

Thanks

---

### Post by Wayno-san on 2007-10-27
I have the same issue Running Vbox on Ubuntu 7.1 with WinXP as the host, but I have a Soundblaster Audigy 2 card installed.  No sound no matter what driver I chose in the Vbox settings.  WinXP thinks that everything is OK.

Any suggestions?

---

### Post by usp8riot on 2007-10-27
I'm using Kubuntu 7.10 with XP and Audigy 2 with no problem using the ALSA driver. But I've been using an updated driver from ALSA that I compiled.

---

### Post by Wayno-san on 2007-10-28
Did you have the same problem prior to the driver update?  

Thanks for your reply!
-Wayne

---

### Post by usp8riot on 2007-10-28
Wish I could say but I didn't use Virtualbox before the driver update. I've used VB1.4 and 1.5 without problems with sound.

---

### Post by Wayno-san on 2007-10-28
Thanks for the info about the driver update.  Looks like it helped, I now have sound in one VM.

Strangely enough I created 2 Windows XP VMs in VBox and set the driver on both to ALSA... in the first VM I get sound, in the second, I do not.  Looks like everything in both guest clients is set the same sound-wise....  go figure.

---

### Post by phenest on 2007-10-28
I'm using Ubuntu 7.10 as host and every guest gives this error:
```

Some audio devices (PCM_out) could not be opened. Guest applications generating audio output or depending on audio input may hang. Make sure your host audio device is working properly. Check the logfile for error messages of the audio subsystem..


Error ID: 
HostAudioNotResponding
Severity: 
Warning


```

VirtualBox 1.5.2

---

### Post by miltonics on 2007-12-19
I'm haveing the same problem as the parent but with Ubuntu 7.10 and VirtualBox 1.5.2.

Also using 2.6.22-14-rt kernenl.

---

### Post by kman14 on 2008-01-10
i also have no sound in virtualbox.
i have xp on vb 1.5.4
xp doesn't think there's a problem - sound plays on web pages like youtube and facebook (intunes) but itunes and wmp have no sound.
it looks like it's playing music - there's just no sound coming out.
have i missed something simple that i need to turn on?

thanks.

---

### Post by CoryLuLu on 2008-04-16
i am having the same problem

i wonder if i install my driver files for my motherboard if it will make a difference.

---

### Post by gavshouse on 2008-05-08
i have the same problem

anyone got a fix yet ?

---

### Post by itag on 2008-05-11
I changed the host(Gusty) sound system to ALSA and 
the virtualbox audio Host Audio Driver to ALSA, then
both host and gust(XP) can play sound.
I'm not sure if this will work for others.

---

### Post by Ev1L on 2008-06-03
It worked for me,thanks :)

---

### Post by LeeU on 2008-07-10
Thanks, itag! Worked great!

---

