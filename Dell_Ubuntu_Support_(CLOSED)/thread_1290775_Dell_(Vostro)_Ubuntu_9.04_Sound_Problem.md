---
title: "Dell (Vostro) Ubuntu 9.04 Sound Problem"
date: 2009-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goostmaster on 2009-10-13
I have a Dell Vostro 220 on which I'm dual-booting Vista x86 and Ubuntu 9.04.

On the Ubuntu I'm having difficulties with the sound, i.e. everything seems to be properly set up but I can only get sound from a USB headset as opposed to the main speakers. 
A large hindrance in fixing this problem is that I don't know what my sound card actually is.
It could either be an HDA Intel sound card or an 82801JI (ICH10 Family) HD Audio Controller. The third option is an ALC662 Digital ALSA Playback Device. At least according to the Checkbox Report ([file:///home/goosty/.checkbox/submission.xml](file:///home/goosty/.checkbox/submission.xml)) I don't know if that link will actually work.
If anyone can help me figure out which one of those is my actual sound card, that would be a great help as the first step to fixing this problem.
If anyone knows what the deuce my problem is and can help me out, that would be greatly appreciated.
Also, I have no troubles with sound on the Vista, just troubles with everything else, cos its Vista, and can't get anything right.

Update:
I still don't know exactly what my sound card is, I think its a Realtek ALC662, which according to some random dude who is my friend is an integrated motherboard sound card, but the words HDA Intel keep popping up so i dont know what the **** is going on.

On the upside, here is my ALSA configuration:

#autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
#Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quite --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index-2
options snd-intel8x0m index=-2
options via82xx-modem index-2
#options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

#USB Magic, part 1

alias, snd-card-0 snd-hda-intel
options-snd-hda-intel index=0




That is my alsa configuration.

Yes, I have tried the line options snd-hda-intel model=MODEL

but according to the alsa-CONFIGURATION.txt, any models listed of ALC662 dont work with my computer, which is not a laptop. I seem to be having trouble finding anybody else who has my problem, but even if i do find somebody, they seem to be using a laptop.

Please, if anyone can help. Please help me. PLEASE

Update:
Hello, again, to anyone who gives a damn. 
The sound card is an HDA Intel ICH10 Family sound card, Codec: Realtek ALC662. I've managed to figure out that much by myself.
Also, my ALSA configuration is reset to the default, namely becuase i re-installed Ubuntu.
Problem is still there.

---

