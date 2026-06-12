---
title: "No Sound at all"
date: 2005-07-31
forum: Desktop Environments
---

### Post by serioussam on 2005-07-31
Sorry to bother you guys again but i m a complete linux newbie  :? 

I have tried all the setting and also checked this guide [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) to configure the sound still i dont get any sound at all :(

When i double click on the sound icon all the bars seems to be at the right place too :-? 

This is what is see after clicking on File>>Change Device 
0. Analog Devices (OSS Mixer)
1. USB Mixer (OSS Mixer)
2. Sigmatel (OSS Mixer)
3. Intel 82801DB-ICH4 (Alsa Mixer)
4. USB Device 0x46D:0x8b3 (Alsa Mixer)
5. Dell Sound Blaster Live! (Alsa Mixer)

No matter which one i select of these there no effect at all ](*,) 

Pls some one help me here :)

---

### Post by varunus on 2005-07-31
You have a sound blaster live?  Go here to fix your sound and make it work:
[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)

Apparently Ubuntu doesn't include the emu10k1 driver...

---

### Post by serioussam on 2005-07-31
hmm well i tried but still no effect :(

---

### Post by 471v3 on 2005-07-31
[QUOTE=serioussam]Sorry to bother you guys again but i m a complete linux newbie  :? 

I have tried all the setting and also checked this guide [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) to configure the sound still i dont get any sound at all :(

When i double click on the sound icon all the bars seems to be at the right place too :-? 

This is what is see after clicking on File>>Change Device 
0. Analog Devices (OSS Mixer)
1. USB Mixer (OSS Mixer)
2. Sigmatel (OSS Mixer)
3. Intel 82801DB-ICH4 (Alsa Mixer)
4. USB Device 0x46D:0x8b3 (Alsa Mixer)
5. Dell Sound Blaster Live! (Alsa Mixer)

No matter which one i select of these there no effect at all ](*,) 

Pls some one help me here :)[/QUOTE]
 Hey, I got sound blaster and I got the same prob ----> duh .. damn, it is pretty hard to fix. Lol, just keep trying ----> GO!!!!!

Linux ..oh linux ... God Bless You My Dear

---

### Post by serioussam on 2005-08-01
[QUOTE=471v3]Hey, I got sound blaster and I got the same prob ----> duh .. damn, it is pretty hard to fix. Lol, just keep trying ----> GO!!!!!

Linux ..oh linux ... God Bless You My Dear[/QUOTE]
 *bump* :(

---

### Post by varunus on 2005-08-02
Can you go into your BIOS and turn off your onboard sound card?  It seems you have an onboard intel and a Sound Blaster, I'm assuming you want to use the sound blaster.

Also, make sure your cord is plugged into the correct sound card on the back.

Also, what is the output of "lsmod | grep snd" in a terminal?

---

### Post by serioussam on 2005-08-20
[QUOTE=varunus]Can you go into your BIOS and turn off your onboard sound card?  It seems you have an onboard intel and a Sound Blaster, I'm assuming you want to use the sound blaster.

Also, make sure your cord is plugged into the correct sound card on the back.

Also, what is the output of "lsmod | grep snd" in a terminal?[/QUOTE]

Hello this is what i get after that command "lsmod | grep snd" , what does this mean now   :?  :roll: 

snd_emu10k1x           18084  3
snd_usb_audio          60224  0
snd_usb_lib            11776  1 snd_usb_audio
snd_intel8x0           29984  1
usbcore               107384  7 snd_usb_audio,pwc,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
snd_emu10k1            81668  0
snd_rawmidi            22944  3 snd_emu10k1x,snd_usb_lib,snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  3 snd_emu10k1x,snd_intel8x0,snd_emu10k1
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd_pcm_oss            47652  2
snd_pcm                84872  6 snd_emu10k1x,snd_usb_audio,snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  4 snd_emu10k1x,snd_intel8x0,snd_emu10k1,snd_pcm
snd_mixer_oss          16768  2 snd_pcm_oss
snd                    50276  14 snd_emu10k1x,snd_usb_audio,snd_intel8x0,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  4 snd

---

