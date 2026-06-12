---
title: "USB memory sticks not automounting in Gnome"
date: 2010-08-17
forum: Desktop Environments
---

### Post by bluedalmatian on 2010-08-17
I've got a strange problem that has just spontaneously appeared.

I'm running 10.04 and USB memory sticks suddenly stopped mounting on the desktop when plugged in.  It used to work, but then stopped.  The OS has definitely not had any upgrades applied because the machine in question doesn't have a network connection.

I did some investigating and found that according to dmesg the stick was being detected by the kernel and assigned to /dev/sdb

I could mount it from the command line and then access it from the command line but it wasn't showing in Gnome.

I then came across this:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

and checked the Nautilus config in gconf-editor as it describes

Sure enough the two checkboxes mentioned were ticked.  So I tried unticking them.  This now causes Gnome to mount the stick, even tho technically that's the opposite of what it should do!

But it only shows up in Places>Computer it doesn't put an icon on the desktop until you double click the memory stick icon in Places>Computer

Reticking the checkboxes in gconf-editor stops it mounting them all together again.

Any ideas what has gone wrong here?

Thanks

---

### Post by iluminameluna on 2011-05-27
> **bluedalmatian said:**
> I'm running 10.04 and USB memory sticks suddenly stopped mounting on the desktop when plugged in.  It used to work, but then stopped.  The OS has definitely not had any upgrades applied because the machine in question doesn't have a network connection.

Any ideas what has gone wrong here?

Thanks

Sorry to say I'm not providing any insight but thanking you for this post. I've been struggling w/ this question across forums but I've gotten NO replies. Almost as if all those gurus think it's such a DUMB problem, it's not worth addressing. Hate snobs but that's just how it appears to me.

The only diff between your sit & mine is that mine IS connected to the internet & I apply all relevant updates. Nothing's changed since you posted. USB sticks won't auto-mount & I'm not savvy enough to have found the post you did.

Here's hoping someone educates "us" plebes .. & again, thanks for your post!

---

### Post by matt_symes on 2011-05-27
Hi

Open a terminal and copy and paste this into it.

```
gconftool-2 -g /apps/nautilus/preferences/media_automount
```

If it returns false type

```
gconftool-2 -s -t boolean /apps/nautilus/preferences/media_automount true
```

Kind regards

---

### Post by iluminameluna on 2011-05-27
> **matt_symes said:**
> Hi

Open a terminal and copy and paste this into it.

```
gconftool-2 -g /apps/nautilus/preferences/media_automount
```

If it returns false type

```
gconftool-2 -s -t boolean /apps/nautilus/preferences/media_automount true
```

Kind regards

I did both this process & the one posted through a link by bluedalmatian   & neither worked. I have both my 16G microCruzer (SanDisk), 1 w/ the 10.04LTS .iso & the other w/ the Uni-USB-Installer.

At the moment I'm d/l Ubuntu-11.04-d.iso .

Is there any info I could provide that could help you help me?

I wouldn't really care but I have my neighbor/helper's little girls in this semi-rural community that I try to help by d/l material for their schoolwork. I save it to the USB drives, their mom takes it to print out & they do their homework .. Any help rec'd would be GREATLY appreciated!

---

### Post by matt_symes on 2011-05-27
Hi

Plug the USB device in, wait 10 seconds and then copy and paste (into a terminal)

```
dmesg | tail -n20
```

Post the results back here between code tags like this

[noparse]```
text from command
```[/noparse]

Kind regards

---

### Post by iluminameluna on 2011-05-27
:KS```
jessie@MumsieDesktop:~$ dmesg | tail -n20
[85106.313401] usb 4-2.2: USB disconnect, address 4
[85120.517873] usb 4-2.3: USB disconnect, address 3
[85558.484054] hub 4-2:1.0: unable to enumerate USB device on port 3
[85558.961941] usb 4-2.3: new full speed USB device using uhci_hcd and address 6
[85559.063899] usb 4-2.3: not running at top speed; connect to a high speed hub
[85559.092085] usb 4-2.3: configuration #1 chosen from 1 choice
[85559.112476] scsi7 : SCSI emulation for USB Mass Storage devices
[85559.119123] usb-storage: device found at 6
[85559.119127] usb-storage: waiting for device to settle before scanning
[85564.117724] usb-storage: device scan complete
[85564.120741] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.3  PQ: 0 ANSI: 2
[85564.129264] sd 7:0:0:0: Attached scsi generic sg3 type 0
[85564.145460] sd 7:0:0:0: [sdc] 2001888 512-byte logical blocks: (1.02 GB/977 MiB)
[85564.147697] sd 7:0:0:0: [sdc] Write Protect is off
[85564.147704] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[85564.147708] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[85564.163031] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[85564.163043]  sdc: sdc1
[85564.180696] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[85564.180708] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```


Btw, I apologize for sounding so offensive. Not my intention but I've been dealing w/ this problem since I installed this latest ver. of Ubuntu & my little girl has had a heck of a time trying to do her schoolwork w/out being able to print out her material. She has had to either sit here in my house copying stuff long-hand from the monitor (uncomfortable, physically & socially, for her) or her mom takes the links I give her & we all hope the cybercafe clerk can print out the right stuff .. I'm too sick to leave my house which is why all this is so complicated.

So, HUGE appreciation for your willingness to help!

---

### Post by iluminameluna on 2011-05-27
I went looking for "usb memory" & found a whole OTHER thread that relates to this question. Here's the solution, simple & elegant, that worked for me:

From Pregiopomo:

Re: unable to unmount usb drives when not root
> I've been having the same problem for a while, and I went for the solution posted here (modyfing the etc/fstub) then I finally went to test it with the laptop of a friend that recently installed Ubuntu 10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I realized that I had some more that probably were creating some conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the one installed by default):
 
usbmuxd
usbutils
libusbmuxd1
libusb-0.1-4
libusb-1.0-0
xserver-xorg-video-sisusb
libmtp8
usb-creator-gtk
usb-creator-common
libmobiledevice0
libgphoto2-port0
libgphoto2-2
media-player-info
libhpmud0
hpijs
hplip

- remove those packages that have been added by you or that may cause conflicts, in my case I had all the previous ones and I removed the following that I added months ago messing up with my laptop:

 
usbmount (yep it sound weird, but now is working properly in my laptop!)
pyton usb
usb creator
gnome pilot


I hope this example might help some people as I did received help reading this forum, this is not "THE WAY" you "HAVE TO" follow to solve this problem, but this is just a way that worked for me, and I think is worth to be shared

Did the above, found only usbmount in my case, chose to do a COMPLETE UNINSTALL & restarted my machine.

ALL GOOD! My girl's going to be SO happy her USB memory is usable again!

---

### Post by matt_symes on 2011-05-27
Hi

I'm very glad you found the solution.  :p

BTW, the output from dmesg was fine and as auto mounting was also set up in Nautilus,  we would have been moving more towards that area.

So i would also like to thank the poster of that thread as he has saved us both some time, head scratching and research.

Kind regards.

---

