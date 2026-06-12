---
title: "Audio Modules"
date: 2012-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ira miles on 2012-05-29
Hi all, 
I am having a second problem with the installation of Ubuntu on a B120: I have no audio. I have almost no Linux experience but have used the forums to do the following:

ira@ira-ME051:~$ sudo aplay -l
[sudo] password for ira: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So, I know that there is a sound card in there, so I run this:

ira@ira-ME051:~$ find /lib/modules/'uname -r' | grep snd
find: `/lib/modules/uname -r': No such file or directory

Can I assume that there are no modules? Well I did. Soooo...

ira@ira-ME051:~$ sudo apt-get install linux-restricted-modules- 'uname -r' linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules
E: Unable to locate package uname -r

So, I could use a little love here. As I said my coding stinks, so if I could download a particular audio module then I would like to do that via the software center (wysiwyg is always safer with me). If so can you reccommend a module to me? Otherwise, I need some terminal training here!

Thanks in advance!

---

### Post by mikewhatever on 2012-05-30
Hi, the commands you've used tell nothing about the modules. They are incorrect (exept the first one), so let's try and see if we can do any better.

First, make sure the sound is not muted. That may sound stupid, but anyway, run alsamixer, and make sure the master, speakers and PCM channels are up. It will ook something like in the picture below.

To check what module is used, run the following:
```
lspci -nnk | grep -iA2 audio
```

If the output shows the driver, then it's loaded. Here's mine as an example:
```
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 30)
	Subsystem: Avance Logic Inc. Device [4005:4730]
	**Kernel driver in use: snd_via82xx**

```

The Linux Restricted Modules packages no longer exist.

PS: For the piece of mind, the following will show available audio modules, lots of them, to be sure. The signes around uname -r are backticks, not the single quotes.
```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by ira miles on 2012-05-31
All you say is true. 
kernel driver in use: snd_hda_intel
Any thoughts on a lack of sound?

---

### Post by ira miles on 2012-05-31
NOt what I did but sound now works. However, under audio settings, the output volumn at the bottom of the window is grayed out. Is this an issue?

---

