---
title: "Kubuntu doesn't detect Audio CD"
date: 2008-12-18
forum: General Help
---

### Post by Moonfrost on 2008-12-18
I'm using Kubuntu 8.10 Intrepid Ibex with KDE 4.1.3 and it doesn't recognize my audio CDs, it detects pretty much everything else, including my backup DVDs and CDs but it doesn't detect audio CDs at all.

Does anybody know if there's a way to make it (KDE) detect Audio CDs? I'm using the "New Device Notifier" widget which as I already have said it detects everything else with no problems.

---

### Post by hivelocitydd on 2008-12-18
you hve to change te cd drive in the amarok settings
in amarok you can find it under settings->config amarok->engines->default device(Default device is /dev/cdrom)

try changing that to /dev/scd0 or /dev/scd1 (depending on how many drives you have)

as for dvd's 

Code:
sudo apt-get install vlc
vlc plays all my dvds just fine (as well as almost ne other video/music file i throw @ it)
then run vlc and open the device w/ the disk in it 

hope this helps

---

### Post by Moonfrost on 2008-12-18
> **hivelocitydd said:**
> you hve to change te cd drive in the amarok settings
in amarok you can find it under settings->config amarok->engines->default device(Default device is /dev/cdrom)

try changing that to /dev/scd0 or /dev/scd1 (depending on how many drives you have)

as for dvd's 

Code:
sudo apt-get install vlc
vlc plays all my dvds just fine (as well as almost ne other video/music file i throw @ it)
then run vlc and open the device w/ the disk in it 

hope this helps

Actually I already have vlc installed since I always used it (even on Windows), the "engines" option and many other options are gone from Amarok 2 which is what I'm using now. But for music CDs I usually use a simple program and I've tried using vlc like I always did, it works but it doesn't detect the CD automatically, I have to manually open vlc and select the option to play the disc.

I usually don't rip my CDs to my PC (for what really? my stereo is close), I only download music I don't have and when I buy the CD I delete that music from the computer as to not take space and have duplicates, which means I don't need to see a library or anything like that when I'm listening to an audio CD (I usually put a disc on the PC when I want to listen with my headphones and browse the internet or play a game at the same time).

---

### Post by maestrobwh1 on 2008-12-27
Same issue here... annoying as I can't use things like Soundkonverter...

---

