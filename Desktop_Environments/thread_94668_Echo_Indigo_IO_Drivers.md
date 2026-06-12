---
title: "Echo Indigo I/O Drivers?"
date: 2005-11-24
forum: Desktop Environments
---

### Post by pammiwhammi on 2005-11-24
I'm thinking of installing Linux on my laptop, but I have a soundcard that I don't know if its supported. Its an Echo Indigo i/o pci card. If there are drivers, where can I find them, how do you install them, and how do I tell my programs to use this card? (for example, Audacity?)

Thanks in advance

pam

---

### Post by ametade on 2005-11-24
Hi,

I think your card is supported:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Echo_Corporation#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Echo_Corporation#matrix)

Details on how to install the driver:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Indigo+IO.&chip=Motorola+56361&module=indigoio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Indigo+IO.&chip=Motorola+56361&module=indigoio)

---

### Post by jwolf on 2005-11-24
I have an Echo Indigo (not the IO) and there are definately drivers available. You will have to compile them from source (not as scary as it sounds) in order to use them. It took me a little while, but I eventually figured out how to get everything working  right (all of the virtual channels are a pain to maintain!), but all is well now.

---

### Post by cgdef on 2007-07-11
Yeah there are drivers alright. You can even install the packages from ubuntu studio which means no compilation. However you will have a boat load of problems using 2 cards. Ubuntu has absolutelly no configuration tool for alsa ( which is insane considering the usability claims that they have ) and you will have to configure some things by hand. It depends on what you would like to do. Applications like rythmbox and totem you can get easily to work by setting up the alsa default card but then things like tvtime are not so trivial. Also it seems that recompiling alsa breaks ubunty. And this is actually one of the few distributions that does that. A lot of things like card initialization to the same device number are done automaticaly but there is still a lot of work to be done before ubunty has an easy to use multimedia control system. The sad thing is that as bad as windows is it is actually 1000 times easier to control the sound system.

---

