---
title: "IBM 600e sound working !!!"
date: 2005-05-02
forum: Desktop Environments
---

### Post by petertc on 2005-05-02
Like most people i have been having problems getting sound working with this laptop,
I have read the posts on most forums a lot depends on the kernek you are running and also the version of ALSA.
Any way to cut a long story short here is what i did. 

Fist of you need to edit the /boot/grub/menu.lst and add this to the kernel you want to boot. acpi=off pnpbios=off. 
See my list below
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=off quiet splash pnpbios=off
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

next off i edited the /etc/modules. and added this line 
snd_cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0 mpuio=0x330 mpuirq=9
it is the last 2 items that seem to be important without these it does not seem to work on my machine .

here is my /etc/modules content.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
snd_cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0 mpuio=0x330 mpuirq=9

alsa-base has been left alone.

>this is an edit i removed a file i created and it killed the sound !! 

add a file /etc/modprobe.d/alsa  and copy this in to the empty file 

# Alsa 0.9.X kernel modules' configuration file.
# taken from [http://linuxfocus.org/~guido/gentoo-tp600e/](http://linuxfocus.org/~guido/gentoo-tp600e/)
#tp600e-gentoo1.4-config.html

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236 
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

<<

you will see in the kmixer windows things listed as CS4239

The one thing to make sure is that the mic is turned off otherwise you get bad feedback.


Now all i have to try and do is get my quickcam working, like most tings i have tried most of the posts and they don't seem to work so i will perseavere.

I am on  the whole impressed with Kubuntu, i have use Mandrake upto 10, then went onto an HD install of knoppix, this is what i still use on my main pc. The laptop is what i try things out on. 
Kantonix, and mepis have both been good, it's apt that really gets the most praise as package management is so much easier than rpms.

I hope the info given helps others out,

---

### Post by viuks on 2005-05-15
Thanks for useful tip. But I still have no sound with hoary. This worked fine for me with warty. So now I will try, to install warty and then upgrade to hoary. Maybe it will work.
Maybe it is something to do with installations, becaiuse U use Kubuntu, but mine is default Ubuntu.

---

### Post by Jussi Kukkonen on 2005-05-21
[QUOTE=viuks]
Maybe it is something to do with installations, becaiuse U use Kubuntu, but mine is default Ubuntu.[/QUOTE]

Nope. I've got sound working on my 600E with Ubuntu 5.04. I used Scott Campbells instructions I found on ubuntu-users mailing list (title had something to do with emacs and alsaconf, although neither was used...).

Here are my notes from that tweaking:

1. make sure you have these rows in */etc/hotplug/blacklist.d/alsa-base* (the last one is probably already there).
```
   snd-cs46xx
   cs46xx
```

2. add these to *etc/modprobe.conf*
```
alias char-major-116 snd
alias char-major-14 soundcore
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
options snd  device_mode=0660
alias snd-card-0 snd-cs4236
alias sound-slot-0 snd-cs4236
options snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5
```

3. reboot

After the reboot (actually after every reboot) :

4 a) load the modules 
```
sudo modprobe snd-cs4236
sudo modprobe snd-mixer-oss
sudo modprobe snd-pcm-oss
```
4 b) ...and set sound levels with a mixer. Here are my amixer commands
 (although you might want to do test first with Volume Control in Gnome):
```
amixer sset Master 31 on
amixer sset PCM 63 on
amixer sset Playback 3 on
```

---

### Post by wvslkr on 2005-05-21
If you add  snd-cs4236 to /etc/modules you won' have to modprobe on reboot.
May require snd-cs4236 isapnp=0.

---

### Post by viuks on 2005-06-06
YES! I disabled quick boot in bios, and now sound works for me too.:)

---

### Post by IbeeX on 2005-06-16
Hi

I got this 

modprobe snd-cs4236 isapnp=0
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-686/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device

Ivan

---

### Post by IbeeX on 2005-06-18
Hi 
I managed it only in kernel parameter there should be pnpbios=off

kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro noapic nolapic acpi=off amp=on pnpbios=off quiet splash

Ivan

---

### Post by beansbbq on 2005-09-10
[QUOTE=IbeeX]Hi 
I managed it only in kernel parameter there should be pnpbios=off

kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro noapic nolapic acpi=off amp=on pnpbios=off quiet splash

Ivan[/QUOTE]


Ivan,


   I have an IBM 600E Thinkpad Pentium II.  I've installed ubuntu version 5.04 from the official media.  My sound problems begin during boot.  There is a consistent and annoying beep.  I modified my kernel parameters in /boot/grub/menu.lst 

**Original**
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

**Modified**
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro noapic nolapic acpi=off amp=on pnpbios=off quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


Upon rebooting my machine, I receive a boot error 17 I believe.  (Could be mistaken about that number).  My only option is to boot into safemode to revert back to my original file settings.  You mentioned that you only made the one change.  Do you see anything wrong with my configuration file?

Thanks,

Jonto

---

### Post by IbeeX on 2005-09-11
title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro noapic nolapic acpi=off amp=on pnpbios=off quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot 

Hi this is my exactly manu.lst

There is one more thig I found it on googe that zou need to desable quick boot in bios on 600e laptop 

___
BIOS Settings

In order for the sound card to work on the 600E you must disable "Quick Boot" in the BIOS. This can be done as follows:

   1. With the unit powered off, press and hold the F1 key.
   2. Power on the unit while still holding the F1 key. The "Easy Setup" screen should appear, at which point you can release the F1 key.
   3. Using the mouse, go to "Config", then to "Quick Book". Set "Quick Boot" to disabled.
   4. Save the BIOS settings and reboot.

If, later, you still don't get sound working, you might try the "Initialize" option in the BIOS, then make sure "Quick Boot" is still turned off. Save, and try sound again. 
___
from page [http://www.linux-laptop.net/hosted/thinkpad600e-fc4.html](http://www.linux-laptop.net/hosted/thinkpad600e-fc4.html) (and some more)

Can you try this

Ivan

---

