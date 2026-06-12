---
title: "Cannot get my Ubuntu to work properly! I'm desperate!"
date: 2009-02-26
forum: General Help
---

### Post by avrilrox on 2009-02-26
Hello, I've been trying to get Ubuntu to work on my AMD64 based computer but I have found a million problems on the way.

I am currently running Ubuntu 8.04, and i have no sound at all! I am using an onboard chip called C-Media 6501. It's an usb device and should be supported by alsa 1.0.14 and above.

**What i have done so far:**

Installed Ubuntu Jaunty Jackalope Alpha 1.

What happened: No sound at all, even though i was running Alsa 1.0.18. Searched for info on the internet, nothing seemed to work.
My usb wireless card (Trendnet 425ub) did connect to my wireless network, but the connection was rather slow and i got really high pings and a data loss of above 50%. My Nvidia 9600Gt worked perfectly.

I thought there might be some issues with the Alpha version, so i installed Ubuntu Intrepid Ibex 8.10. Same problem with my sound device, my wireless worked the same way as it used to under Jaunty Jackalope but i couldn't get my Nvidia Drivers to work. They just refused to install.

I had used 8.04 before so i decided to install it. I didn't know the 64bit version would have such a bad compatibility. I used to run everything on my 32 bit Hardy Heron. I currently cannot get my wireless adapter to work, not even with Ndiswrapper (which did work under 32bit). Cannot install my Nvidia drivers. Cannot get my sound to work.

I currently cannot connect to my wireless network, so i need to switch between OS in order to download files. It's really annoying. I hate Vista and i want to use Ubuntu.. but i can't.


Also, i installed alsa, except for alsa-utils, which was the last one i attempted to install and failed.

Any ideas?

---

### Post by jonobr on 2009-02-26
Im thinking you bought the cup prematurely...
.
DId you try the sound troubleshooting guide 
here
[http://https://help.ubuntu.com/community/SoundTroubleshooting]("http://https://help.ubuntu.com/community/SoundTroubleshooting")

Im sure you can ignore the first few steps

---

### Post by albinootje on 2009-02-26
> **avrilrox said:**
> I am using an onboard chip called C-Media 6501.

So, you didn't get any sound in all the different configurations, right ?
Here are two links with possible solutions :
[http://ubuntuforums.org/showthread.php?t=439392](http://ubuntuforums.org/showthread.php?t=439392)
[https://answers.launchpad.net/ubuntu/+question/41059](https://answers.launchpad.net/ubuntu/+question/41059)

---

### Post by avrilrox on 2009-02-26
> **jonobr said:**
> Im thinking you bought the cup prematurely...
.
DId you try the sound troubleshooting guide 
here
[http://https://help.ubuntu.com/community/SoundTroubleshooting]("http://https://help.ubuntu.com/community/SoundTroubleshooting")

Im sure you can ignore the first few steps

Alright. Installed Jaunty Jackalope in order to get my wireless adapter to work. I'll check that link! Thanks!

---

### Post by avrilrox on 2009-02-26
> **albinootje said:**
> So, you didn't get any sound in all the different configurations, right ?
Here are two links with possible solutions :
[http://ubuntuforums.org/showthread.php?t=439392](http://ubuntuforums.org/showthread.php?t=439392)
[https://answers.launchpad.net/ubuntu/+question/41059](https://answers.launchpad.net/ubuntu/+question/41059)

That doesn't work for me either. Editing asounrc doesnt work.

Ubuntu does recognize my sound card but there is no sound output at all.

---

### Post by Yellow Pasque on 2009-02-26
If you want to use ndiswrapper with a 64-bit system, then you need a 64-bit (specifically Windows XP-64) driver. Also, just because you run 32-bit Ubuntu successfully on one machine, and then have problems with Ubuntu 64-bit on another machine, doesn't mean you should blame your problems on 64-bit "compatibility". If you want to test the theory out try installing Ubuntu 8.10 32-bit/x86 on your system with the ADM processor (just because you have an AMD64 CPU, it doesn't mean you have to run a 64-bit Linux).

---

### Post by cariboo on 2009-02-26
C-Media is having licensing issues and don't supply a lot of drivers for their hardware, to make sure there is a driver loaded for your hardware could you open a Applications-->Accessories-->Terminal and  type:

```
sudo lshw -C multimedia
```

and paste the output in your next post.

Jim

---

### Post by avrilrox on 2009-02-27
> **cariboo907 said:**
> C-Media is having licensing issues and don't supply a lot of drivers for their hardware, to make sure there is a driver loaded for your hardware could you open a Applications-->Accessories-->Terminal and  type:

```
sudo lshw -C multimedia
```

and paste the output in your next post.

Jim

```
PCI (sysfs)
```

---

### Post by avrilrox on 2009-02-27
> **Temüjin said:**
> If you want to use ndiswrapper with a 64-bit system, then you need a 64-bit (specifically Windows XP-64) driver. Also, just because you run 32-bit Ubuntu successfully on one machine, and then have problems with Ubuntu 64-bit on another machine, doesn't mean you should blame your problems on 64-bit "compatibility". If you want to test the theory out try installing Ubuntu 8.10 32-bit/x86 on your system with the ADM processor (just because you have an AMD64 CPU, it doesn't mean you have to run a 64-bit Linux).

I know I can run a 32 bit Linux but I have 4 gigs of ram, so i won't be able to use it completely.

Installing a Windows XP or WIndows Vista 64 bit wireless adapter driver freezes my ubuntu. It used to work with my Pentium D when i was running a 32bit Ubuntu.

---

### Post by avrilrox on 2009-02-27
Okay. I got my sound to work but it works only when i login. I can hear the login sound but i can't hear anything afterwards.

What i did was creating a asoundrc file under my home folder. Here's a cat of the file.
```
asd@x2:~$ cat .asoundrc
pcm.!default {
type plug
slave.pcm "softvol"
}

pcm.softvol {
type softvol
slave {
pcm "ch51dup"
}
control {
name "All"
card 0
}
}

pcm.ch51dup {
type route
slave.pcm surround51
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.5 0.5
ttable.1.5 0.5
}

```



And changed snd-usb-audio from **-2** to **0**
Here's a cat.
```
asd@x2:~$ sudo cat /etc/modprobe.d/alsa-base
[sudo] password for asd: 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; :sbin/modprobe --quiet snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
**options snd-usb-audio index=0**
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```


I also **created** the **audio** group and added my user to it. Nothing seemed to change.

---

### Post by albinootje on 2009-02-28
> **avrilrox said:**
> I know I can run a 32 bit Linux but I have 4 gigs of ram, so i won't be able to use it completely.


To use 4 Gb of RAM or more you only need a Linux kernel with PAE support, you can do so by installing and using the kernel from the ubuntu-server :
```

sudo apt-get install linux-image-server

```
See also : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by avrilrox on 2009-02-28
> **albinootje said:**
> To use 4 Gb of RAM or more you only need a Linux kernel with PAE support, you can do so by installing and using the kernel from the ubuntu-server :
```

sudo apt-get install linux-image-server

```
See also : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Sweet! I had no idea this existed! That's great to know!

Do you think I'd get a much lower performance by running a 32bit system on my Athlon64?

---

### Post by avrilrox on 2009-02-28
Is there any way to get my audio working? I can hear the Ubuntu sound when logging in but there's no sound afterwards.

---

### Post by entr3p on 2009-02-28
Check your Volume Control on the top right section.

---

### Post by jwbrase on 2009-02-28
Yes, I recall that I had to find and unmute some rather obscure tabs in volume control to get my sound working.

---

### Post by avrilrox on 2009-02-28
The problem is I'm running Jaunty Jackalope and there is no sound bar i can check. I set the volume to the highest in every channel using alsamixer. Nothing seemed to help though.

---

### Post by BigZee on 2009-03-02
Hi,

I've a similar problem with an Asus k8n4-e deluxe motherboard. Everything works except sound. Could you try something? It's not a solution but I think it's a useful test. If you change from using the nvidia graphics driver (nvidia) in xorg.conf to the open source nv driver, does sound work ok? It does for me so I'm blaming the nvidia driver. My guess is that the nvidia driver is taking over duties for sound (possibly because my card can also support sound through HDMI although I'm not using it) but that is a guess. Anyway, if you find that sound works, then it might be that you're getting the same problem as I am.

---

### Post by avrilrox on 2009-03-02
> **BigZee said:**
> Hi,

I've a similar problem with an Asus k8n4-e deluxe motherboard. Everything works except sound. Could you try something? It's not a solution but I think it's a useful test. If you change from using the nvidia graphics driver (nvidia) in xorg.conf to the open source nv driver, does sound work ok? It does for me so I'm blaming the nvidia driver. My guess is that the nvidia driver is taking over duties for sound (possibly because my card can also support sound through HDMI although I'm not using it) but that is a guess. Anyway, if you find that sound works, then it might be that you're getting the same problem as I am.

Hello. I have a nVidia 9600GT and i installed these drivers 5 seconds before checking this thread... :lolflag:

I remember seeing some **sound modules** being installed with the graphic drivers. You may be right?

Have you tried adding you user to the **audio group**? It doesn't work for me, but it does for most people. Also, make sure you sound is not muted and that you have set your output to Alsa? What version of Ubuntu are you currently running?

---

