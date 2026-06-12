---
title: "Problem with screen resolution on ubuntu installed through virtual box"
date: 2009-03-20
forum: Desktop Environments
---

### Post by smarty7 on 2009-03-20
I recently installed gusty on PC through Virtual Box, since the time of installation, i'm having problems with screen resolution.
The screen does not fit on my monitor, windows uses the resolution of 1280x720 but in ubuntu 7.10 it is not even in the option.
Please help!

---

### Post by Shazaam on 2009-03-20
Is it too big or too small? Have you installed the Guest Additions yet?

---

### Post by MissKitty on 2009-03-20
You need to install the drivers for your graphics card. Have you done that yet? I had the same problem when I first installed ubuntu. Once I got the drivers ubuntu changed the resolution by it's self. Ubuntu should notice your graphics card right away and give you driver options. What card do you have?

---

### Post by smarty7 on 2009-03-21
Ubuntu is showing at 1280x1024, windows shows on 1280x720.
So basically it soo big, i have scroll down to the bottom!

Actually as you know screen resolution dosen't matter that much but my problem specifically is that the whole ubuntu screen does not fit to my monitor.
In windows whenever you change your screen resolution, the height and width of the screen is not changed, only the effects appers on the display(like icons go bigger or smaller like that)
But here in ubuntu whenever i change the resolution, firstly it hardly changes from the default one, and if it changes, whoa! my ubuntu height and width are increased or decreased.

---

### Post by smarty7 on 2009-03-21
> **MissKitty said:**
> You need to install the drivers for your graphics card. Have you done that yet? I had the same problem when I first installed ubuntu. Once I got the drivers ubuntu changed the resolution by it's self. Ubuntu should notice your graphics card right away and give you driver options. What card do you have?

Sorry miss you're at the wrong post!
Being pellucid i just want to say that your answer is not correct.
Because i installed through [VIRTUALBOX]("http://techmania-shail.blogspot.com/2009/03/install-ubuntu-on-windows-xp-using.html"), in which you don't have to install any drivers, take headaches to start internet, etc.

---

### Post by smarty7 on 2009-03-24
Okey! now i've moved on to ubuntu 8.10 this problem is still there, but now the screen size is **_small_** 800x600
And in screen resolution there are only two options, first 800x600, 640x480.

---

### Post by dandnsmith on 2009-03-24
You do need the guest additions installed, then you can select the driver to use (which isn't the native driver for your graphics chipset).

There have been quite a few posting about this in the VirtualBox forums (a lot of the info given is to read the manual etc.) You should there find the name by which the driver goes (it eludes me for the moment, as I don't have a reference source handy)

---

