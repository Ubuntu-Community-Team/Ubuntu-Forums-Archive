---
title: "No sound in ubuntu"
date: 2005-08-11
forum: Desktop Environments
---

### Post by Vinger on 2005-08-11
Hello

I have no sound at all in ubuntu.
I have had Windows, SUSE and Mandrake (Mandriva) on the same machine, but for some reasons, i like Ubuntu the most, except for the silence.

I tried to follow the ubuntuguide ([http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)  and the codecs) but no sound.

Then i tried to adjust some parameters of the multimediasetting (ESD, ALSA, ...) and my sound settings (Sound server, ...)

Nothing worked.

Can my sound be muted somewhere? Can i have set wrong parameters?
What can i do???

---

### Post by Matriz on 2005-08-11
doublecheck your mixer that there is no mute on....i dont know anything else sry  :(

---

### Post by Lord Illidan on 2005-08-11
Try typing ```
lspci
```  in a terminal.. and give us the output!

---

### Post by Vinger on 2005-08-11
tx:

i checked the mixer, and nothing is muted. (i think)
When i mute my PCM, i hear a silent 'clic', but the rest gives no sound.

Here is the answer of the command "lspci"

> 
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP


tx for the quick responces!

---

### Post by Vinger on 2005-08-15
I checked the mixer, and nothings is muted (i think)
I installed KUbuntu to try if anything changed, but everything rest silent.

I checked the (in dutch it's "volumemeter") level of sound and this gives me that there is no sound. 

So i think there must be something muted, but i don't find where/what it can be.

anyone an idea?

---

### Post by Vinger on 2005-08-15
my soundcard is:
SIS 7012 with chip: CMI9761 

in the device manager, he recognize the sis card.
In the hardwaresupport, the say that the card works fine, but with another chip.

Anyone an idea with this?

---

### Post by Vinger on 2005-08-16
I have also an old sound-card. 
Maybe i can add it and see if that is a solution?

Does that give problems? working with two soundcards... 
My computer must also work in windows...

---

### Post by Vinger on 2005-08-20
Ok, i reinstalled UBUNTU because i didn't know anymore what i did...

I folowed the guide (ubuntuguide/configure sound properly)

Then i tried the forum [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)

I have systembeeps, but that's all...
I can't play music, i hear no sound from games, ...

The only thing i have read was to upgrade to breezy. Is that safe allready?

where can i search further? 
Anybody ideas?

---

### Post by pekko on 2005-08-21
Same soundcard and same problem here. I installed Ubuntu yesterday. Please let me know if you could solve the problem.

---

### Post by lotech on 2005-08-21
But how about on KDE ?

---

### Post by pekko on 2005-08-21
I just found the solution from the forum:

[http://www.ubuntuforums.org/showthread.php?t=47130](http://www.ubuntuforums.org/showthread.php?t=47130)

That did the trick for me. \\:D/

---

### Post by Vinger on 2005-08-21
I tried KDE (Kubuntu), but the problem remained...

---

### Post by Vinger on 2005-08-22
OK...

Tx!

With that trick, i hear sound again!

tx!

---

