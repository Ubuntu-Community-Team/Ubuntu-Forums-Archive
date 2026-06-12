---
title: "Startup Sound Works but no sound from then on ..."
date: 2006-05-29
forum: Desktop Environments
---

### Post by gideono on 2006-05-29
Hi I installed breezy this morning and it would seem that everything is working fine except my sound. I can hear the sound that plays when the login screen pops up but
the sound cuts out after that ... If i try and play something with xmms i get the following error :
 
<snip>
** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Device or resource busy
Message: alsa mixer timed out
</snip>
Note: Nothing else is open playing sound.

This is my lspci output:
<snip>
ls@escape:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150
0000:06:01.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:01.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
</snip>

None of the other audio applications in ubuntu standard install seems to work either yet i get the startup sound fine ... but nothing from then on can someone maybe shed some light on the subject here ?

Thanks in Advance

---

### Post by Sef on 2006-05-29
Let's start with the easy things first:

1) Sound icon > right click > open volume control > unmute if any sound icons are muted and sound is high enough.

2) System > Preferences > Sound >  make sure your default is set.

3) alsamixer > make sure that all are unmuted and sound is high enough


If one of those works, then you would need to install the codecs, if you have not already:

[RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by gideono on 2006-05-29
Hi Sef

Thanks for the reply ...
I checked 1 , 2 and 3 and they were all correct nothing muted or on low volume
Any other ideas ? I dont know if this will help but the output of 
lsof tells me that dsp is not being used but aplay seems to be hung on a wave
file called question.wav.
I have killed the aplay process manualy and succeeded in gettiing xmms not to give
dsp device busy anymore but it still doesnt play anything it just sits at 0:00.

---

### Post by gideono on 2006-05-29
Just and update

I loaded the whole directory of /usr/share/sounds/ into xmms.
And hit play ... now it skips the most of them but then it plays some other ones
but when it plays one it sounds distorted / condensed and then freezes on that one
until i manualy skip it ... for example it would play bigben.wav.

TIA

---

