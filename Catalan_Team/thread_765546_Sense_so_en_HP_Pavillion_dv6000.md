---
title: "Sense so en HP Pavillion dv6000"
date: 2008-04-24
forum: Catalan Team
---

### Post by miquelet on 2008-04-24
Tinc un portàtil nou amb una partició amb l'XP i una altra amb l'ubuntu.  Amb l'XP no tinc cap problema amb el so, però amb l'ubuntu no em funciona.  Vaig instal·lar els drivers nous d'ALSA i la icona del so que fins llavors estava vermella es va posar blava, com si hagués de funcionar..., però no.  Quan intento reproduir el que sigui amb el Totem, em surt um missatge que diu que el dispositiu d'audio està ocupat. A Preferències de so, reproducció de so, test, em surt això:  audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No s'ha pogut obrir el recurs per a l'escriptura.  Algú em pot orientar una mica?  Moltes gràcies.

---

### Post by menut on 2008-04-25
Has provat això ?:

> [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Estaria bé que ens diguessis quin model exacte tens ([a aquesta llista em penso que estan tots]("http://search.hp.com/gwesspa/query.html?lang=es&submit.x=13&submit.y=7&qt=pavillion+dv6000&la=es&cc=es") !)

---

### Post by miquelet on 2008-04-25
M'he estat mirant l'enllaç i m'ha semblat que l'opció que s'adeia al meu cas era la J.  Calia fer això:
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.16rc1.tar.bz2
cd alsa-driver-1.0.16rc1
./configure --with-cards=hda-intel
make
sudo make install

però quan he fet make m'ha sortit errors:

miquel@miquel-laptop:~/alsa-driver-1.0.16rc1$ make
make dep
make[1]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq'
make[4]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq/oss'
make[4]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq/oss'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/other'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/other'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/vx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/vx'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/wavefront'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/wavefront'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/synth'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/synth/emux'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/synth/emux'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/synth'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ymfpci'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ymfpci'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus'
make[4]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/sh'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/sh'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb/usx2y'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb/usx2y'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/vx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/vx'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia'
make[1]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/miquel/alsa-driver-1.0.16rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/hwdep.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/memory_wrapper.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/memalloc.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/sgbuf.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm_native.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm_lib.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm_timer.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm_misc.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/pcm_memory.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/rtctimer.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/timer.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/wrappers.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/misc_driver.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/sound.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/init.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/memory.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/info.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/control.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/misc.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/device.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/isadma.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/sound_oss.o
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.o
En el fitxer inclòs dès de /home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 dès de /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: la macro "init_utsname" va rebre 1 arguments, però en va prendre solament 0
In file included from /home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/home/miquel/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/home/miquel/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
miquel@miquel-laptop:~/alsa-driver-1.0.16rc1$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/miquel/alsa-driver-1.0.16rc1/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: ha fallat stat() sobre «snd-hwdep.ko»: No such file or directory
cp: ha fallat stat() sobre «snd-page-alloc.ko»: No such file or directory
cp: ha fallat stat() sobre «snd-pcm.ko»: No such file or directory
cp: ha fallat stat() sobre «snd-rtctimer.ko»: No such file or directory
cp: ha fallat stat() sobre «snd-timer.ko»: No such file or directory
cp: ha fallat stat() sobre «snd.ko»: No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1
miquel@miquel-laptop:~/alsa-driver-1.0.16rc1$ make
make dep
make[1]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq'
make[4]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq/oss'
make[4]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq/oss'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore/seq'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/acore'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/other'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c/other'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/i2c'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/vx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers/vx'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/drivers'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/isa/wavefront'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa/wavefront'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/isa'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/synth'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/synth/emux'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/synth/emux'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/synth'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ymfpci'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci/ymfpci'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pci'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus'
make[4]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa/soundbus'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/aoa'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/soc/sh'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc/sh'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/soc'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/usb/usx2y'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb/usx2y'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/usb'
make[2]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/vx'
make[3]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia/vx'
make[2]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1/pcmcia'
make[1]: Leaving directory `/home/miquel/alsa-driver-1.0.16rc1'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/miquel/alsa-driver-1.0.16rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.o
En el fitxer inclòs dès de /home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 dès de /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: la macro "init_utsname" va rebre 1 arguments, però en va prendre solament 0
In file included from /home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/home/miquel/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/home/miquel/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/home/miquel/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/home/miquel/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
miquel@miquel-laptop:~/alsa-driver-1.0.16rc1$ 

Em demanaves el meu model; em sembla que és aquest:00:1b.0 0403: 8086:284b (rev 03)

Demano excuses per endavant per si el missatge és massa llarg.

---

### Post by papapep on 2008-04-25
És una Gutsy o una Hardy?

---

### Post by miquelet on 2008-04-27
És Gutsy.  Però ja tinc el problema solucionat, només m'ha calgut reiniciar l'equip, cosa que he fet al cap de dos dies.  Moltes gràcies!!!

---

