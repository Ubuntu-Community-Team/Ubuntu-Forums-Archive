---
title: "X is broken after Hoary to Breezy update"
date: 2006-02-02
forum: Desktop Environments
---

### Post by kylenewton on 2006-02-02
Heyall.

I had Kubuntu Hoary installed on my laptop and finally decided I'd give it a try updating it to Breezy. So today during my AI class I booted into my Kubuntu partition and activated wlan0 'sudo dhclient wlan0'. I then updated the repositories from 'hoary' to 'breezy'. When that was done, I 'sudo apt-get clean' 'sudo apt-get update' and finally 'sudo apt-get dist-upgrade' which told me there was ~640mb to download and unpack.

The downloading finished in half an hour, but the unpackaging was taking forever (which might be expected). Well, class ended before the upgrade was complete. Now, this whole time I had a working KDE. Well, I left the laptop running and walked the 5 minutes to my next class. When I took my laptop out of my bag, plugged it back in and opened it up, it was waiting for me at tty1. I tried to go back to tty7 but alas, no luck.

I thought maybe a restart was in order, so I rebooted back into my Kubuntu partition (as opposed to my WinXP partition). Again, I was greeted by terminal 1. The last thing in startup that I see is "xmodmap: unable to open display ' ' " where ' ' are two single quotes.

I thought maybe my ndis drivers might have fudged a bit during the upgrade, so I plugged in directly to the school network, hoping to maybe run dist-upgrade again. But no such luck because 'sudo ifup eth0' answers with 'drop_privileges: user dhcp does not exist' and 'Failed to bring up eth0'. So I'm at a loss. I don't know what I might do next to get my laptop up and running again, short of transferring everything to a portable hard-drive and reinstalling off a CD.

I'm clay in your hands, please mold me.

---

### Post by glycoknob on 2006-02-02
Hallo,

login and go the /var/log/messages directory 
take a look at the output from Xorg.0.log and gdm or kdm log files lying around here. 
use less for viewing or tail -n 30 <file> for viewing the last chunk. 
take a look in the files, or post them here.

However, probably you updated your kernel as well and maybe your graphics card driver broke. if you have an older nvidia-card you could try installing nvida-glx-legacy instead of the nvidia-glx drivers. they won't support older cards up from the breezy release.

hth
martin

---

### Post by kylenewton on 2006-02-02
Thanks for the reply.

I can believe I broke the graphics drivers (ATI Radeon Mobility 9000) during the upgrade. However, I need to gain an internet connection again in order to download/fix the drivers, don't I? I downloaded the install and live CD for Kubuntu Breezy last night, maybe there's a way I can 'upgrade' using packages from the CD with apt-get?

---

