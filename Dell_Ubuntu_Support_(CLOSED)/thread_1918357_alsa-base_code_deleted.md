---
title: "alsa-base code deleted"
date: 2012-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by algar32 on 2012-01-31
I accidently deleted the code in my alsa-base.config. I need it for sound i think. Can someone paste it here? Or show me how to get that folder again. Thanks. I am new to xubuntu so im kind of a noob ;)

---

### Post by ankspo71 on 2012-01-31
Do you mean /etc/modprobe.d/alsa-base.conf? That file comes from the package called "alsa-base".

Here's the code in my /etc/modprobe.d/alsa-base.conf (Xubuntu 11.10):
```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
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
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```




Here are the names of the default audio packages in Xubuntu 11.10, with the words "alsa" and "pulse" in the name.

```
james@XFCE:~$ dpkg --get-selections | grep alsa
alsa-base					install
alsa-utils					install
bluez-alsa					install
gstreamer0.10-alsa				install
```
```
james@XFCE:~$ dpkg --get-selections | grep pulse
gstreamer0.10-pulseaudio			install
libpulse-mainloop-glib0				install
libpulse0					install
pulseaudio					install
pulseaudio-esound-compat			install
pulseaudio-module-x11				install
pulseaudio-utils                                install
```




Hope this helps.

---

### Post by algar32 on 2012-01-31
Thanks so much, this is exactly what I needed :D.

---

### Post by algar32 on 2012-02-01
Actually I cant edit alsa-base.config... So it still has all that stuff in it but I cant add the line i need to make sound work on my dell mini 9... WHenever I go to save it, it says " cant open file to write"

---

### Post by ankspo71 on 2012-02-02
Hi,
Did you try editing the file with elevated privleges? Open your terminal and paste in the following command, if you haven't tried this already:
```
gksudo leafpad /etc/modprobe.d/alsa-base.conf
```
If that doesn't work then you might need to reinstall the package called 'alsa-base'.
Hope this helps.

---

### Post by algar32 on 2012-02-04
It allowed me to edit the code! thanks. But still no sound :(. I really just wish I could get sound on this thing. Has anyone else had problems with xubuntu and dell mini 9s? Thanks.

---

