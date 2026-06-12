---
title: "Do I need to compile the kernel?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by gusjones on 2005-12-15
Hello, 

I a m trying to set up an avermedia DVB-T card on my Ubuntu system and came across what looked like some simple set-up instructions.

However, it looks like I'd need to recompile the Kernel. I have looked at the Ubuntu howtos, but they don't adequately explain how I include these modules into the kernel.

I am hoping someone will look at these posts and tell me how I can include the modules without compiling a new Kernel, as I would be entering uncharted territory.

Here is an excerpt from the following web link 

[http://www.blackbone.info/main/tutorials/aver761_tut.html](http://www.blackbone.info/main/tutorials/aver761_tut.html)


[COLOR="Red"]
######################################
# Setup Tutorial for Avermedia DVB-T 761 with Linux #
#####################################

Example on Debian 3.1 Sarge Standard Installation

First you have to compile a new kernel e.g. 2.6.13.2 because the installation
kernel is not working with the device.
It seems so but it is still not possible to run the card with the install
kernel.So , build your new kernel with the following modules:

Device Drivers
   - Multimedia Devices
      - Video For Linux (select)
         - BT848 Video for Linux (select)
      - Digital Video Broadcasting Devices
         - DVB For Linux
         - DVB Core Support (select)
            - Nebula/Pinnacle PCTV/Twinhan PCI Cards (select)
         - Customise DVB Frontends
            - Spase sp887x based (select)
   - Sound
      - ALSA
         - PCI Devices
            BT878 Audio Capture (select)

These are the few steps to detect the card by the kernel and load all needable
modules.[/COLOR]

Can anyone help? :confused:

---

