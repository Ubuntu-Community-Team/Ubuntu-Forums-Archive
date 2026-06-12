---
title: "Wacom tablet not showing in Gimp"
date: 2006-09-19
forum: Desktop Environments
---

### Post by toykilla on 2006-09-19
I have 2 issues right now. I have a Wacom Graphire 4 tablet that I just installed. It is a bit jumpy. The curser does not move very far and when i pick it up to move it more, it jumps back a few inches. 

Second, under Gimp, I am getting "No extended input devices" when i try to configure them.

---

### Post by MetalMusicAddict on 2006-09-19
> **toykilla said:**
> I have 2 issues right now. I have a Wacom Graphire 4 tablet that I just installed. It is a bit jumpy. The curser does not move very far and when i pick it up to move it more, it jumps back a few inches. 

Second, under Gimp, I am getting "No extended input devices" when i try to configure them.
Do you run Compiz/XGL? A guide in my sig might help if you dont.

---

### Post by toykilla on 2006-09-20
thanks that worked.. kinda.. When i rebooted i found my moust # and event# of the pen tablet had changed..I had to go through the config again to get my mouse moving.

---

### Post by StevenYap on 2006-09-20
> **toykilla said:**
> thanks that worked.. kinda.. When i rebooted i found my moust # and event# of the pen tablet had changed..I had to go through the config again to get my mouse moving.

Did you install the package wacom-tools? It puts a udev rule that symlinks /dev/input/wacom to whatever event# the driver gets assigned.

---

### Post by MetalMusicAddict on 2006-09-20
> **StevenYap said:**
> Did you install the package wacom-tools? It puts a udev rule that symlinks /dev/input/wacom to whatever event# the driver gets assigned.
Yea. Install the Wacom-tools package. Im testing Edgy and gonna update my How-To to reflect using the wacom-tool package and Edgy.

---

### Post by toykilla on 2006-09-22
yes Wacom-tools was installed. But that wouldnt affect the mouse would it? I have zero mouse activity.

---

