---
title: "Multiple soundcard help in Ubuntu 8.04RC"
date: 2008-04-21
forum: Desktop Environments
---

### Post by worm1000 on 2008-04-21
HI all. 
Firstly if this message is off topic, could someone who may be able to assist reply to me privatly please? 
I'm having a problem where I have 2 soundcards 1 pci soundblaster audigy card and a usb logitech headset connected to the pc. 
My problem is When I boot ubuntu 8.04 rc, the usb headset always seems to be the default device for any kind of sound output. 
I went to a terminal window and typed in 
asoundconf list 
to list my sound devices in my pc and audigy appears for my sb audigy card. 
I then typed 
asoundconf set-default-card audigy 
I thought after doing this all sound would come out of my audigy but no this didn't help. 
I rebooted and this didn't make any difference. 
The fact my audigy card is being detected by ubuntu, is there something i'm missing here to get all sound output via the sb audigy and not the usb headset? 
Even after booting ubuntu with no usb headset connected no sound output is heard at all. 
I even went in to the volume control properties in gnome and changed the device to the audigy card no difference. 

Can the change I need to make be done within gnome?
Thanks for any assistance on this issue.

---

### Post by despuit on 2012-02-14
In terminal type 

less /proc/asound/modules

That will show you which soundcards occupy which slot and what're their names.

My output is
0 snd_au8830
1 snd_intel8x0

so it should look something like that.

Now identify which cards you don't wanna use and take their names.

In terminal now type

sudo gedit /etc/modprobe.d/alsa-base

Find the place where it says something like 
# Prevent abnormal drivers from grabbing index 0
and in the list below add
options snd_whateveryourcardnameswere index=-2

Since you have one card you want to blacklist you add two lines with different names then.

Now save /etc/modprobe.d/alsa-base and reboot the computer. It *should* now set the "wrong" sound card to slot -2 (thus, making them disabled) and the correct soundcard should thus grab slot 0 and work.

It has been suggested that instead of blacklisting the wrong one, one could manually assign slots in the same /etc/modprobe.d/alsa-base file (at the start of the file, where it says "# autoloader aliases" if you wish to switch between them.

---

