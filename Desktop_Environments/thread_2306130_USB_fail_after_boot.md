---
title: "USB fail after boot"
date: 2015-12-12
forum: Desktop Environments
---

### Post by palisz on 2015-12-12
Hi,
Have you ever met such a mistake? If I start my laptop, USB switches on and after some seconds switches off. Mouse LED does not light I can not use it. If I restart, (either from Win or ubuntu) everyting is OK. 
My machine is : Asus X750J laptop, Intel® Core™ i5-4200H CPU @ 2.80GHz × 4. 4 GB RAM,  120GB SSD, built in camera, card reader, DVD, Win10 - before it Win8.1 and the mistake was the same.
I checked the machine with: dmesg | grep -i USB and I found differences between the good and the bad start. When the USB does not work, the first few lines are the same, when the USB works well, but after you can read as follows:

[    2.316520] scsi5 : usb-storage 3-5:1.0
[    2.316550] usb 3-5: USB disconnect, device number 3
[    2.316594] usbcore: registered new interface driver ums-realtek
[    2.330473] usbcore: registered new interface driver ath3k
[    2.444862] usb 3-6: USB disconnect, device number 4
[    2.685127] usb 3-6: new full-speed USB device number 6 using xhci_hcd
[    7.691187] WARNING: CPU: 2 PID: 0 at  /build/linux-hEVYOL/linux-3.13.0/drivers/usb/host/xhci-ring.c:1590  handle_cmd_completion+0xe36/0xe40()
[    7.691188] Modules linked in: ctr ccm rfcomm bnep arc4 ath9k  ath9k_common ath9k_hw snd_hda_codec_realtek ath snd_hda_codec_hdmi  mac80211 cfg80211 joydev uvcvideo hid_generic videobuf2_vmalloc  videobuf2_memops ums_realtek videobuf2_core usb_storage videodev usbhid  hid ath3k btusb bluetooth nls_iso8859_1 x86_pkg_temp_thermal  intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul  ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper  ablk_helper cryptd snd_hda_intel snd_hda_codec serio_raw snd_hwdep  asus_nb_wmi asus_wmi sparse_keymap mxm_wmi lpc_ich snd_pcm shpchp  snd_page_alloc snd_seq_midi snd_seq_midi_event mei_me snd_rawmidi mei  snd_seq i915 snd_seq_device snd_timer snd video drm_kms_helper mac_hid  parport_pc soundcore drm ppdev i2c_algo_bit wmi lp parport psmouse ahci  r8169 libahci mii
[    7.895484] usb 3-6: Device not responding to set address.
[    8.099645] usb 3-6: device not accepting address 6, error -71
[    8.211782] usb 3-6: new full-speed USB device number 7 using xhci_hcd
[    8.229842] usb 3-6: New USB device found, idVendor=13d3, idProduct=3362
[    8.229845] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    8.229847] usb 3-6: Product: Bluetooth USB Host Controller
[    8.229848] usb 3-6: Manufacturer: Atheros Communications
[    8.229849] usb 3-6: SerialNumber: Alaska Day 2006
[    8.616302] usb 3-1: USB disconnect, device number 2
[    8.648537] usb 3-6: USB disconnect, device number 7
[    8.649532] usb 3-10: USB disconnect, device number 5

This mistake is not very dangerous, but a little bit unpleasant. ;) Can somebody explain, what happened, what is the problem?

---

### Post by palisz on 2015-12-12
So I found a solution, but I do not know why :D  According to the 2. line([    2.316550] usb 3-5: USB disconnect, device number 3) In the BIOS I switched off the card reader. The mistake remains the same. After it I switched off the bluetooth (usb 3-6). AND IT IS GOOD!  Well, I hate bluetooth, I never use and the machine is OK.
The only small problem, that I do not know, what happened :D

---

