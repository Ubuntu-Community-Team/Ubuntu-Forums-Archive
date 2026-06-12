---
title: "PCTV HD Pro Stick"
date: 2009-01-07
forum: General Help
---

### Post by romeyde on 2009-01-07
I stupidly picked up a PCTV HD Pro Stick thinking it was supported.  I was planning on using it to record OTA broadcasts.   After a few hours or struggling, I think I have it recognized at least but can't seem to get any further.   For example,  when trying to run 'tvtime', I get an error saying /dev/video0 doesn't exist (it doesn't).   

To my untrained eye, this looks good.  Anyone else working with one of these and Ubuntu 8.1?


[   27.896772] dib0700: loaded with support for 8 different device-types
[   27.896913] dvb-usb: found a 'Pinnacle PCTV HD Pro USB Stick' in cold state, will try to load a firmware
[   27.896916] firmware: requesting dvb-usb-dib0700-1.20.fw
[   27.930704] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.930729] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.329391] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   28.534544] dib0700: firmware started successfully.
[   29.036075] dvb-usb: found a 'Pinnacle PCTV HD Pro USB Stick' in warm state.
[   29.036131] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   29.036360] DVB: registering new adapter (Pinnacle PCTV HD Pro USB Stick)
[   29.631799] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   29.649589] xc5000 0-0064: creating new instance
[   29.650175] xc5000: Successfully identified at address 0x64
[   29.650177] xc5000: Firmware has not been loaded previously
[   29.650279] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/input/input7
[   29.676164] dvb-usb: schedule remote query interval to 50 msecs.
[   29.676169] dvb-usb: Pinnacle PCTV HD Pro USB Stick successfully initialized and connected.
[   29.676332] usbcore: registered new interface driver dvb_usb_dib0700
[   30.210428] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]

---

