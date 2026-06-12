---
title: "sound not working"
date: 2009-04-28
forum: General Help
---

### Post by mgreco_1988 on 2009-04-28
i just installed ubuntu 9.04 and i cant seem to get my sound to work for anything. Any suggestions?

---

### Post by Hellstudios on 2009-04-28
What sound card are you using?

---

### Post by mgreco_1988 on 2009-04-28
to be honest im not sure. how can i find that out?

---

### Post by b@sh_n3rd on 2009-04-28
What is the computer system you use? You can either find out via the Documentation of your system or look inside your box on the mainboard. There oughta be a chip somewhere around, close to the audio ports if you have a built-in sound card. The chip usually has it's name. This is how my systems show it but the name might also be printed on the board itself if it's an additional sound card (PCI/not built-in).

If you know your mainboard and it's got a built-in sound card, you can read the mainboard's manual to find out. This is if your system isn't branded.

---

### Post by mgreco_1988 on 2009-04-28
Intel Corporation 82801I (ICH9 Family) HD Audio Controller

is this what im looking for?

---

### Post by b@sh_n3rd on 2009-04-28
Ahuh. That's it.

**EDIT:** Hey, you don't seem to be the only one with this prob. Check out this thread. [http://ubuntuforums.org/showthread.php?t=912896](http://ubuntuforums.org/showthread.php?t=912896) in the meantime, I'll see if I can uproot more :D. Good luck.

**EDIT2:** Hi, I'm in the process of configuring my own stupid sound card which unfortunately someone thought oughtn't be automatically detected. Gah!!. Anyways, while exploring a file I found this. The ALSA driver for your card is "snd-hda-intel". Type: ```
sudo modprobe snd-hda-intel
```
and try to play some sound. If this works add the driver (snd-hda-intel) to the end of the "/etc/modules" file and reboot.

---

### Post by b@sh_n3rd on 2009-04-28
hey, i just came up with something myself...check this thread/link: [http://ubuntuforums.org/showthread.php?p=7169619#post7169619](http://ubuntuforums.org/showthread.php?p=7169619#post7169619)
Hope this helps :D. Remember that your sound driver is "snd-hda-intel".

---

