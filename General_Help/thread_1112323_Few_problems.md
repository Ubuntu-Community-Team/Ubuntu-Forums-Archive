---
title: "Few problems"
date: 2009-03-31
forum: General Help
---

### Post by clone11 on 2009-03-31
I can't seem to figure out how to install the audio drivers. In windows I use the RealTEK hd audio driver. Well I looked up the linux version of the driver, it says to install manulay for ubuntu. I get to this step "Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution". I"m not sure which one to edit also it ask for the number of the audio device I ran lspci -v and below is the output. There is no ACLxxxx any ideas?
```
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: Unknown device 0175:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping
```
Specs
E8400 Intel
64bit linux
2Gb ram
Evga nforce 780I

---

### Post by clone11 on 2009-03-31
Any suggestions?

---

### Post by 123456789123456789123456 on 2009-03-31
check nvidia for a manufacture driver comaptable with ubuntu.
If not, see if there is a third party, comunity open source driver that is 100% compatable with nvidia realtek audo devices.

---

### Post by clone11 on 2009-03-31
I have noidea what to use I checked nvidias site for Nforce drivers and they are only windows

---

### Post by clone11 on 2009-03-31
Bump on vista the drivers I use is realtekHD but it says i need to manulay install them on ubuntu and i get to a point to where i need to input the ACL number but I have noidea what mine is.

---

### Post by clone11 on 2009-03-31
bump

---

### Post by hyper_ch on 2009-03-31
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by clone11 on 2009-03-31
Sorry, I fixed it up a bit and updated with the code tags thanks for the advice.

---

### Post by clone11 on 2009-03-31
Also on one of the steps it says "Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)" How do I do this, Or is it already enabled?

---

### Post by clone11 on 2009-03-31
bump

---

### Post by clone11 on 2009-04-01
I figured it out it's ACL883, But i'm having more problems on the installation instructions for the realke it says to run sudo make, when I do it outputs this

```
chris@chris-desktop:~/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11$ sudo make
make dep
make[1]: Entering directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make[2]: Entering directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
copying file alsa-kernel/core/info.c
/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make: *** [include/sndversions.h] Error 2

```

---

