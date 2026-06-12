---
title: "USB Device in VMware"
date: 2005-12-30
forum: General Help
---

### Post by andrewsawyer on 2005-12-30
I have VMware Workstation installed inside Ubuntu Breezy 64bit, and I have Windows XP SP2 running within VMware.

My only reason to have Windows is video chatting with my folks in the UK.  It's not possible in Ubuntu, but it is in Windows.

I have a Sony video camera with USB streaming.  It works fine in a windows only environment, and I have had a video chat with it before.  I am however having difficulty getting it to work (or any other USB storage/media device for that matter).

Clicking on VM at the top of VMware when Windows is loaded, and choosing Removable Devices >> USB Devices >> Sony USB Device gives me the following message:

```
A USB device is about to be unplugged from
the host and connected to this virtual
machine.  It will first be stopped to enable
safe removal.  With some devices, the host
may display the message "The device can
now be safely removed."
```

Followed by:

```
The existing driver (snd-usb-audio)
could not be sucessfully
disconnected. (Operation not
permitted)

Unload the driver manually, then try
again.
```

Followed by:

```
The existing driver (usb-storage)
could not be sucessfully
disconnected. (Operation not
permitted)

Unload the driver manually, then try
again.
```

Followed again by:

```
The existing driver (snd-usb-audio)
could not be sucessfully
disconnected. (Operation not
permitted)

Unload the driver manually, then try
again.
```

The thing is, I'm not sure how to disconnect it.  I have even tried keeping it turned off until Windows loads and then plugging it in and turning it on - same error.

I'm getting the same error with my digital camera, which should just appear as a removable drive in Windows.  I have even dismounted it from within Nautilus, yet it still says it can't mount it in Windows.

And help would be very much appreciated.  I would really like to have a video chat with my mum and dad sometime soon!

Andy

---

### Post by anil_robo on 2005-12-30
This is strange! I am using XP under vmware successfully to video-chat with my folks through yahoo messenger. The built-in mike in the USB camera doesn't work, but that's not a big problem as I can connect the jack mike to sound card. I'm also using my usb mouse, and usb digital still camera also with great ease with vmware!

---

### Post by andrewsawyer on 2005-12-30
I can use my USB mouse, which was plugged in and running durng setup, however I can't access my USB webcam/handycam, Panasonic digital camera, or USB canon printer.  None appear in Windows at all, however they do appear in VMware in the VM drop down.

I've tried running /usr/bin/vmware-config.pl again, but this hasn't helped.

---

### Post by andrewsawyer on 2005-12-30
Please note:

I have tried making a new Virtual Machine with Windows XP in it while the USB devices (webcam, printer and digital camera) were turned on.  This has not helped, and I am still faced with the same issue.

Any help would be much appreciated.

---

### Post by anil_robo on 2005-12-30
Go to windows control panel --> System--> Hardware--> Device manager. THere should be a button to "scan for hardware changes". CLick that button (sorry my windows knowledge is rusting these days). It should scan the entire system "virtual" hardware for any new hardware, and probably you can get your thing working.

If it fails, try loading the drivers on vmware windows, and then the hardware may start working!

Remember: VMWARE is an "emulation", it's not the real  thing! Most things should work, but if they don't - you can hardly do a thing except trying trying and trying! :)

---

### Post by andrewsawyer on 2005-12-31
Unfortunately still no joy :-(

By the look of it, Windows doesn't recognise it because VMware isn't showing it to Windows.  VMware is trying to disconnect it from Ubuntu before showing it to Windows, and Ubuntu isn't letting it go.  That's the way I read it anyway.

I've tried running VMware as both standard user and sudo.  Still no luck though.  I've also posted this same question to the VMTN Discussion Forum, however have yet to receive a reply.  I'll let you know the outcome if I get it sorted, but in the meantime any other suggestions would be much appreciated.

---

### Post by andrewsawyer on 2005-12-31
Got it!!!

sudo modprobe -r snd-usb-audio

well, sudo modprobe -r and then which ever device it tells you it can't access.  Incase anyone else has the same problem, don't sudo modprobe -r usbhid, as this is your mouse!

anil_robo - you said you had your webcam working - what is the refresh rate?  Mine seems awfully slow.  I'm assuming it is to do with the fact that it is an emulation.  Could you confirm?

Cheers,

Andy

---

### Post by anil_robo on 2005-12-31
[quote=andrewsawyer] anil_robo - you said you had your webcam working - what is the refresh rate?  Mine seems awfully slow.  I'm assuming it is to do with the fact that it is an emulation.  Could you confirm?[/quote]

I have counted the framerate using Yahoo Messenger video chat, and the frame rate is the **same** for real windows and vmware windows.

---

