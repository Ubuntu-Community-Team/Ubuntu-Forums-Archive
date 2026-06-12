---
title: "USB mouse not working"
date: 2006-08-30
forum: Desktop Environments
---

### Post by NoTiG on 2006-08-30
hey... ever since i updated last (around 122 updates) my mouse no longer works. before... it would work about half the time ... and when it didnt work i would just keep rebooting till it did. its a logitech G5 laser mouse... any ideas why it doesnt work? something to do with usb? 

PS. my logitech usb headphones dont work either. they did before... sometimes. 

all of this works fine in windows.

---

### Post by xtknight on 2006-08-30
See if you see any USB hub messages in **dmesg**.  **less** it using **dmesg | less** or perform these commands to cull out USB messages:

dmesg | grep ehci
dmesg | grep EHCI
dmesg | grep usb
dmesg | grep USB

---

### Post by NoTiG on 2006-08-30
dmesg | grep usb  gives nothing. is it suppose to ?

---

### Post by xtknight on 2006-08-30
That is a little odd.  What does **lsusb** report?  What about **lsmod | grep usb**?

---

### Post by NoTiG on 2006-08-30
snd_usb_audio          79296  1
snd_usb_lib            16640  1 snd_usb_audio
snd_hwdep               9376  1 snd_usb_audio
snd_rawmidi            25504  3 snd_seq_midi,snd_usb_lib,snd_mpu401_uart
usbhid                 39904  0
usbmouse                5504  0
snd_pcm                89864  6 snd_usb_audio,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd                    55268  17 snd_seq_oss,snd_seq,snd_usb_audio,snd_hwdep,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               130692  8 ndiswrapper,snd_usb_audio,snd_usb_lib,usbhid,usbmouse,ehci_hcd,uhci_hcd


one thing i should probably mention is that im on a laptop... and my touchpad still works. and also for the speakers... instead of routing sound through headphones it goes to the speakers..... so i wonder if these usb devices are just being overridden or something

---

### Post by xtknight on 2006-08-30
You know, I'm having lots of issues with my USB now too.  Maybe it's one of the recent updates?  I noticed a couple other USB threads so I think something's going on here.  Whenever I unplug/replug in my mouse my whole system unfreezes (keyboard/mouse freeze).  Weird.

---

### Post by dziubelis on 2006-11-02
True...
My USB mouse (HAMA) slows (to a crawl) / freezes the system (Ubuntu 6.06), but then I connect it to PS/2 (with adapter) and reboot, everything works fine.

Other USB stuff like flashdrive, externall HDD dont work at all.

Ill try finding out what reports will give commands posted (do I have to connect USB mouse for that?).

---

