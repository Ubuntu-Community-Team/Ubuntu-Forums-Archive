---
title: "Inspiron 1720 wireless issue"
date: 2012-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drivingmemad on 2012-08-27
I had Ubuntu 11.04 installed and all was working perfectly, however, I have now upgraded to 11.10 and cannot connect to internet wirelessly. I have had the same issue when trying out other Linux distros such as Open Suse and Mandriva.
I followed the advice in the Solved posting at [http://ubuntuforums.org/showthread.php?t=1974006](http://ubuntuforums.org/showthread.php?t=1974006)
This doesnt seem to have worked, though.
lsmod shows B43-Size31816Used by 0; and ssb-Size50682Used by 1 b43
My lspci -nn | grep 0280 output is
0c: 00.0 network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY[14e4:4315] (rev 01).
Any help and/or ideas would be most welcome.

---

### Post by mikewhatever on 2012-08-27
More info would be required to troubleshoot. Can you post the full output of lsmod and of 'rfkill list all'.

---

### Post by drivingmemad on 2012-08-28
Hi mikewhatever,
Thanks for the quick response.
lsmod output =
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
memstick               15857  1 r592
nand_ecc               13070  1 nand
mtd                    35662  2 sm_common,nand
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                63474  0 
btusb                  18160  2 
serio_raw              12990  0 
snd_seq_midi           13132  0 
bluetooth             148869  23 bnep,rfcomm,btusb
snd_rawmidi            25241  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  513833  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   196290  4 i915,drm_kms_helper
wmi                    18744  1 dell_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915

rfkill list all output = 
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by mikewhatever on 2012-08-28
The output of lsmod looks a bit short. Are you sure that is all?

---

### Post by drivingmemad on 2012-08-29
Hi mikewhatever,
Sorry. I missed this off the end of lsmod
video                  19069  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

Many thanks :$

---

### Post by mikewhatever on 2012-08-29
There is no wireless module in any part of the lsmod output, so you need to make sure it's loaded. 

sudo modprobe b43

That should load the module, the wireless should start working. If it does, just append b43 to /etc/modules to make it autoload at startup.

---

### Post by drivingmemad on 2012-08-30
Hi mikewhatever,
Thanks again for the response.
I'll give that a go and let you know the outcome :-)

---

### Post by drivingmemad on 2012-08-30
hi mikewhatever,
Success! Thanks, wireless module loaded and I now have internet access.
However, just to illustrate my lack of knowledge here, what is the command to append b43 to etc/modules?
Ive tried 
append b43/etc/modules
etc/modules/b43
b43 /etc/modules
None of these worked
Homer Simpson time methinks
I'll have a Google for the answer and see what I can find.

---

### Post by drivingmemad on 2012-08-30
hi mikewhatever,
All sorted now, thanks. 
i found this post on Ubuntu Forums [http://ubuntuforums.org/showthread.php?t=1790296](http://ubuntuforums.org/showthread.php?t=1790296)
And followed chilli555's instructions posted on June 24th 2011
Reboot my laptop, and all wireless connected straight away
I'll mark this post as Resolved now
Thank you very much for all your help, it was very much appreciated :-)

---

### Post by mikewhatever on 2012-09-02
Glad you got it working. :)

For the sake of future readers, Chili's instructions were as follows:

```
sudo su
echo b43 >> /etc/modules
exit
```

---

