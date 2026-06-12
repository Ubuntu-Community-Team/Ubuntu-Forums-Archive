---
title: "Sound Fix does not Work - Mini 9"
date: 2009-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sJ&amp;$op*2W on 2009-03-25
The fix absolutely does not fix my sound. I have tried 4 times, with fresh installs, adding the line to my alsa-base file, mixer after reboot, etc.  To the letter of the tutorial.  I tried removing pulseaudio, doing a killall pulseaudio, disabling bluetooth in the BIOS.  Nothing.  Not a bit of sound.

I have a Mini 9 that came with Windows XP and BIOS A04.  

I really want to get this working as Dell is going to charge me a restocking fee if I return it.

---

### Post by anjilslaire on 2009-03-26
Have you gone into the sound mixer and turned the speaker volume up for the HDA Intel (Alsa mixer) device?

---

### Post by armandh on 2009-03-26
the details of the sound fix that ALWAYS worked for me starts the 3rd post down

[http://ubuntuforums.org/showthread.php?t=981602](http://ubuntuforums.org/showthread.php?t=981602)


PS I agree besure the head phone and/or speakers are turned up.[and mutes off] 
.

---

### Post by sJ&amp;$op*2W on 2009-03-26
As I said, I followed the instructions to the letter and turned up speakers. I tried that in both the GUI mixer and in ALSAMIXER in terminal.

---

### Post by armandh on 2009-03-26
if you followed the instructions [and saved the change to the file] it should work 
or 
it is broken
or
exactly was not really exactly every space and dash.
or 
there has been some model change everyone is unaware of

---

### Post by jespdj on 2009-03-26
Ok, enter this command:
```
cat /etc/modprobe.d/alsa-base
```
Copy and paste the output here.

Did you reboot after applying the fix?

---

### Post by sJ&amp;$op*2W on 2009-03-26
Yes, I typed the line exactly, saved alsa-base, restarted.  As I said, to the letter.  Here are the results from cat in terminal.

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
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
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell

---

### Post by jespdj on 2009-03-27
I copied your ALSA config file and compared it (with diff) with mine, it is exactly the same, so the problem is not in the config file.

Have a look at your mixer settings by double-clicking the volume icon in the top left of the screen. Click Preferences to make more items visible in the mixer settings and turn up the volume for Master, PCM and Speaker. See the attachment for what my mixer looks like.

Also have a look at the [PulseAudio Fixes](http://ubuntuforums.org/showthread.php?t=789578) thread, follow the instructions for your version of Ubuntu.

---

### Post by sJ&amp;$op*2W on 2009-03-27
Okay, my mixer looks exactly like yours.  I'll take a look at the pulseaudio fixes.  I did try doing a
> 
killall pulseaudio
sudo apt-get remove --purge pulseaudio
and that didn't seem to help.

Thanks for all the assistance.  I'm beginning to think the speakers are just physically defective.  I never booted Windows so I never got a chance to see if they worked under that.

---

