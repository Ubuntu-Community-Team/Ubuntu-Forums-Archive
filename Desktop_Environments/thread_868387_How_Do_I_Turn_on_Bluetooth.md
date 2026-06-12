---
title: "How Do I Turn on Bluetooth?"
date: 2008-07-23
forum: Desktop Environments
---

### Post by SuperMike on 2008-07-23
I have an Acer Extensa 4420 laptop and it's brand new. It may have only sat in a box at BestBuy perhaps 6, 7 months. It has this little button I'm supposed to click and my Bluetooth will supposedly be ready for me to integrate my Motorola ear piece with Ekiga or something, or perhaps sync up my contact information with my Blackberry. I have Ubuntu 8.04.

When I click my Bluetooth button on the laptop, it does nothing.

Where do I go from here?

---

### Post by NilsE on 2008-07-23
Right click on the bluetooth icon in the notification area and select preferences then make sure the services in the services tab that are needed for your devices are checked. Probably input and audio.  Then try to make the device themselves ready for connection and see if they connect on the main tab.  You may need to turn your bluetooth device off and on a few times.

---

### Post by SuperMike on 2008-07-23
My notification area doesn't have a Bluetooth icon, unfortunately. However, I found a Bluetooth icon in Preferences, clicked it, went to the second tab, and turned it on so that it shows the icon in Notification Area all the time. I see that the Audio and Input services are checked and running. The other two services: Network and Serial, are not. When I start those and then go back into the control panel again, these are unchecked again.

I do see a Bluetooth icon on my laptop with a button beside it. I slide it to the right (it's one of those push to the right and release buttons) and I see no difference in the light on that Bluetooth button, and no difference with the icon inside Ubuntu.

I assume this is a bug in Ubuntu 8.04? I'll go over to Launchpad to file it, I guess.

---

### Post by NilsE on 2008-07-24
OK, try these steps

1) Reboot and go into your bios settings and make sure all bluetooth things are turned on including what the switch does.

2) After reboot try the connection process again and see if it works.

3) If it still does not work, reboot again and immediately after coming up go into a terminal and enter 

dmesg

and see if there is any message returned about bluetooth such as errors or successes.  You can also post the dmesg output here and we can look at it.

By the way, when you slide the switch are you getting any popups indicating bluetooth is on and discoverable or turned off or anything like that.

---

### Post by SuperMike on 2008-07-24
1. This BIOS is pathetic. They give me no options for this. I'm almost wondering if there's an advanced BIOS I can get into if I press some special keystroke because the normal BIOS setup is primitive.

2. Reboot not necessary if I can't change the BIOS.

3. I'll test this dmesg later. I'll report back with the output.

4. Sliding switch -- no reaction with lights on laptop or on screen. Also changes no output from the lspci, lsusb, and many of the other commands I've been suggested to type.

---

### Post by SuperMike on 2008-07-24
> **NilsE said:**
> 

3) If it still does not work, reboot again and immediately after coming up go into a terminal and enter 

dmesg

and see if there is any message returned about bluetooth such as errors or successes.  You can also post the dmesg output here and we can look at it.

My dmesg is 549 lines, so I won't post here. However, I will show you what grepped output looks like on it:

# dmesg | grep -i blue
[  196.551475] Bluetooth: Core ver 2.11
[  196.551750] Bluetooth: HCI device and connection manager initialized
[  196.551754] Bluetooth: HCI socket layer initialized
[  196.579468] Bluetooth: L2CAP ver 2.9
[  196.579474] Bluetooth: L2CAP socket layer initialized
[  196.621375] Bluetooth: RFCOMM socket layer initialized
[  196.621390] Bluetooth: RFCOMM TTY layer initialized
[  196.621392] Bluetooth: RFCOMM ver 1.8

And if I snap the Bluetooth spring button to the right once (because that's how it works), and then check dmesg, I get this:

[  472.904173] atkbd.c: Unknown key pressed (translated set 2, code 0xd4 on isa0060/serio0).
[  472.904181] atkbd.c: Use 'setkeycodes e054 <keycode>' to make it known.
[  472.906799] atkbd.c: Unknown key released (translated set 2, code 0xd4 on isa0060/serio0).
[  472.906805] atkbd.c: Use 'setkeycodes e054 <keycode>' to make it known.

---

### Post by SuperMike on 2008-07-25
Latest: The reason the Acer Extensa 4420 laptop doesn't work with Bluetooth is because the hardware is not in there. The switch does nothing, evidently. People at least are reporting this on the web, but I have not confirmed it yet. The Acer website is pathetic, so I have no real way of knowing without waiting forever on the phone with their tech support.

---

