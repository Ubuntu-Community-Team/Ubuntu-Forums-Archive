---
title: "Thunderbird Installation asks for Hoary CD then..."
date: 2005-05-13
forum: Desktop Environments
---

### Post by dumb-noob on 2005-05-13
I recently switched from warty to hoary and everything was going smoothly until I got to installing thunderbird....I guess this is where my lack of linux experience comes in and my stupidity shows through, but I can't for the life of me, get thunderbird installed.

While running the "sudo apt-get install mozilla-thunderbird" command, the terminal asks me to insert the hoary cd into the cdrom and press enter. So, I do as it asks, and the "update" will get to 99% then it will ask me for the disc and to press enter again. It does this repeatedly, and never will complete the process of installing the necessary components for thunderbird.

There was one other application that it was doing this same thing on, but I can't recall which one it was.

Has anyone else had similar problems? If so, any pointers on what I need to try next?

Thanks
SC

---

### Post by tread on 2005-05-13
1. sudo gedit /etc/apt/sources.list
2. Comment out the cd from the repository list
3. Fire up synaptic
4. Reload package information
5. Search and install Thunderbird

---

### Post by Segovia on 2005-05-13
[QUOTE=tread]1. sudo gedit /etc/apt/sources.list
2. Comment out the cd from the repository list
3. Fire up synaptic
4. Reload package information
5. Search and install Thunderbird[/QUOTE]
I was going to suggest that too.  Data on the CD may be corrupt somehow, it seems.  If you wish to do it all from within the Synaptic GUI:

1. Open Synaptic.
2. Click "Settings (Menu) > "Repositories".  A new window opens.
3. The top (normally) item on the list should be "CD Ubuntu 5.04 "Hoary Hedgehog"
4. Highlight that one and click the "Remove" button (right side of the window).
5. Click OK.

This of course will force Synaptic to get your packages from the Internet, instead of the CD-ROM.

---

### Post by dumb-noob on 2005-05-13
MUCH better now. 

Thank you both for the time to help me out,

SC

---

