---
title: "Desktop Effects Could Not Be Enabled"
date: 2010-12-30
forum: Desktop Environments
---

### Post by Yomama1994 on 2010-12-30
Hey guys I'm running Ubuntu 10.10 using Oracle Virtual Box on a Toshiba Satelite L305 S5955, and when i try to use Docky on Ubuntu it says Composite has to be enabled and idk how to do this. Also when i try to change my Virtual Effects it says "Desktop effect could not be enabled." Please Help.

---

### Post by Krytarik on 2011-01-01
I don't know much about Virtual Box, but you can only enable desktop effects if you are able to enable hardware-acceleration for your video card/chip.

---

### Post by eddiemernard on 2011-01-02
Just to let you know I'm not in fact familiar with oracle virtual box so I cannot give a relative advice pertaining to that. You may want to look at this site [https://answers.launchpad.net/ubuntu/+question/16138](https://answers.launchpad.net/ubuntu/+question/16138) and hopefully it would help.

---

### Post by Kalimol on 2011-01-02
Most likely, Ubuntu isn't jiving with the graphics support in VirtualBox. I've never had any luck with the graphics support in VB, and I know they've improved somewhat, but it's equivalent to having a seriously stone age graphics card in the VM. Compiz (the Gnome compositor) needs more juice than that. I haven't played with the new graphics acceleration features, but they'll probably require some tweaking to get the guest OS to recognize them.

Not that it matters, but what's the host - Windows?

---

