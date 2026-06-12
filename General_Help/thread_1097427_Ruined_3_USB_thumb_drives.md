---
title: "Ruined 3 USB thumb drives"
date: 2009-03-15
forum: General Help
---

### Post by mongo72 on 2009-03-15
I'm new to Ubuntu (8.10 server version with desktop installed on top of that).

I had three different USB thumb drives (two PQI U230 1GB, and a 512MB Memorex).  All were working fine on my windows machine and were usable by different windows machines.

I wanted to experiment with creating a runnable image from a USB drive, and plugged one in to the USB port on the computer.

No blinking light, no activity, no indication that it was active.  I removed it and plugged it in again.  No luck.

I then plugged it in to my windows machine and was told it was "not a recognized USB device".  No amount of activity could restore it. Dead.  Kaput.  Contents gone forever.

Same thing with USB thumb drives 2 and 3.  Can someone tell me what I did wrong?  What information can I provide in order to help you help me?

---

### Post by lindsay7 on 2009-03-16
If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

---

### Post by cybergalvez on 2009-03-16
> **mongo72 said:**
> I'm new to Ubuntu (8.10 server version with desktop installed on top of that).

I had three different USB thumb drives (two PQI U230 1GB, and a 512MB Memorex).  All were working fine on my windows machine and were usable by different windows machines.

I wanted to experiment with creating a runnable image from a USB drive, and plugged one in to the USB port on the computer.

No blinking light, no activity, no indication that it was active.  I removed it and plugged it in again.  No luck.

I then plugged it in to my windows machine and was told it was "not a recognized USB device".  No amount of activity could restore it. Dead.  Kaput.  Contents gone forever.

Same thing with USB thumb drives 2 and 3.  Can someone tell me what I did wrong?  What information can I provide in order to help you help me?

what happens if you run gparted, are the USB drives visible?,

---

### Post by mongo72 on 2009-03-16
I've tried to run the HP USB recovery tool, but I am not sure if it is that specific version.  Since the USB drive does not show up as a windows drive, the tool has nothing to reformat.

I'll check for that specific version and see if it helps.

Thank you!

---

### Post by mongo72 on 2009-03-16
> **cybergalvez said:**
> what happens if you run gparted, are the USB drives visible?,

I'll give gparted a try as soon as I can, probably later this evening.  

Thank you for giving me a starting point to try and diagnose the problem.

---

### Post by LegendofTom on 2009-03-16
I would assume you have an unformatted USB drive.  If you are going to boot an image, remember that you need a bootloader.

---

### Post by khelben1979 on 2009-03-16
Have you tried the usb stick with all your usb ports?

---

### Post by mongo72 on 2009-03-16
> **LegendofTom said:**
> I would assume you have an unformatted USB drive.  If you are going to boot an image, remember that you need a bootloader.

You are most likely correct, but what I don't understand is how it got unformatted simply by plugging it into the Ubuntu machine.

---

### Post by mongo72 on 2009-03-16
> **khelben1979 said:**
> Have you tried the usb stick with all your usb ports?

Yes, I have tried the USB sticks in multiple ports both on the Ubuntu machine as well as the Windows machine (to verify their status as really dead).  All with the same results.

Ruining a USB stick isn't the end of the world, though it is frustrating and will eventually become expensive.  

I am more interested in how they got ruined so I can both "not do that again" and eventually learn a little something.

Thanks for your interest and suggestions.

---

### Post by windhorn on 2009-03-16
I stuck a 4G USB stick into my new Ubuntu 8.10 installed machine and it showed a bunch of empty folders with random names.  The space available was listed as 64 MB.  The stick had U3 software on it -- could the problems you are having be related to this?

I haven't tried it on a Windows machine yet to see if it was damaged (there was no useful info on it fortunately).

---

### Post by mongo72 on 2009-03-16
> **windhorn said:**
> I stuck a 4G USB stick into my new Ubuntu 8.10 installed machine and it showed a bunch of empty folders with random names.  The space available was listed as 64 MB.  The stick had U3 software on it -- could the problems you are having be related to this?

I haven't tried it on a Windows machine yet to see if it was damaged (there was no useful info on it fortunately).

It doesn't sound like the exact problem, but it does seem as though it could be related.  It is almost that simply by plugging in a USB stick, something gets written to the device, corrupting the file system, or even the info on the device that is needed to announce itself.  

A bad file system I could live with, but the USB sticks aren't even recognized by Windows as a valid USB device any more.

Thanks everyone for all the suggestions.  When I do get this figured out, I'll be sure to include the details.

---

### Post by mongo72 on 2009-03-16
> **cybergalvez said:**
> what happens if you run gparted, are the USB drives visible?,

After plugging in one of the "dead" usb thumb drives, it does not show up in parted, only the two hard drives that are in the machine. :(

---

### Post by mongo72 on 2009-03-17
> **lindsay7 said:**
> If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

Unfortunately, the tool was not helpful in this case.  It only works when the USB thumb drives show up as a drive letter when inserted.  In this case, the USB thumb drives are so corrupted, they do not even show up.

---

### Post by aeiah on 2009-03-17
formatting the drives on the command line in linux usually does the trick for me. a lot of drives come with windows software on a small partition and it usually messes things up for linux and thus confuses windows when you go back to use it on them.

---

### Post by mongo72 on 2009-03-17
Thanks for the help everyone, but no joy on anything tried.

I don't really have an explanation for what happened to the USB thumb drives.  All I know is I'm not plugging in any USB storage media to that machine again.

I do appreciate all the help and suggestions.

---

### Post by Slim Odds on 2009-03-17
Did you try:
```
lsusb
```?

---

### Post by kuja on 2009-03-17
Immediately after plugging it in, look at the output of dmesg | tail. If linux recognizes it at all you'll see something here.

---

### Post by deepakbm on 2009-03-17
Mount manually This will help





[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by mixmaster on 2009-03-17
Well, I regularly use USB drives on linux boxes without these sort of problems, as I am sure do many other people, so there must be a specific reason why your setup is trashing the things.  This is not an attempt to apportion blame - I'm simply suggesting that some obscure combination of hardware/software/configuration is at play.

If you have another drive that you are willing to hazard, plug it in and see if you can get linux to recognise it before you do anything else.  Remember that it will not necessarily automount depending on how you have your system set up.  Also, I'm not sure about 8.10 server but on some earlier 'buntus the USB drive light did not come on.

Were all the thumb drives from the same manufacturer and if so who?
What filesystem did you have on the USB drive, DOS or NTFS?
When you removed the drive the first time, did you attempt to unmount it?

---

### Post by Octagonal on 2009-03-17
Is it possible the usb ports are connected to the firewire connectors on the motherboard and physically destroying each of the usb drives.

---

### Post by jacktar on 2009-03-17
As deepakbm suggested, mount the drive manually as they don't automount in Ubuntu server

---

### Post by alex2399 on 2009-03-17
I also have problems with USB 2.0 Flash drives. Have a Sandisk Cruzer U3 without the original software because I formatted it. When starting Ubuntu, and plugging it in it never works. The light on the USB stick flashes once, dims and nothing happens. Though actually the system tries to identify it or something but does not succeed. I circumvent this by doing the following in a terminal:
```
sudo rmmod ehci_hcd
```
This removes USB 2.0 functionality so reverts to a lower USB spec.
After this the drive works at low speed. After issuing this command:
```
sudo modprobe ehci_hcd
```
the drive is disconnected, identiefied and mounted at USB 2.0 speeds and functions as it should.
So try the first command, see if your USB sticks can be found somehwere, if it does, try the second command.

---

### Post by mongo72 on 2009-03-17
No, they are USB ports.  I have swapped the port I was using with the one a USB mouse was plugged into at an earlier suggestion to try different ports.

---

### Post by mongo72 on 2009-03-17
> **kuja said:**
> Immediately after plugging it in, look at the output of dmesg | tail. If linux recognizes it at all you'll see something here.

OK, after plugging in the USB drive, I see this message in dmesg:

usb 2-2: reset low speed USB device using uhci_hcd and address 12

---

### Post by halok on 2009-03-17
> **Octagonal said:**
> Is it possible the usb ports are connected to the firewire connectors on the motherboard and physically destroying each of the usb drives.

This could be possible, has the original poster checked this?

---

### Post by mongo72 on 2009-03-17
> **alex2399 said:**
> I also have problems with USB 2.0 Flash drives. Have a Sandisk Cruzer U3 without the original software because I formatted it. When starting Ubuntu, and plugging it in it never works. The light on the USB stick flashes once, dims and nothing happens. Though actually the system tries to identify it or something but does not succeed. I circumvent this by doing the following in a terminal:
```
sudo rmmod ehci_hcd
```
This removes USB 2.0 functionality so reverts to a lower USB spec.
After this the drive works at low speed. After issuing this command:
```
sudo modprobe ehci_hcd
```
the drive is disconnected, identiefied and mounted at USB 2.0 speeds and functions as it should.
So try the first command, see if your USB sticks can be found somehwere, if it does, try the second command.

I issued the first command, and saw these messages in dmesg after inserting the thumb drive:

[82671.982518] usb 1-2: new low speed USB device using uhci_hcd and address 16
[82672.230035] usb 1-2: new low speed USB device using uhci_hcd and address 17
[82672.480158] usb 1-2: new low speed USB device using uhci_hcd and address 18
[82672.900025] usb 1-2: device not accepting address 18, error -71
[82673.020021] usb 1-2: new low speed USB device using uhci_hcd and address 19
[82673.440032] usb 1-2: device not accepting address 19, error -71
[82673.440070] hub 1-0:1.0: unable to enumerate USB device on port 2
[82804.390022] usb 1-1: new full speed USB device using uhci_hcd and address 20
[82804.520024] usb 1-1: device descriptor read/64, error -71
[82804.770028] usb 1-1: device descriptor read/64, error -71
[82805.000031] usb 1-1: new full speed USB device using uhci_hcd and address 21
[82805.130019] usb 1-1: device descriptor read/64, error -71
[82805.490018] usb 1-1: new full speed USB device using uhci_hcd and address 22
[82805.910015] usb 1-1: device not accepting address 22, error -71
[82806.030022] usb 1-1: new low speed USB device using uhci_hcd and address 23
[82806.450017] usb 1-1: device not accepting address 23, error -71
[82806.450047] hub 1-0:1.0: unable to enumerate USB device on port 1

So from this, the OS is recognizing that there is a device in a USB port, it just doesn't know what to do with it. (or so I think...)


After running lsusb I see this: (no devices, other than the mouse):
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo fdisk -l only shows my two hard drives.  Since this is the first step to manually mounting the device, by identifying what device it is, I have nothing to manually mount.

gparted only shows the two hard drives.

I took a chance and plugged in a USB-based hard drive, one of those external jobs for backing up data.  It was immediately recognized, and I was able to force mount it (it said it was not cleanly unmounted from windows).

After the force mount, the drive shows up and everyone is happy.

I then repeated the process with the thumb drive, and nothing.

Somehow plugging in and unplugging the USB drive without properly unmounting them caused a corruption on the thumb drive itself.  I don't understand it, but there you go.

Thanks to everyone for all the help and suggestions.  I'll keep playing with it, and if anything helpful comes up, I'll be sure to update the thread.

Thank you, thank you, thank you!

---

### Post by mongo72 on 2009-03-17
> **halok said:**
> This could be possible, has the original poster checked this?

They are indeed, USB, as my mouse works in any of the ports in question.

---

### Post by mongo72 on 2009-12-23
> **halok said:**
> This could be possible, has the original poster checked this?

I wanted to follow up on this thread after so long an elapsed time in the hope that it helps someone else in need.  

Octagonal's post in this thread was on the correct path to getting this problem figured out, though the problem was not a USB port connected to a Firewire plug on the motherboard. The USB ports were indeed connected up to the USB plugs on the motherboard, but the cable was inserted in the wrong direction.

That is, what should have been plugged into the first pin, was actually plugged into the "last pin".  This caused the USB voltage to be "backwards" (positive was hooked up to the negative, etc) and this basically fried the thumb drives.

After turning around the connection on the motherboard, plugging in a USB device works just as it should.

Thanks for the help and I learned a very valuable lesson.

---

