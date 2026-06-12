---
title: "Alsa kernel module problem..."
date: 2009-01-20
forum: General Help
---

### Post by Crafty Kisses on 2009-01-20
So one of my older computers I'm trying to run the 2.6.26-1-686 kernel, but my soundcard doesn't work under it for some reason, so I dug a little deeper, and it turns out I need the following kernel module "**snd-cs46xx.ko**" so I looked for it, and couldn't find it, so I ran into the following problem, it's a little complex if you can bare with me:
```
sudo apt-get update
sudo apt-get install alsa-source
m-a prepare
m-a a-i alsa-source
```
So now I have the alsa source, and module assistant, as it turns out the snd-cs46xx module is not in that alsa package, so I run the following:
```
modinfo soundcore
```
It didn't return I had a module, so I finally downloaded the driver from alsa's website, and I try to compile it, by doing the following:
```
cd /usr/src
mkdir alsa
cd alsa
cp /downloads/alsa-snd-cs46xx.ko
```
Then I unzip the module, then I start building it:
```
bunzip2 alsa-driver-alsa-snd-cs46xx.ko
tar -xf alsa-driver-alsa-snd-cs46xx.ko
cd alsa-driver-alsa-snd-cs46xx.ko
./configure --with-cards=cs46xx --with-sequencer=yes ; make ; make install
```
Then I obviously set the permissions:
```
chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 
```
I also grab the alsa-lib package, and start unzipping it:
```
bunzip2 alsa-lib-alsa-snd-cs46xx.ko
      tar -xf alsa-lib-alsa-snd-cs46xx.ko
      cd alsa-lib-alsa-snd-cs46xx.ko
      ./configure ; make ; make install

```
Then I insert the alsa-snd-cs46xx module into the kernel:
```
modprobe snd-cs46xx ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```
So then, I search to see if the module exists, so I run the following:
```
lsmod | grep alsa-snd-cs46xx.ko
```
Then I get the following results:
```
FATAL: Module alsa-snd-cs46xx.ko not found.
```
So what I wanted to do now is test something, I downloaded the original alsa driver tarball, so I ran the following:
```
tar xf alsa-driver-1.0.17.tar.bz2
cd alsa-driver-1.0.17/
./configure --with-cards=cs46xx --with-sequencer=yes --with-isapnp=no --disable-verbose-printk
make
make install
modprobe snd-cs46xx
```
So then I try to search for the module again by running:
```
modprobe snd-cs46xx
```
I get the same results as last time:
```
FATAL: Module alsa-snd-cs46xx.ko not found.
```

---

### Post by Yellow Pasque on 2009-01-20
There's an excellent script for building the latest ALSA suite from source:
[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)
Note that ALSA 1.0.19 was released today (1/19/09).

Also, if you can't get ALSA to work, you can try OSS4. It supports some cs46xx devices:
```
oss_cs461x	pci1013,6001	Crystal CS4610
oss_cs461x	pci1013,6003	Crystal CS4280 
oss_cs461x	pci1013,6004	Crystal CS4615
oss_cs461x	pcs153b,112e	Terratec DMX Xfire 1024
oss_cs461x	pcs1681,50	Hercules Game Theater XP
oss_cs461x	pcs1681,51	Hercules Game Theater XP+
oss_cs461x	pcs5053,3357	TurtleBeach SantaCruz / VideoLogic SonicFury
```

---

