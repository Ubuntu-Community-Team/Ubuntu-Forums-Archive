---
title: "Trouble with USB in xVM Windows"
date: 2009-02-18
forum: General Help
---

### Post by mugwump40 on 2009-02-18
I have a clean install of UBUNTU 8.10 and I installed the non-OSE version of SUN VirtualBox.  Then I installed Windows XP in the VirtualBox.  Let me just say that I've tried every virtualization tool I'm aware of (Wine, Windoors, Win4Lin, VMWorkstation, etc) and none of them are even in the same league as SUN xVM!  Everything worked great except I could not use any USB devices, even though they showed up as "Installed and working properly" in Windows Devices.  I feel pretty sure that UBUNTU isn't properly recognizing the USB devices.  I went into /etc/udev/rules.d/40-permissions.rules and added the GROUP+"usbusers" to the file. (SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664")  Now, when I open up the SUN xVM Virtual Manager and click on "settings", "USB", all my usb devices are showing up properly.  (They were greyed out before).  My problem now is that when I "Start" Windows XP, the initial black screen opens for a few milliseconds and then closes.  Here is the end part of the log:
00:06:34.253 ********************* End of statistics **********************
00:06:34.859 USB: Successfully reset device 'b596adf0[proxy 15a9:0004]'
00:06:35.258 USB: Successfully reset device 'b5972170[proxy 1668:6010]'
00:06:35.344 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
00:06:35.533 ERROR [COM]: aRC=VBOX_E_INVALID_VM_STATE (0x80bb0002) aIID={e3c6d4a1-a935-47ca-b16d-f9e9c496e53e} aComponent={Console} aText={Invalid machine state: 1)} aWarning=false, preserve=false
00:06:35.592 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={fd443ec1-0006-4f5b-9282-d72760a66916} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false

Anyone have any suggestions??  Thanks!

---

