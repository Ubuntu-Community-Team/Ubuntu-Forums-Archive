---
title: "system chose to replace sound source"
date: 2008-02-10
forum: Desktop Environments
---

### Post by jaikat on 2008-02-10
hello

i've installed a satellite card (Twinhan visionplus 1020A)
worked fine until the next day when the tray icon for the volume applet showed a red stop sign over it and sound stopped working, when i click on the icon the system says that it could not find a sound card..

when i tried  lspci -v | grep Audio

i get

02:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

which is the satellite card.(my sound card is a Cmedia)

fortunately i have a built-in sound card which i had disabled from the bios. i went back and enabled the device and now i have sound, but i would really like to use the Cmedia because its a more capable card.

now that i have the ATI sound card (the one built-in) working, i tried  lspci -v | grep Audio

and now i get

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
02:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

it seems the satellite card audio capture drivers have replaced the Cmedia sound drivers, and the system doesn't seem to even know there is a Cmedia card in there anymore..

is there a way i can get things back to normal with the Cmedia?

I appreciate any help..

---

### Post by PmDematagoda on 2008-03-05
This thread is a duplicate of:-
[http://ubuntuforums.org/showthread.php?t=693364](http://ubuntuforums.org/showthread.php?t=693364)

This thread has been locked.

---

