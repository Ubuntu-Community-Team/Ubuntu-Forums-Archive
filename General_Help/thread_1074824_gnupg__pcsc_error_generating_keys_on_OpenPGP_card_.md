---
title: "gnupg / pcsc error: generating keys on OpenPGP card failed"
date: 2009-02-19
forum: General Help
---

### Post by StefanX on 2009-02-19
I am using GnuPG on Ubuntu 8.10 and tried to create keys on a OpenPGP card. I followed this instruction [http://www.gnupg.org/howtos/card-howto/en/smartcard-howto-single.html#id2506175](http://www.gnupg.org/howtos/card-howto/en/smartcard-howto-single.html#id2506175) but the generation failed:

gpg: Bitte warten, der SchlÃ¼ssel wird erzeugt ... = Keys will be generated...
gpg: pcsc_transmit failed: not transacted (0x80100016)
gpg: apdu_send_simple(0) failed: general error
gpg: SchlÃ¼sselerzeugung fehlgeschlagen = key generation failed
gpg: key generation failed: Allgemeiner Fehler
SchlÃ¼sselerzeugung fehlgeschlagen: Allgemeiner Fehler = key generation failed: general error

I am pretty sure I did everything correct. The generation of keys succeeded using the same card at a Windows computer. Any help is really appreciated. Also please let me know how to "debug" this error if required.

In the following is an output of /var/log/messages

pcscd: hotplug_libhal.c:423:HPRemoveDevice() Removing USB device[0]: usb_device_8e6_3437_noserial_if0
pcscd: eventhandler.c:124:EHDestroyEventHandler() Stomping thread.
pcscd: ifdhandler.c:307:IFDHGetCapabilities() lun: 0, tag: 0xFB1
pcscd: eventhandler.c:137:EHDestroyEventHandler() Waiting polling thread
pcscd: eventhandler.c:496:EHStatusHandlerThread() Die
pcscd: eventhandler.c:161:EHDestroyEventHandler() Thread stomped.
pcscd: readerfactory.c:1133:RFUnInitializeReader() Attempting shutdown of Gemplus GemPC Twin 00 00.
pcscd: ifdhandler.c:226:IFDHCloseChannel() lun: 0
pcscd: ccid_usb.c:489:WriteUSB() usb_bulk_write(001/005): No such device
pcscd: readerfactory.c:994:RFUnloadReader() Unloading reader driver.
kernel: [ 5845.076174] usb 1-2.4: new full speed USB device using ehci_hcd and address 6
kernel: [ 5845.209544] usb 1-2.4: configuration #1 chosen from 1 choice
pcscd: hotplug_libhal.c:342:HPAddDevice() Adding USB device: usb_device_8e6_3437_noserial_if0
pcscd: readerfactory.c:1082:RFInitializeReader() Attempting startup of Gemplus GemPC Twin 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
pcscd: readerfactory.c:949:RFBindFunctions() Loading IFD Handler 3.0
pcscd: ifdhandler.c:1323:init_driver() Driver version: 1.3.8
pcscd: ifdhandler.c:1336:init_driver() LogLevel: 0x0003
pcscd: ifdhandler.c:1356:init_driver() DriverOptions: 0x0000
pcscd: ifdhandler.c:81:IFDHCreateChannelByName() lun: 0, device: usb:08e6/3437:libhal:/org/freedesktop/Hal/devices/usb_device_8e6_3437_noserial_if0
pcscd: ccid_usb.c:236:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
pcscd: ccid_usb.c:246:OpenUSBByName() ProductString: Generic CCID driver
pcscd: ccid_usb.c:252:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
pcscd: ccid_usb.c:408:OpenUSBByName() Found Vendor/Product: 08E6/3437 (Gemplus GemPC Twin)
pcscd: ccid_usb.c:410:OpenUSBByName() Using USB bus/device: 001/006
pcscd: ccid_usb.c:816:get_data_rates() declared: 10753 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 14337 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 15625 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 17204 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 20833 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 21505 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 23438 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 25806 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 28674 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 31250 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 32258 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 34409 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 39063 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 41667 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 43011 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 46875 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 52083 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 53763 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 57348 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 62500 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 64516 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 68817 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 71685 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 78125 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 83333 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 86022 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 93750 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 104167 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 107527 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 114695 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 125000 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 129032 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 143369 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 156250 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 166667 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 172043 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 215054 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 229391 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 250000 bps
pcscd: ccid_usb.c:816:get_data_rates() declared: 344086 bps
pcscd: ifdhandler.c:307:IFDHGetCapabilities() lun: 0, tag: 0xFB0
pcscd: readerfactory.c:267:RFAddReader() Using the pcscd polling thread
pcscd: ifdhandler.c:924:IFDHPowerICC() lun: 0, action: PowerUp
pcscd: Card ATR: 3B FA 13 00 FF 81 31 80 45 00 31 C1 73 C0 01 00 00 90 00 B1 
pcscd: ifdhandler.c:307:IFDHGetCapabilities() lun: 0, tag: 0xFAE
pcscd: ifdhandler.c:353:IFDHGetCapabilities() Reader supports 1 slot(s)
pcscd: prothandler.c:128:PHSetProtocol() Attempting PTS to T=1
pcscd: ifdhandler.c:488:IFDHSetProtocolParameters() lun: 0, protocol T=1
pcscd: ifdhandler.c:1451:extra_egt() Extra EGT patch applied
pcscd: ifdhandler.c:1035:IFDHTransmitToICC() lun: 0
last message repeated 14 times
last message repeated 4 times
pcscd: openct/proto-t1.c:487:t1_transceive() CT sent S-block with wtx=1
otto last message repeated 55 times
otto pcscd: commands.c:1236:CCID_Receive Card absent or mute
pcscd: openct/proto-t1.c:221:t1_transceive() fatal: transmit/receive failed
pcscd: ifdwrapper.c:750:IFDTransmit() Card not transacted: 612
pcscd: winscard.c:1630:SCardTransmit() Card not transacted: 0x80100016


Again, any help is really appreciated!

---

