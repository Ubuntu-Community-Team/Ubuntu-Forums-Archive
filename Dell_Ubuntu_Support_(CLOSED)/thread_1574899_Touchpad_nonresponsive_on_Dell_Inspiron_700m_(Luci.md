---
title: "Touchpad nonresponsive on Dell Inspiron 700m (Lucid Lynx Ubuntu 10.04)"
date: 2010-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ionFreeman on 2010-09-14
So... a couple of weeks ago, my wife turned on her laptop, and the mouse pad did not respond. No button clicks, no mouse movement. The machine's been through a lot, and the hardware may just have failed, but I suspect some sort of software update.

Is there a test I can do to see which it is?

Is there something that's probably the problem? I found a [helpful looking post]("http://guide.ubuntuforums.org/showthread.php?t=737060&highlight=touchpad") about grub, but I don't have a menu.lst file.

---

### Post by mörgæs on 2010-09-15
How does the machine work, if you boot a live CD?

The thread mentioned is for Grub1, which used menu.lst. Ubuntu 10.04 uses Grub2.

---

### Post by ionFreeman on 2010-09-21
mörgæs,

It brings me back to [this problem]("http://ubuntuforums.org/showthread.php?t=1463294"). A sleep mode sort of state.

What would you have suggested I edit if it had fixed the problem?

Ion

---

### Post by ionFreeman on 2010-09-21
I did try some previous kernels. It's a 2.6.32-24-generic now. I tried 'em back to 2.6.31-20-generic. No dice.

It's possible the mousepad just gave out. Is there a way to test for that?

---

### Post by mörgæs on 2010-09-22
Then what about newer kernels? Ubuntu 10.10 (beta), for example:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You could also try an unrelated Linux like Slitaz or Fedora for cross-examining the touchpad.

---

### Post by ionFreeman on 2010-09-26
Thanks, mörgæs. I'd just like to know if the mousepad is working. I've reverted to kernels under which it worked, so I feel like I've ruled that out.

Do you have any other suggestions?

---

### Post by mörgæs on 2010-09-26
It is not only a matter of switching kernels, the best test is trying a completely different distro and/or release. Then you will know if the hardware is working.

---

