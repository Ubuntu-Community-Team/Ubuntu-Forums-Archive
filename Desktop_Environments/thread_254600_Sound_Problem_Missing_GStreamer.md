---
title: "Sound Problem Missing GStreamer"
date: 2006-09-10
forum: Desktop Environments
---

### Post by meph on 2006-09-10
This is the error im getting when i click the sound ICON. I have been using this and it didn't really botherd me but i was wondering if there was an eazy fix.
> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Thank you for the help!
Alex

---

### Post by tuxinvader on 2006-09-10
Open Applications -> Accessories -> terminal 

Then run "lspci" and post the output here.

You could also run alsamixer and let us know if you see any volume controls or get an error. If you do get into it without an error hit 'esc' to exit.

---

### Post by meph on 2006-09-10
spci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)


alsamixer: function snd_ctl_open failed for default: No such device


i hope that helps

---

### Post by tuxinvader on 2006-09-10
Is it onboard sound? lspci doesn't list a sound card and alsa can't see it either?? If it is onboard, is it disabled in your BIOS? I would reboot and check your BIOS settings.

Is it a USB sound card? Try lsusb

---

