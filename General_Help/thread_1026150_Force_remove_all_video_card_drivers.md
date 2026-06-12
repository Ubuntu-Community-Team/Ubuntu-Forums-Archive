---
title: "Force remove all video card drivers?"
date: 2008-12-30
forum: General Help
---

### Post by GXice on 2008-12-30
I think my system is a complete mess. I've been trying for several days to make my integrated graphics (GeForce 6100/nForce 605) to work properly, but things are wrong. Every bootup I get the same "Running in Low-Graphics mode" dialog box, the resolution doesnt change higher than 800x600, and refresh rate is 61Hz :S

I've tried using Envy and manualy downloading the binaries, but nothing worked.

Can someone help me remove all traces of video drivers and how to start from scratch again? I'm desperate to see some Compiz functionality and sick of not being able to use Visual Effects. :(

Thanks! Running Hardy, btw.

---

### Post by hansdown on 2008-12-30
Hi GXice.
To remove the drivers, go to system> administration> synaptic package manager. Search for envy and click on your driver. Choose complete removal.
For installing, follow this...  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by GXice on 2008-12-30
> **hansdown said:**
> Hi GXice.
To remove the drivers, go to system> administration> synaptic package manager. Search for envy and click on your driver. Choose complete removal.
For installing, follow this...  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thanks Hansdown for the prompt reply.

The link you gave me was one of my initial attempts to install video drivers. I followed those steps, installed nvidia-glx (which is the 96.43.05 driver) and after a reboot, it's like nothing happened. No drivers were in effect and nothing changed.

Is it possible there's some corruption with my xorg.conf file? Or any other possibilities?

---

### Post by hansdown on 2008-12-30
Hi GXice.
I don't know if mixing (GeForce 6100/nForce 605) cards may or may not be the problem, but have you tried the other nvidia drivers?

---

### Post by GXice on 2008-12-31
> **hansdown said:**
> Hi GXice.
I don't know if mixing (GeForce 6100/nForce 605) cards may or may not be the problem, but have you tried the other nvidia drivers?

Sorry, my mistake in the first post. It's not nForce 605, its 405.

The nForce 405 refers to the nForce4 based southbridge which is used with GeForce 6100 northbridge to form the integrated graphics chipset.

---

### Post by hansdown on 2009-01-01
Hi GXice.
You seem to be correct about the xorg.conf file.
Please have a look.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509211](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=509211)

---

