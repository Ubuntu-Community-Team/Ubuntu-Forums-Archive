---
title: "Setting up a CueCat barcode scanner"
date: 2005-12-07
forum: Desktop Environments
---

### Post by pr0fess0r on 2005-12-07
Hi
I have a CueCat barcode scanner (not the USB model, it's the one that plugs between the keyboard cable and the PC) Has anyone got one of these working? Any tips would be appreciated!
cheers
pr0fess0r

---

### Post by Rinzwind on 2005-12-07
Those scanners are cool :) :)


Here's a nice page: [http://tuxmobil.org/barcode_readers_unix.html](http://tuxmobil.org/barcode_readers_unix.html)
> **CueCat Driver**

The :Cue:Cat is a little barcode reader that RadioShack distributes for free with their new barcoded product catalog. It connects on a PS/2 keyboard, mouse, or USB port (directly for USB CueCats, or through a CueCat USB adapter with regular PS/2 CueCats) and sends codes when it scans a barcode successfully. This driver [http://opensource.lineo.com/cgi-bin/cvsweb/cuecat/](http://opensource.lineo.com/cgi-bin/cvsweb/cuecat/) watches scancodes on any of these ports and decodes the ones coming from the :Cue:Cat. When it decodes a barcode successfully, it sends it in human-readable form on /dev/scanners/cuecat. As well as a kernel driver patch, a utility called CueAct is included which can read barcodes from the CueCat driver and look up relevant information from the Internet.


Hmm the site with the driver is dead :(

edit:
something better:
[http://osiris.978.org/~brianr/cuecat/files/opensource.lineo.com/cuecat/](http://osiris.978.org/~brianr/cuecat/files/opensource.lineo.com/cuecat/)

and a driver here:
[http://osiris.978.org/~brianr/cuecat/files/opensource.lineo.com/cuecat/cuecat_driver/](http://osiris.978.org/~brianr/cuecat/files/opensource.lineo.com/cuecat/cuecat_driver/)

---

### Post by pr0fess0r on 2005-12-07
The driver download link doesnt work :(

---

### Post by Linuturk on 2006-06-13
[QUOTE=pr0fess0r]The driver download link doesnt work :([/QUOTE]

I found the driver via a quick google. If anyone wants it, email me:

linuturk AT gmail DOT com

[http://ubuntuforums.org/showthread.php?t=143421&highlight=cuecat](http://ubuntuforums.org/showthread.php?t=143421&highlight=cuecat) << here is a good thread to consolidate our issue.

The driver specifically states don't use the cuecat in Xserver. Is there anyway to get it to work?

---

### Post by LeslieL on 2006-08-20
I'm trying to get my old USB (not PS2) CueCat working on my Compaq NX7010 laptop under Dapper. I've googled and found a driver for kernel 2.4.21, but not for 2.6.15, which is what I'm running. Will the old driver work?

I can get input from the CueCat to show up in Alexandria when I scan an ISBN, but it's garbled. I can't get input to show up in a text editor or in the console. What do I need to do to use the CueCat?

---

### Post by daller on 2006-10-31
You should try the driver, though it's not for that specific kernel!

And please everyone, go and contribute your knowledge here:

[https://help.ubuntu.com/community/BarcodeReaders](https://help.ubuntu.com/community/BarcodeReaders)

---

### Post by terryeden on 2006-12-03
Has *anyone* got this working?  My PS/2 cuecat spits out the garbage in the console window, but it doesn't do anything even in applications which are meant to support cuecat (DVDProfiler, readerware etc).

Thanks

---

### Post by stargazer713 on 2007-02-14
Hi, I just started using Readerware with my CueCat. Also the program All My Movies. All my Movies has trouble with the CueCat but if you still haven't gotten the CueCat to work, you have to have your PS2 keyboard connected to the other end of the CueCat Cable with the center connector plugged into the back of your computer in the keyboard connector. The female end has to be terminated. If you have a USB keyboard I think I heard that Radio Shack has a PS2 termination. If you have a USB/PS2 keyboard still plug the PS2 into the end of the connector. 

My problem is using it on my laptop without a PS2 connection on my laptop. I bought a PS2 to USB adapter but I can't get it to work that way. I think it still needs that end termination but plugging in another keyboard makes the scanner scan things erratically. 

I hope this helps you.

---

### Post by paulperson on 2007-02-20
Hey, I just got the cuecat and it works, but it sends out jumbled letters. I searched outside and found some sites that tell you how to remove the encryption not through a driver but though a hardware hack. (I can do this and I am only 17 and did it with a compass and a small knife)
Can you tell me what model number you have? If you can tell me this, I can tell you how to remove the encryption.
For example my model is 68-1965

---

