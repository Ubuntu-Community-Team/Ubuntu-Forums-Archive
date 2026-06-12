---
title: "LIRC help on Jaunty with Compro"
date: 2009-05-18
forum: General Help
---

### Post by ferdiel on 2009-05-18
Background:
I have a Compro VideoMate K100 remote and receiver (marketed as a Vista MCE remote with RC6 label at the back). The device registers in Vista as a HID device.
 
System information:
Os: Ubuntu 9.04
Kernel version: 2.6.28-11-generic
LIRC version: 0.8.4a
Hardware: Intel LittleFals 2 with 2GB memory
Remote: Compro videoMake K100 (USB Vista MCE remote)
 
Problem description:
I cannot get the remote to work on Ubuntu and maybe somebody can tel me if I'm wasting my time with the remote and the receiver. 
 
I installed LIRC and configured it by selecting 'Windows Media Center Remotes (new version Philips et al.)' from the list
 
lsusb lists the device as 'ID 185b:3082 Compro'
 
Here's the output from /var/log/messages:
 
May 18 06:32:30 wsfr004001002 kernel: [229151.428200] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
May 18 06:32:30 wsfr004001002 kernel: [229151.428206] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
May 18 06:32:30 wsfr004001002 kernel: [229151.430456] usbcore: registered new interface driver lirc_mceusb2
May 18 06:34:07 wsfr004001002 kernel: [229248.436748] intel_rng: FWH not detected
May 18 06:50:27 wsfr004001002 kernel: [230228.637147] intel_rng: FWH not detected
May 18 06:51:11 wsfr004001002 kernel: [230272.134320] usbcore: deregistering interface driver lirc_mceusb2
May 18 06:51:25 wsfr004001002 kernel: [230286.505670] 
May 18 06:51:25 wsfr004001002 kernel: [230286.505676] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.51 $
May 18 06:51:25 wsfr004001002 kernel: [230286.505681] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
May 18 06:51:25 wsfr004001002 kernel: [230286.624031] usb 1-2: reset high speed USB device using ehci_hcd and address 3
May 18 06:51:25 wsfr004001002 kernel: [230286.756488] lirc_dev: lirc_register_plugin: sample_rate: 0
May 18 06:51:25 wsfr004001002 kernel: [230286.756868] lirc_mceusb2[3]: Compro VideoMate IR on usb1:3
May 18 06:51:25 wsfr004001002 kernel: [230286.757205] usbcore: registered new interface driver lirc_mceusb2
May 18 07:13:31 wsfr004001002 -- MARK --
 
LIRC loads no problem without any errors 'sudo /etc/init.d/lirc restart'
 
Any help
 
Thanks - Ferdie
If I'm not wasting my time with this model, what should be done

---

### Post by eddy_crim on 2009-06-20
I have exactly the same remote and the same problem. It *must* be possible to get it to work because when i boot from the mythbuntu live cd it works fine (ish). However when i boot into Ubuntu it dosn't seem to like it. Going to work on it today so i may post a followup

---

### Post by darklord on 2009-06-21
I also had problems with mine remote (for jaunty - ubuntu 9.04), i found a partial fix for gnome-lirc-properties see message 4, this resolve a known bug - hope this helps but i still have to setup gnome-lirc-properties after rebooting.

[http://ubuntuforums.org/showthread.p...30#post7492230](http://ubuntuforums.org/showthread.p...30#post7492230)

---

### Post by frikkieh on 2010-07-09
I have the same remote and found some good install guides [here]("http://ubuntuforums.org/showthread.php?t=765454") and [here]("http://old.nabble.com/New-MCE-Remote-from-COMPRO---K100-td21110917.html").

However I still can't get this remote to work in Lycid Lynx (10.04).
lsusb gives shows a detected device:  
Bus 001 Device 002: ID 185b:3082 Compro 

With the "mode2" or "irw" commands, no characters are displayed (corresponding HEX output) when testing.

However, if the USB receiver is removed by physically unplugging it, the mode2 and irw program immediately exits to the command prompt.

Looks like some configuration needs to be done to map the key codes to an action, but this is developer stuff as I can gather from lirc.org.

Can anyone please advise me how to configure this?

Thanks, Frikkie

---

