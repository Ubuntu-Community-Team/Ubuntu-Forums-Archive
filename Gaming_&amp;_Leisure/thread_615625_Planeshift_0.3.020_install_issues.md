---
title: "Planeshift 0.3.020 install issues"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by gcrussell1 on 2007-11-17
I'm thinking about playing Planeshift, but I'm having trouble installing it: I downloaded and ran the .bin for 0.3.019 and it worked fine, but told me I needed to update. The updater's down, so I downloaded the .bin for 0.3.020 (the latest version) and tried to run it and got this message:```
sudo: PlaneShift_CBV0.3.020-x86.bin: command not found
```I tried running it through the GUI with a simple double click and it told me this:

[b]"PlaneShift_CBV0.3.020-x86.bin" cannot be opened
No application suitable for automatic installation is available for handling this kind of file.[/b]

The 0.3.019 installer was the same kind of file, and installed without trouble. I tried deleting the 0.3.020 installer and reDL-ing it (from a different mirror), and the issue continues. I'd try a bittorrent download, but I can't get through the Chinese firewall with bittorrent, so no dice there.

Any ideas?

---

### Post by gcrussell1 on 2007-11-18
It's been a day... bump...

---

### Post by karth on 2007-11-18
From the directory in which the .bin is:

Any trouble with +x flags?```
chmod +x PlaneShift_CBV0.3.020-x86.bin
```

Try running it with ```
sudo ./PlaneShift_CBV0.3.020-x86.bin
```

---

### Post by gcrussell1 on 2007-11-18
Wow... I kinda feel like an idiot, but I know I tried sudo before (the code I posted is an error message from the sudo command)... The chmod +x command gave no input, did it possibly change something? I'm sure I tried to run it from the directory it was in, and not the ~ directory... I'm not that dumb, am I? I can't be... I tried running it from the .bin shortcut and it didn't see it at all...

Regardless... it installed this time... so cheers!

---

