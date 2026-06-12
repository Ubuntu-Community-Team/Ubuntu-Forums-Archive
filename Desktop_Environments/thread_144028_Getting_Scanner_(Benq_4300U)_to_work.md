---
title: "Getting Scanner (Benq 4300U) to work"
date: 2006-03-13
forum: Desktop Environments
---

### Post by sweeney276 on 2006-03-13
I have had my scanner, a Benq 4300u, running with earlier versions of Linux, particularly with MEPIS.  It ran "out of the box", but doesn't under Kubuntu.

I have Sane installed. Xsane and QuiteInsane as well as Kooka, but none of them can find it.

This scanner works with the snapscan backend, and I have followed the instructions on the snapscan webpage without success.  I guess this must be because libusb is the path the 2.6.x kernels are going down.

When I use sane-find-scanner, it finds the scanner but saneimage -L brings up a message that the correct firmware has to be installed.  I downloaded u222v067.bin which is the correct firmware file and amended snapscan.conf to recognise it.  Still no luck.

So I made sure the permissions allowed me to read/write files in /proc/bus/usb/ and this did no good.

The light comes on in the front of the scanner, so I know power is getting through and I have checked the usb cable (even changing it to make sure) but still it is not recognised by any software.

Thinking it might be a fault in my hardware, I connected my friend's scanner/printer (a HP pcs 1210) to my set up instead of my Benq 4300u, and it worked straight away, yet my Benq refuses to check itself on start up or be recognised by any software.

Anybody got any ideas?

---

### Post by z-vet on 2006-03-14
I had a Benq 3300U and it worked fine right after an install. Take a look at /etc/sane.d/snapscan.conf, you can find a list of supported scanners and your scanner listed there. Try to hotplug the scanner first: shutdown > unplug scanner > power up > shutdown > plug scanner back again > power up and see if it works.

---

### Post by sweeney276 on 2006-03-15
Yes, tried that too, without success.  I guess that there's two options: get another scanner or reinstall.

Thanks for your help, though :-(

---

### Post by z-vet on 2006-03-15
Try this:
Put your u222v067.bin file in /usr/local/lib/firmware and made it executable. Then edit /etc/sane.d/snapscan.conf, on line 5 you need to specify the path to your firmware file, e.g. 
```
firmware /usr/local/lib/firmware/u222v067.bin
```
Check if it works.

---

### Post by sweeney276 on 2006-03-15
Looked at my settings again and all OK but unchecked the line in snapcan.conf relating to firmware.

I then tried Kooka and it showed my scanner was recognised in the select scanner dialogue.  The light went on on my Benq 4300u, but when Kook's maid window came up it said there was no scanner.

I tried Quiteinsane and its scanner dialogue came up with the Benq 4300u shown but when I selected that, sane threw up an error massage which said something like "IO error when communicating with the device".

The next thing I'm going to do is run the live disc to see if the scanner is recognised "as-is".  Any further ideas?

---

### Post by sweeney276 on 2006-03-15
No, it didn't work.  On the live disk Kooka didn't recognise the scanner.  It looks as though I'm going to have to reinstall (something could have been altered on the way as z-vet said the Benq 4300u worked straight away).

Unless anyone's got any ideas, I'm going to reinstall my system tomorrow to see if that's true for me......

---

### Post by z-vet on 2006-03-15
It's very strange. Look at snapscan.conf: there is a list of scanners working "out of the box" and yours listed there. 
I've got it working once (on other distro) using [this page](http://snapscan.sourceforge.net), maybe try it too...

---

### Post by matchstich on 2006-12-15
ok,  i did something wrong, when i open xsane scanner manger i get failed to open device:snapscan:libusb:003:003: invalid argument

---

### Post by Bartje on 2007-02-02
I get the error message (translation to English, because my system is in Dutch):
Couldn't find device 'snapscan:libusb:001:003':
Error during communication 

Anybody knows what that means, and what to do about it?

---

### Post by dazzled on 2007-02-20
I posted on this once before. If you have a dual boot system with the Mirascan driver installed, plug in the scanner and boot into Windows. Immediately restart into Ubuntu. All will now be well.  Ubuntu/Xsane appears not to initialize the scanner correctly.

A poor solution, but I still know no other.

---

