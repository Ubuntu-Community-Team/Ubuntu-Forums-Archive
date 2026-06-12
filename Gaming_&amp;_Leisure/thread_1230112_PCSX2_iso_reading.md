---
title: "PCSX2 iso reading"
date: 2009-08-03
forum: Gaming &amp; Leisure
---

### Post by gobberpooper on 2009-08-03
I'm having this annoying problem with PCSX2. I want to play Onimusha 3, but it's just way too slow! I heard that putting it on the hard drive makes it faster.
So first I used Brasero to create an ISO. I mounted it using the command
```
sudo mount -t iso9660 -o ro,loop=/dev/loop0 /home/shridhar/Desktop/Onimusha3.iso /media/iso/
```Then I configured the CDVD plugin to use the device /dev/loop0 thinking it would use the files in /media/iso/. But that didn't work. So I used Archive Mounter, but I don't know what device to configure PCSX2 to. I've tried gksudo-iso and the nautilus script to mount. Final Fantasy X is also slow but playable. It runs at ~40fps but with Onimusha I'm getting 2.5fps at the first scene. I haven't actually gotten to gameplay because the first part is slow and frustrating.

Can anybody help me with this? Or better can anybody give me a link to a better CDVD plugin that can use iso's? I used the .deb installer which didn't come with that one. Please no compiling stuff, I am absolutely clueless when it comes to that stuff. Thank you!

Edit:
Never mind I used ```
dd if=/dev/cdrom of=/home/shridhar/Desktop/Onimusha3.iso
``` which made the iso perfectly and then I found a plugin that let's me use ISOs from the hard drive. Unfortunately, Onimusha just doesn't seem to work out for me. Seems to keep going at 5FPS, even at gameplay. Can anybody fix that?

---

