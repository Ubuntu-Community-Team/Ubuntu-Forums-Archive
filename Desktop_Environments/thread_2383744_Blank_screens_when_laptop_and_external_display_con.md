---
title: "Blank screens when laptop and external display connected"
date: 2018-01-29
forum: Desktop Environments
---

### Post by roger_moore on 2018-01-29
Hi all

When the laptop is not connected to any external monitors grub loads, then the Xubuntu splash screen followed by the login screen. If I connect the external monitor after I log in I can use both monitors with the laptop screen as my primary. However when I connect the external monitor before boot, grub will only load and thereafter both screens will be blank with no splash screen or login screen. Also, the laptop is in dual boot with Windows 7 and that boots and works fine with the external monitor connected.

Intel microcode is installed and the laptop uses Intel GMA 3600 graphics. Xubuntu is 16.04.3.

I can't seem to figure out what the problem is. Any fixes?

---

### Post by roger_moore on 2018-01-31
_Update:_

I've since used Xubuntu on Virtualbox with dual virtual monitors and it works as expected so its not a Xubuntu problem. On further searches I found out that I have the Cedarview range of Intel products where the GPU was an outsourced design. It was quiet a bag of worms seeing that the CPU is capable of 64 bit but on the windows side only 32-bit drivers were released. The default GMA500 linux drivers is the only current drivers available for this GPU. 

A workaround to boot to the external larger monitor is to type "video=LVDS-1:d" just after quiet splash in grub. This disables the laptops internal screen and allows the external monitor to be used. 

Another option is to install the cedarview-drm drivers which requires Ubuntu 12.04. I haven't tried this as yet.

---

### Post by Autodave on 2018-01-31
What version of Ubuntu are you using?  I would hardly think that you want to go backwards to 12.04.  Surely youi aren't using something older than 12.04?

---

### Post by roger_moore on 2018-02-01
> **Autodave said:**
> What version of Ubuntu are you using?  I would hardly think that you want to go backwards to 12.04.  Surely youi aren't using something older than 12.04?

I had tried it with Ubuntu 12.04.5 LTS 32-bit to see if it made both my displays work. The cedarview drivers installed but didn't make a difference.

_Update:_

I have since tried using different monitors. I had first tried it with a HD LG monitor with VGA and then a HD Samsung with HDMI. Both times the above behavior was exhibited. 

However when I tried it with an old Acer square screen (max resolution 1280x1024) the laptop booted into grub then it showed the splash screen on the external monitor and also showed the login on the external monitor. The built in laptop screen's backlight was on and the mouse was able to move to the laptop's screen but no image was displayed. I logged in and started arandr to try and configure the laptop display but still no image displayed. If the external monitor remains detached until the laptop is booted then I can configure however I want.

---

### Post by roger_moore on 2018-02-02
There seems to be some development/patches in the non-LTS kernels.

[https://www.linuxquestions.org/questions/slackware-14/pc-only-boots-into-slackware64-current-with-specific-monitor-attached-4175606740/](https://www.linuxquestions.org/questions/slackware-14/pc-only-boots-into-slackware64-current-with-specific-monitor-attached-4175606740/)

[https://bugs.freedesktop.org/show_bug.cgi?id=78562](https://bugs.freedesktop.org/show_bug.cgi?id=78562)

---

