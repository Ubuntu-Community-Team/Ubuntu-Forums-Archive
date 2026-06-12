---
title: "sound problem"
date: 2005-09-03
forum: Desktop Environments
---

### Post by one_ro on 2005-09-03
Hi guys,

I have a big problem... don't ask me how I did it, but I accidentally erased my [FONT=Arial Black]/dev/dsp[/FONT] file while I was trying to get sound working. I have a Toshiba laptop with an integrated Intel audio card which kept not working no matter what I did.
I compiled the latest alsa drivers (according to a How-to) but after restarting I got the following error message:
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
...
and after that managed to erase [FONT=Arial Black]/dev/dsp[/FONT].

Can you please advice?

---

### Post by Takis on 2005-09-03
Not so sure if this will work, but try rebooting.

---

### Post by gnutux on 2005-09-03
I don't think that would work, you need to reinstall the kernel.

gnutux

---

### Post by Takis on 2005-09-04
[QUOTE=gnutux]I don't think that would work, you need to reinstall the kernel.

gnutux[/QUOTE]
But the kernel is just something loaded into memory on boot (from a single file). In any case, try rebooting before reinstalling the kernel.

---

### Post by mlomker on 2005-09-04
mknod /dev/dsp c 14 3

That will restore the entry but I don't know if that's your only problem at this point.

---

### Post by one_ro on 2005-09-04
I tried rebooting, with no avail. After reinstalling the latest alsa drivers, the situation got out of control. So far I tried this:
[COLOR=Red]sudo /usr/src/alsa-driver-1.0.9/snddevices[/COLOR]
(which restored my **[FONT=Arial]/dev/snd[/FONT]** folder) and after that
[COLOR=Red]sudo /dev/MAKEDEV audio[/COLOR]
(which restored my **[FONT=Arial]/dev/dsp[/FONT]** file).

The sound still doesn't work though; when I tried to change the device under Control Center/ ... / Sound System, it says it's restarting the sound system and after that I get the same error:

Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

But **it is** there, as [COLOR=Red]ls /dev/dsp[/COLOR] shows
[COLOR=Teal]/dev/dsp[/COLOR]

In this stage, rebooting **[COLOR=Blue]**deletes**[/COLOR]** the **[FONT=Arial]/dev/snd[/FONT]** folder and the **[FONT=Arial]/dev/dsp[/FONT]** file!!
(BTW, it would be nice if one could restart the sound system w/o rebooting, something like [COLOR=Red]ifdown[/COLOR] and [COLOR=Red]ifup[/COLOR] do  with the ethernet card)

w/ or w/o them, I cannot run neither [COLOR=Red]alsaconf[/COLOR], which is giving:
sudo: alsaconf: command not found
nor [COLOR=Red]alsamixer[/COLOR], which gives:
alsamixer: function snd_ctl_open failed for default: No such file or directory

 ](*,)   ](*,)   ](*,)   ](*,)   ](*,)   ](*,)  ...

Had I not reinstalled the alsa driver, I think the solution was this one:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=213936](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=213936)

Basically, I also have a modem on my motherboard which got focus on boot time before the sound card. This is why it kept giving the error message that /dev/dsp was busy (because alsa cannot play on multiple channels at once). Digging further about this, I found a thread on a Romanian list which offers a solution (a script that makes alsa run multiple channels, full-duplex, both input and output).

But before reaching that stage, what can I do with alsaconf?? Or alsamixer?? And why-oh-why do those files dissapear after reboot??

Hope to hear from you soon guys, 'cause I'm getting desperate... (I feel that we could solve this, though, and write a proper How-To in the end).
Cheers,
Adrian

---

### Post by one_ro on 2005-09-06
Problem solved :)
[COLOR=Red]apt-get update[/COLOR]
for the newest KDE and everything is back to normal now.
Cheers!

---

