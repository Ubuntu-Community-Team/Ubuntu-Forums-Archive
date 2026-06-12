---
title: "Persistant V8.10 on a USB working but....."
date: 2009-03-23
forum: General Help
---

### Post by muteXe on 2009-03-23
... gettting some weird messages on shutdown.

I used the "create bootable usb" option from the 8.10 live disc, I made it persistant, giving it another 2Gb for storage.  It all seems to work okay, but i get the following messages when i try to shut down:

```

[ 470.140153] usb 7-1: device descriptor read/64, error -71
[ 523.xxxxxx] usb 7-1: device descriptor read/64, error -71

```

where "xxxxxx" is some numbers which i didnt have time to write down.  I get about 4 of these lines, with the number in the brackets getting bigger each time.  Then a read/write error (which i didnt have time to write down again sorry), then it shuts down.

So the USB stick works, I've tested its persistancy by writing a few text files and seeing if they exist when i reboot, which they do.  I'm just curious about these error messages.  I've googled "device descriptot read/64" and they all point to USB ports not working.  They must be working because my changes remain from boot to boot, and i've also tried it on another machine at work today (i get the same messages as above with that machine as well).

Has anyone come across this kind of thing before?  As i said, it doesn't seem to be a show-stopper, i'm just curious as to what the errors are, plus I would like a clean shutdown.

Thanks in advance,

mute

---

