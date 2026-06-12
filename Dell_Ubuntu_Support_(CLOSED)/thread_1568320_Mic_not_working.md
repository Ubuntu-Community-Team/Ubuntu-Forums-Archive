---
title: "Mic not working"
date: 2010-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dtrich0 on 2010-09-05
Hello there,
I have a E4300 DELL laptop and I have installed Lubuntu. The only problem that I have is that neither internal mic nor external mic(mic in line) is working. The speaker is working perfectly.
Any help?
Thanks in advance,
Dimos

---

### Post by mikewhatever on 2010-09-06
In 10.04, which, for the lack of info, I assume you have installed, the mic is muted by default. Take a look at the Sound Preferences->Input Tab, and if it is muted, uncheck the mute box.

---

### Post by dtrich0 on 2010-09-06
As Lubuntu has not mixer in System->Preferences I installed xfce4-mixer and I increase the volume of the mic from 0 to +50. Now everything is working perfect.
Thanks for you help:D

---

### Post by dargaud on 2010-09-07
I have a Latitude E6410 and cannot find if there is a mic on it. I've enabled all the inputs in the HDA Intel Kmix. The specs say: "Microphone jack and integrated, noise reducing microphone array with speech enhancement". Nothing in dmesg or other hardware tools tells me if there's a mic.

---

### Post by gabe.saltar on 2011-01-31
Greetings,

      I have the same problem.  I just installed lubuntu 10.10 on my Dell Inspiron 10v.  My sound card is a Realtek ALC272.  My speakers work just fine but the built-in mic or the external microphone are not working.  I installed the gnome-alsamixer I unmuted the microphone and raise the volume of it but did not work. Then I installed the xfce4-mixer package an it refuses to run.  can somebody please help me?  Thanks in advanced.

Gabe

---

### Post by kdford on 2012-12-08
> **gabe.saltar said:**
> Greetings,

      I have the same problem.  I just installed lubuntu 10.10 on my Dell Inspiron 10v.  My sound card is a Realtek ALC272.  My speakers work just fine but the built-in mic or the external microphone are not working.  I installed the gnome-alsamixer I unmuted the microphone and raise the volume of it but did not work. Then I installed the xfce4-mixer package an it refuses to run.  can somebody please help me?  Thanks in advanced.

Gabe

I was having the same problem... Running lubuntu 12.10.  It does have a mixer installed by default, amixer, which is accessed by running amixer or right clicking on the volume panel applet and selecting "Volume Control Settings".  Tab to change input/output, left and right to select 

Just in case it was the actual hardware, I plugged an external mic into the port and it worked.  The test led me to believe that either the mic hardware in my laptop is broken or its driver isn't loading correctly, however the latter doesn't make sense because the same driver would be used for the internal mic or an external mic I would think.

---

