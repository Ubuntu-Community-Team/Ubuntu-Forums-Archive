---
title: "Games (ppracer, chromium) segfaulting due to missing sequencer"
date: 2005-12-30
forum: Desktop Environments
---

### Post by pinkunicorn on 2005-12-30
I'm trying to install a gaming maching for my kids, using Ubuntu. I started out with Hoary and upgraded that to Breezy. The hardware is pretty old (~2000). I have finally gotten hardware acceleration to work on the 3Dfx Voodoo3 card I'm using.

> $ glxinfo | grep direct
> libGL warning: 3D driver claims to not support visual 0x25
> libGL warning: 3D driver claims to not support visual 0x26
> libGL warning: 3D driver claims to not support visual 0x29
> libGL warning: 3D driver claims to not support visual 0x2a
> libGL warning: 3D driver claims to not support visual 0x2d
> libGL warning: 3D driver claims to not support visual 0x2e
> libGL warning: 3D driver claims to not support visual 0x31
> libGL warning: 3D driver claims to not support visual 0x32
> libGL warning: 3D driver claims to not support visual 0x35
> libGL warning: 3D driver claims to not support visual 0x36
> libGL warning: 3D driver claims to not support visual 0x39
> libGL warning: 3D driver claims to not support visual 0x3a
> libGL warning: 3D driver claims to not support visual 0x3d
> libGL warning: 3D driver claims to not support visual 0x3e
> libGL warning: 3D driver claims to not support visual 0x41
> libGL warning: 3D driver claims to not support visual 0x42
> direct rendering: Yes

As far as I've been able to google, these warnings should be harmless.

I'm now trying to start ppracer, and to begin with it starts up nicely, but as soon as I try to press a key to leave the first screen it crashes with 

> open /dev/sequencer: No such file or directory
> Fatal signal: Segmentation Fault (SDL Parachute Deployed)

On the first screen, I get the falling snow and the music in the background and everything seems to work fine, but nothing further works.

I've also tried chromium which dies with the same message, except that it doesn't do anything at all before dying.

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=pinkunicorn]I'm trying to install a gaming maching for my kids, using Ubuntu. I started out with Hoary and upgraded that to Breezy. The hardware is pretty old (~2000). I have finally gotten hardware acceleration to work on the 3Dfx Voodoo3 card I'm using.

> $ glxinfo | grep direct
> libGL warning: 3D driver claims to not support visual 0x25
> libGL warning: 3D driver claims to not support visual 0x26
> libGL warning: 3D driver claims to not support visual 0x29
> libGL warning: 3D driver claims to not support visual 0x2a
> libGL warning: 3D driver claims to not support visual 0x2d
> libGL warning: 3D driver claims to not support visual 0x2e
> libGL warning: 3D driver claims to not support visual 0x31
> libGL warning: 3D driver claims to not support visual 0x32
> libGL warning: 3D driver claims to not support visual 0x35
> libGL warning: 3D driver claims to not support visual 0x36
> libGL warning: 3D driver claims to not support visual 0x39
> libGL warning: 3D driver claims to not support visual 0x3a
> libGL warning: 3D driver claims to not support visual 0x3d
> libGL warning: 3D driver claims to not support visual 0x3e
> libGL warning: 3D driver claims to not support visual 0x41
> libGL warning: 3D driver claims to not support visual 0x42
> direct rendering: Yes

As far as I've been able to google, these warnings should be harmless.

I'm now trying to start ppracer, and to begin with it starts up nicely, but as soon as I try to press a key to leave the first screen it crashes with 

> open /dev/sequencer: No such file or directory
> Fatal signal: Segmentation Fault (SDL Parachute Deployed)

On the first screen, I get the falling snow and the music in the background and everything seems to work fine, but nothing further works.

I've also tried chromium which dies with the same message, except that it doesn't do anything at all before dying.[/QUOTE]

Does the file /dev/sequencer actually exist?  If you open a terminal and type:
```

$ ls -l /dev/sequencer

```
Does it produce any output?

If not, your sound driver might not be creating a sequencer device node.

Let us know the results and we will proceed from there.

---

### Post by pinkunicorn on 2005-12-30
[QUOTE=cwaldbieser]Does the file /dev/sequencer actually exist?  If you open a terminal and type:
```

$ ls -l /dev/sequencer

```
Does it produce any output?

If not, your sound driver might not be creating a sequencer device node.

Let us know the results and we will proceed from there.[/QUOTE]

No, there is no /dev/sequencer file. 

My sound card presents itself as "VIA Technologies
AC97 Audio Controller" (onboard the motherboard).

I have the following modules loaded:

```

snd_ens1370            17632  1
gameport               14472  1 snd_ens1370
snd_rawmidi            22816  1 snd_ens1370
snd_seq_device          8204  1 snd_rawmidi
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_ens1370,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7808  1 snd_ens1370
snd                    48644  10 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore               9184  1 snd

```

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=pinkunicorn]No, there is no /dev/sequencer file. 

My sound card presents itself as "VIA Technologies
AC97 Audio Controller" (onboard the motherboard).

I have the following modules loaded:

```

snd_ens1370            17632  1
gameport               14472  1 snd_ens1370
snd_rawmidi            22816  1 snd_ens1370
snd_seq_device          8204  1 snd_rawmidi
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_ens1370,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_ens1370,snd_pcm
snd_ak4531_codec        7808  1 snd_ens1370
snd                    48644  10 snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore               9184  1 snd

```[/QUOTE]

Try this:
```

$ sudo modprobe snd_mixer_oss

```
That seems to be the relevant module when I list my loaded modules.  If that works, it should create the device for you.

---

### Post by pinkunicorn on 2005-12-31
[QUOTE=cwaldbieser]Try this:
```

$ sudo modprobe snd_mixer_oss

```
That seems to be the relevant module when I list my loaded modules.  If that works, it should create the device for you.[/QUOTE]

Just loading it as above and then starting ppracer makes no difference. Or do you mean that I need to put that in somewhere to make it happen automatically and then reboot? Would rc.local be right, or is there a better place?

---

### Post by pinkunicorn on 2005-12-31
[QUOTE=pinkunicorn]Just loading it as above and then starting ppracer makes no difference. Or do you mean that I need to put that in somewhere to make it happen automatically and then reboot? Would rc.local be right, or is there a better place?[/QUOTE]

I added snd_mixer_oss to /etc/modules and rebooted, and that doesn't help either. I still get no /dev/sequencer.  :confused:

---

### Post by SuperBOB on 2006-02-22
sudo modprobe snd-seq

That should do it

---

