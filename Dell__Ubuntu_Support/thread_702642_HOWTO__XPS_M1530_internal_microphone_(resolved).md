---
title: "HOWTO:  XPS M1530 internal microphone (resolved)"
date: 2008-02-20
forum: Dell  Ubuntu Support
---

### Post by LukasD on 2008-02-20
[SIZE="4"]_Problem:_[/SIZE]

Your internal microphone isn't working on your sleek new Dell XPS M1530.


[SIZE="4"]_Solution:_[/SIZE]

These instructions are for Ubuntu 7.10 (Gusty) using the 2.6.22-14-generic kernel.

1. **Do not install** Dell's custom linux-backports-modules (l-b-m) package.

2. Download build 1.0.16 from the Alsa Project (three files):
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2")
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2")
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2")

3. Install the required tools and kernel headers:
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-2.6.22-14-generic
```

4. Setup installation directories:
```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /home/user/downloads/alsa-* /usr/src/alsa
sudo tar xjf alsa-driver-1.0.16.tar.bz2
sudo tar xjf alsa-lib-1.0.16.tar.bz2
sudo tar xjf alsa-utils-1.0.16.tar.bz2
```

5. Compile and install alsa-driver:
```
cd alsa-driver-1.0.16
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

6. Compile and install alsa-lib:
```
cd ../alsa-lib-1.0.16
sudo ./configure
sudo make
sudo make install
```

7. Compile and install alsa-utils:
```
cd ../alsa-utils-1.0.16
sudo ./configure
sudo make
sudo make install
```

8. Reboot

9. Go into your volume control (Alsa mixer) -> Edit -> Preferences

10. Add tracks Surround, Digital and Digital Input Source.  Click close.

11. Increase the Master and Surround levels in the Playback tab.  Increase the Digital level under the Recording tab.  Select Digital Mic 1 for the Digital Input Source under the Options tab.  NOTE: Make sure nothing is muted under the levels.

12. If you are installing Skype be sure to install the 2.0 beta for Linux.  You can find it here:
[http://www.skype.com/download/skype/linux/beta/]("http://www.skype.com/download/skype/linux/beta/")

Have fun!
Lukas

:popcorn:

---

### Post by LK_gandalf_ on 2008-02-21
is it the same on the 64bit version?

---

### Post by bLv on 2008-02-24
Hi
I've tried your tutorial and after the reboot my soundcard doesn't work at all. When I click on the tray I have : (that's a translation from the french) The sound controller does'nt find a periferic to controll. This means that you don't have the good "greffons GSTreamer" or you don't have a soundcard configured.

How can i reverse the operation?

---

### Post by atulmathur on 2008-02-26
I have similar problem with this solution ... This doesnt work ...

The big problem is how do we reverse this?

Regards,

Atul Mathur

---

### Post by dragonx on 2008-02-28
the solution in this url
[http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/]("http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/")

---

### Post by var on 2008-03-24
> **LukasD said:**
> [SIZE="4"]_Problem:_[/SIZE]
5. Compile and install alsa-driver:
```
cd alsa-driver-1.0.16
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

when I try to do this I get this error:

```
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/i2c/l3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/i2c/l3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/i2c/other'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa/wavefront'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/oxygen'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/oxygen'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/at91'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/at91'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/fsl'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/fsl'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc/sh'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/usb/caiaq'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16/pcmcia'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.16  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16/acore/hwdep.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16/acore/memory_wrapper.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16/acore/memalloc.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16/acore/sgbuf.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.o
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:2996: warning: ‘struct vm_fault’ declared inside parameter list
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:2996: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: In function ‘snd_pcm_mmap_status_fault’:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3004: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3005: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: At top level:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3011: error: unknown field ‘fault’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3011: warning: initialization from incompatible pointer type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3036: warning: ‘struct vm_fault’ declared inside parameter list
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: In function ‘snd_pcm_mmap_control_fault’:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3044: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3045: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: At top level:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3051: error: unknown field ‘fault’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3051: warning: initialization from incompatible pointer type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3091: warning: ‘struct vm_fault’ declared inside parameter list
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: In function ‘snd_pcm_mmap_data_fault’:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3103: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3116: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c: At top level:
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3124: error: unknown field ‘fault’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.c:3124: warning: initialization from incompatible pointer type
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
```

under Gutsy. how can I fix this?
thanks a lot. :)

greetings.

---

### Post by LukasD on 2008-03-25
Hello all,

Sorry I haven't had a chance to follow up sooner.  I'm not sure why some of you are experiencing problems with my instructions.  I did re-check to ensure I didn't leave anything out.  Still works perfectly (at least for me).

Lukas

---

### Post by var on 2008-03-26
> **LukasD said:**
> Hello all,

Sorry I haven't had a chance to follow up sooner.  I'm not sure why some of you are experiencing problems with my instructions.  I did re-check to ensure I didn't leave anything out.  Still works perfectly (at least for me).

Lukas

ok, I've installed them all. but microphone's volume is still too low (even if all recording volumes are set at the highest level and when I try to record something with the Gnome recorder, I hear my voice very very far).

here my alsamixer screens:

[http://img174.imageshack.us/my.php?image=alsa1sa2.jpg]("http://img174.imageshack.us/my.php?image=alsa1sa2.jpg")
[http://img182.imageshack.us/my.php?image=alsa2tv0.jpg]("http://img182.imageshack.us/my.php?image=alsa2tv0.jpg")
[http://img174.imageshack.us/my.php?image=alsa3zl5.jpg]("http://img174.imageshack.us/my.php?image=alsa3zl5.jpg")

how can I fix this?
thanks. :)

greetings.

---

### Post by LK_gandalf_ on 2008-03-26
I have kubuntu 8.04, and the microphone still doesn't work. Any ideas?

---

### Post by MonkeyZiggurat on 2008-03-29
I have instaled Dell's custom backports (which didn't work) and want to give this a try. What shall I replace them with before I start all this malarky? I didn't check to see what I had installed before downloading dell's files like a muppet, so I don't know what to rollback to or where to find it.

---

### Post by Elderlygent on 2008-03-31
WARNING WARNING WARNING: i incautiously installed the latest ALSA as recommended, only to find that in the process I have zapped my sound. Tried re-installing gstreamer, no joy. Alsa Mixer has morphed into something called gamix, which has no controls.

Any ideas, short of a complete Gutsy reinstall??

---

### Post by sdennie on 2008-03-31
Are you sure it's necessary to install the latest alsa-lib and alsa-util packages?  I would imagine the hardware on an XPS m1530 is similar to the m1330 I'm using and all I needed to do was install the alsa-drivers package and then use instructions similar to what you've listed for the alsa mixer config part.

Also, to uninstall, you could try going into each of the directories you typed "make install" in and type "make uninstall".  Then, I believe something like this should restore als-util and alsa-lib to it's original state:

```

sudo apt-get --reinstall install alsa-utils libasound2

```

I think something like this should re-install the old alsa kernel modules but, it looks like no one has had much luck with getting the mic to work without using at the very least these drivers so, it may be overkill.

```

sudo apt-get --reinstall install linux-image-`uname -r`

```

I don't have an Ubuntu kernel installed so, that last command may or may not work.

---

### Post by LK_gandalf_ on 2008-03-31
I have Kubuntu 8.04, and the fix (alsa-driver etc etc) doesn't work. 

Someone said maybe it's for the kernel version, which on hardy the last stable available is 2.6.24-12. 

is it possibile this is the problem? i have to send a bug report? :(

---

### Post by Elderlygent on 2008-04-01
Thanks Vor. Alas The system won't let me uninstall as you suggest.
So let non-Dell users beware.

---

### Post by czcar on 2008-04-01
Hi

So is this working with Ubuntu 8.04? 

lspci | grep Audio shows:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

But the above solution works to no avail!

Any suggestions,

Thanks

Cameron

---

### Post by LK_gandalf_ on 2008-04-01
I'have just written it....for me the microhpone doesn't work on 8.04 . It seems to be related to the kernel, so do we need to do a downgrade?
Can ew report the bug?

---

### Post by herger on 2008-04-02
Hi all.
I have Dell XPS 1330 and he microphone doesn't work: I can only record a terrible noise....
The settings are all the same as at the beginning of the thread and if I post

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

What can I do to use skype?
Thanks in advance and regards

Herger

---

### Post by LK_gandalf_ on 2008-04-04
Update. With the last hardy kernel 2.6.24-14 the microphone still doesn't work.
Please, any suggestion? No skype no party....:(

---

### Post by davarse on 2008-04-14
hi i find this thread in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and i tried to install to my laptop (aspire 5920) but it has error messege when i tried to do Setup installation directories (no. 4 in the giude)
i got the message from terminal: 

david@david:/usr/src/alsa$ sudo cp /home/user/downloads/alsa-* /usr/src/alsa
cp: cannot stat `/home/user/downloads/alsa-*': No such file or directory
david@david:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.16.tar.bz2
tar: alsa-driver-1.0.16.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david:/usr/src/alsa$ sudo tar xjf alsa-lib-1.0.16.tar.bz2
tar: alsa-lib-1.0.16.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david:/usr/src/alsa$ sudo tar xjf alsa-utils-1.0.16.tar.bz2

any suggestion??:confused:

---

### Post by Styx on 2008-04-16
Hi

> david@david:/usr/src/alsa$ sudo cp /home/user/downloads/alsa-* /usr/src/alsa
cp: cannot stat `/home/user/downloads/alsa-*': No such file or directory


The problem is that you are trying to copy (cp) the data from /home/user/download/... It appears that you do not haf this directory. 
If you downloaded with firefox then the date might be on the desktop

Try
```
sudo cp ~/desktop/alsa-* /usr/src/alsa
```

good luck. For me i dit not work on an inspiron 1520

---

### Post by mrojas73 on 2008-04-20
Worked great in getting my mic working.  XPS M1530.
Thank you

---

### Post by jespdj on 2008-04-20
On the Ubuntu Hardy release candidate, the microphone works out-of-the-box (ALSA 1.0.16 is already included). You do have to configure it, however:
[LIST=1]
[*]Double-click the volume control icon in the top right of the screen.
[*]Select Edit / Preferences.
[*]Add "Digital" and "Digital Input Source" to the list of visible tracks.
[*]On the Options tab, select "Digital Mic 1" for "Digital Input Source".
[*]On the Recording tab, set the volume for the microphone.
[/LIST]

---

### Post by herger on 2008-04-20
Hi.
I tried Your suggestion, but I do not have any "Digital Input Source", just 3 "Input Source".....  :confused:
Then, I selected "Mic 1" in "Input source", but if I launch the "sound recorder", it doesn't register anything, enev changing all the possibile sources...
What can I do?? I am really disappointed: I have to run Windows Vista on my other partition just to use Skype....
Thanks in advance and regards

Herger

---

### Post by Fascination on 2008-04-24
> **jespdj said:**
> On the Ubuntu Hardy release candidate, the microphone works out-of-the-box (ALSA 1.0.16 is already included). You do have to configure it, however:
[LIST=1]
[*]Double-click the volume control icon in the top right of the screen.
[*]Select Edit / Preferences.
[*]Add "Digital" and "Digital Input Source" to the list of visible tracks.
[*]On the Options tab, select "Digital Mic 1" for "Digital Input Source".
[*]On the Recording tab, set the volume for the microphone.
[/LIST]

Worked like a dream, perfect!

---

### Post by crimsontime on 2008-04-30
Yes, thank you, thank you Jespdj!!!

I've spent hours trying to get this in Gutsy, installed the Dell backports which completely destroyed my audio.  Then installed Hardy and finally found your post.  You're my Ubuntu hero of the day:)

---

### Post by IgnatiusReilly on 2008-04-30
GREAT!!!

Thanks a lot.

It works also with Hardy and my Dell XPS M1330.

---

### Post by LK_gandalf_ on 2008-05-01
> **herger said:**
> Hi.
I tried Your suggestion, but I do not have any "Digital Input Source", just 3 "Input Source".....  :confused:
Then, I selected "Mic 1" in "Input source", but if I launch the "sound recorder", it doesn't register anything, enev changing all the possibile sources...
What can I do?? I am really disappointed: I have to run Windows Vista on my other partition just to use Skype....
Thanks in advance and regards

Herger

try sudo alsamixer -V -a
;)

---

### Post by drdanield@gmail.com on 2008-06-08
Below jespdj's guide worked for the laptop internal microphone on Gateway M-6319 that has audio device chipset Intel 82801H (ICH8 Family) HD Audio Controller (rev 03)

> **jespdj said:**
> On the Ubuntu Hardy release candidate, the microphone works out-of-the-box (ALSA 1.0.16 is already included). You do have to configure it, however:
[LIST=1]
[*]Double-click the volume control icon in the top right of the screen.
[*]Select Edit / Preferences.
[*]Add "Digital" and "Digital Input Source" to the list of visible tracks.
[*]On the Options tab, select "Digital Mic 1" for "Digital Input Source".
[*]On the Recording tab, set the volume for the microphone.
[/LIST]

Thanks jespdj.  For other info re how to get the Gateway M-6319 working with Ubuntu see [http://nohair.com/code/computers:ubuntu:gateway_m-6319](http://nohair.com/code/computers:ubuntu:gateway_m-6319)

---

### Post by fcb on 2008-07-03
I am also using a Dell XPS m1330. Last night I fixed my internal microphone by enabling the "Digital Input Source". I don't know why but, now it is gone, there is no "Digital Input Source" tick-box in alsamixer. Can anyone help with this?

---

