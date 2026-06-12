---
title: "virtualbox unable to detect USB ports"
date: 2011-08-13
forum: Desktop Environments
---

### Post by fidelandche on 2011-08-13
Hi all,

I am running 11.04 with a dual boot of vista. I am also running virtualbox (downloaded from oracles site) I installed the extension pack from their website, I have added a new filter and I am in the user group but still virtualbox will not see the usb ports or the device plugged in. The reason for running virtualbox is if I can get the usb to work, I will then remove vista completely from my system and just virtualbox for the only two programmes that do not work in Ubuntu.

So any advice on getting the usb to work would be great.

Cheers

Andy

---

### Post by haqking on 2011-08-13
> **fidelandche said:**
> Hi all,

I am running 11.04 with a dual boot of vista. I am also running virtualbox (downloaded from oracles site) I installed the extension pack from their website, I have added a new filter and I am in the user group but still virtualbox will not see the usb ports or the device plugged in. The reason for running virtualbox is if I can get the usb to work, I will then remove vista completely from my system and just virtualbox for the only two programmes that do not work in Ubuntu.

So any advice on getting the usb to work would be great.

Cheers

Andy


are you using devices menu to select USB device ?

and obvious would be is USB enabled from the VM settings.

---

### Post by fidelandche on 2011-08-13
> **haqking said:**
> are you using devices menu to select USB device ?

and obvious would be is USB enabled from the VM settings.

When I go into the settings menu the USB is enabled and when I go into devices there is no device to select.

---

### Post by haqking on 2011-08-13
> **fidelandche said:**
> When I go into the settings menu the USB is enabled and when I go into devices there is no device to select.


ok so to be clear, you have USB enabled in the VM settings.

The USB device is plugged in and detectable in your Host.  In your VM when up and runnin if you go to Devices menu and choose USB devices, there is nothing there ?

and from the USB icon at bottom of VM ?

---

### Post by fidelandche on 2011-08-13
> **haqking said:**
> ok so to be clear, you have USB enabled in the VM settings.

The USB device is plugged in and detectable in your Host.  In your VM when up and runnin if you go to Devices menu and choose USB devices, there is nothing there ?

and from the USB icon at bottom of VM ?

The SatNav is detectable in 11.04, when going into the devices menu there is nothing there at all to select and when you say USB enabled in the settings, am I right in thinking this is what you mean?

And the icon at the bottom of Virtualbox shows that there is no USB device plugged in

---

### Post by haqking on 2011-08-13
> **fidelandche said:**
> The SatNav is detectable in 11.04, when going into the devices menu there is nothing there at all to select and when you say USB enabled in the settings, am I right in thinking this is what you mean?

ok so yeah its enabled.

Can you screendump the VM devices menu also, i beleive you but helps if can be seen.

just press PrtScreen key and save it, that way you wont get the screen recorder dialog in your images ;-)

---

### Post by fidelandche on 2011-08-13
I would, but I appear to be unable to take a picture of the image. But when you go onto the device menu and click on USB all you get is just a little black line with nothing there to click, unlike the CD/DVD devices menu.

---

### Post by fidelandche on 2011-08-13
Well unsure of what happened, but the VB will now pick up the USB devices when plugged in. So that's sorted now on to the next issue I have.

Cheers

---

### Post by haqking on 2011-08-13
cool glad its solved

---

### Post by fafatheone on 2011-08-13
I had the same problem some time ago (and every time I did a clean install of ubuntu and VirtualBox).

The solution I found was to open 'Users and Groups' Settings, edit the group 'vboxusers' and add yourself to it, log out and back in.
Now USB devices show up in VirtualBox devices menu. Worked like a charm for me.

---

### Post by haqking on 2011-08-13
> **fafatheone said:**
> I had the same problem some time ago (and every time I did a clean install of ubuntu and VirtualBox).

The solution I found was to open 'Users and Groups' Settings, edit the group 'vboxusers' and add yourself to it, log out and back in.
Now USB devices show up in VirtualBox devices menu. Worked like a charm for me.

he already said in OP that he was in user group.

solved now anyways

---

