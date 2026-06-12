---
title: "Wifi lost after reboot in Kubuntu"
date: 2006-01-18
forum: General Help
---

### Post by blaise69 on 2006-01-18
Hi guys,

I realise there are many posts about wireless connections in these forums, but I couldn't manage to find anything that represented my issue, so here goes...

I freshly installed Kubuntu yesterday (18th Jan 2006), I have a Dell Inspiron Laptop with a Wireless PCMCIA card, this has worked fine on Win 2K and Ubuntu.

After install of Kubuntu, the wireless card wasn't recognised as expected, so I followed the instructions from the Wiki for the 'NDiswrapper How to', I have the correct windows drivers and installed them without any trouble, I followed the guide through and everything went as expected until the last point ```
sudo gedit /etc/modules
```I assume this is for two reasons, firstly gedit is a Gnome application, so I tried the same command but with Kate instead, secondly the file doesn't seem to exists in my Kubuntu installation, I assumed that this was just the way things are with Kubuntu, but i didn't know what the Kubuntu version of the file was or where it would be held. :confused: 

Well anyway, I ingored this step this, my wireless was installed, and browsing my network and the internet was fine, until I rebooted.

Now My wireless card has no green lights on, as though it's not been installed, it's not recognised by any KDE GUI tools, like Network Settings, however ndiswrapper still claims that it's drivers are installed and that the hardware has been recognised, and lspci lists it correctly also.

does anyone have any suggestions how I can get it working again, and how i can make it persist after a reboot?

TIA

Cheers,

Blaise.

---

### Post by Choad on 2006-01-18
you will have to re do the following step 

sudo modprobe ndiswrapper

you will have an /etc/modules file. else something went seriously wrong. try 

sudo nano /etc/modules

thats what worked for me. then at the end of the file just add "ndiswrapper" (without the quotations) this means that it will do the modprobe at boot time

---

### Post by blaise69 on 2006-01-19
Thanks for the reply Choad, I followed your steps and that seemed to switch on  the card, however the connection is now disabled.

If I use the GUI to access the network settings, I can't seem to activate administration mode, it asks for my password, then just refreshes back to non-admin mode, even though my password is correct.

But I found a way using terminal to activate, 'sudo ifup wlan0'

I've not had to use this before, and I'm not sure why I need to now , why isn't this being done automatically?

Cheers,

Blaise.

---

### Post by sharke on 2006-01-19
Try in terminal "kdesu kcontrol" without the quotes this should give you the kde control center then set your connection .
Regards
Sharke

---

