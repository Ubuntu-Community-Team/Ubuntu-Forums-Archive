---
title: "Dell D630 with Feisty failing to boot"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by fergpm on 2007-06-16
I just purchased one of the new D630's from dell with the intent of loading Feisty as the 2nd operating system.  I insert the install CD and the initial splash screen shows up and it doesn't matter if I select the default or the graphics safe mode it errors out and goes to a BusyBox ash shell and gives the following error message.

/bin/sh: can't access tty: job control turned off

Then brings up a (initramfs) prompt.

What am I missing? How can I get this to work?

---

### Post by cnshzj007 on 2007-06-17
[SIZE="3"]I have the same laptop as you.
And I met the same problem as you.

Fortunately, I change the liveCD of U704 with alternative CD.
Then it works well during the install.
But after install, U704 can not start the gdm because that  the U704 can not detect the X3100 GPU and has no right driver in CD U704.

Luckily, we can enter into the recover model and apt-get update;apt-get dist-upgrade to the latest core 2.6.20-16-generic.
Key of the GPU problem is to apt-get install xserver-xorg-video-intel and to vim the /etc/X11/xorg.conf and change the [drive "intel"].

reboot, enjoy!
[/SIZE]

---

### Post by jayant on 2007-06-17
Thanks for the tip. It worked for me effortlessly after doing the update and intel thing!

---

### Post by fergpm on 2007-06-18
This worked GREAT as to getting my machine to boot into Xserver. Thanks!!!!  :D

---

### Post by jvalenzuela on 2007-06-19
The same equipment for me, but when I tried with alternate CD the result was:

hang during format of partitions (83%), in fact doing nothing.

I've tried with option: using all disk and lvm manager.

After these errors I've tried installing Wubi-7.04 from windows, but the installation hungs too.

Do you have some suggestion?

Thanks in advance.

---

### Post by jayant on 2007-06-19
> **jvalenzuela said:**
> The same equipment for me, but when I tried with alternate CD the result was:

hang during format of partitions (83%), in fact doing nothing.

I've tried with option: using all disk and lvm manager.

After these errors I've tried installing Wubi-7.04 from windows, but the installation hungs too.

Do you have some suggestion?

Thanks in advance.

I think it's because you may not have a connection to the internet. When your installation is at around 85% try pressing ctrl + alt + F4 or ctrl + alt + F5 ( i dont remember which one ( to get back to the original screen press ctrl + alt + F1 ) ) this will show you whats going on. If you see messages that say error resolving host. It means it's trying to connect to the internet and can not do so successfully. In my case I just skipped the network autodetect during install and entered the settings manually as in my home network the dns server isn't set up properly and so i pointed my manual settings to the opendns.com servers.

I am not sure if this is the problem. But if it fixes your problem I'll be glad.

---

### Post by jvalenzuela on 2007-06-21
Unfortunately, I've skipped the network configuration too.... Thanks anyway.

More info, Finally I could finish the Wubi installation. Curiosly the Wubi installer didn't create a home.virtual.disk file so the only thing I did was to copy another file, change the name and restart the installation.

I'm going to try this installation to be sure that all is running well and after that I'm going to try the normal one (perhaps using a external USB disk before remove all my windows info :)

Thanks again.

---

### Post by jvalenzuela on 2007-06-22
Here again...

After Dell support say to me that I must reinstall windows (due to controller error) I decide that was a good moment to try again Ubuntu on hard disk.

After update new bios firmware (A02) , try again with the results:

1)  Desktop disk - Hangs.
2) Alternate disk - Runs without problems.

Now I'm finnishing to install some little things like intel graphics drivers (thanks to cnshzj007) because when I activate Compiz the PC complete hangs, problems with installed java AWT and others....

---

### Post by susan_1890 on 2007-06-22
I'm pretty new to Linux and Ubuntu so I was hoping you could clarify a bit more for me. I installed using the alternate CD and ran the 3 apt-get commands you suggested. (Note to other newbies -- you have to type sudo apt-get ...).

However, I wasn't sure exactly where in xorg.conf I'm supposed to make a change. I tried changing the Section "Device", Identifier "Generic Video Card", Driver "vesa" to Driver "Intel" but that didn't work. Should I be changing something else?

Thanks!

---

### Post by susan_1890 on 2007-06-22
I figured it out. I had the right place, but I typed "Intel" instead of "intel".  Oops!

Anyway -- thanks for the tips -- it seems to be working fine.

---

### Post by jvalenzuela on 2007-06-25
After a long weekend, I can read with some time about "my" intel graphics problem...

First, it's general our X3100 graphics card is TOO new. The official intel driver doesn't include all new characteristics for 965GM chipset, theoretically we must update to the 2.0 drivers BUT this is for Xorg 7.3 and this is not OFFICIAL by now (planned date is August). Ubuntu developers are including this (and new driver) in the first alpha release of 7.10.....

I think that I'm going to wait for the first one of:

1) Xorg 7.3 finally released (dual screen, hot plug on second screen...)
2) Somebody on Intel release the 2.0 drivers for Feisty.

---

### Post by jice99 on 2007-06-30
This also worked for me on the D630 & I am a newbie as well.  To clarify for other newbies:

Install with alt CD, be sure to setup networking for the update to work later.  (needs internet access)
Boot into recovery mode, and use commands:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xserver-xorg-video-intel
vim /etc/X11/xorg.conf
(be sure you know how to use vi @ this point :)
 find Section "Device" with Identifier "Generic Video Card" & change Driver to "intel" (lowercase)
 save & reboot

Thanks all!

> **cnshzj007 said:**
> [SIZE="3"]I have the same laptop as you.
And I met the same problem as you.

Fortunately, I change the liveCD of U704 with alternative CD.
Then it works well during the install.
But after install, U704 can not start the gdm because that  the U704 can not detect the X3100 GPU and has no right driver in CD U704.

Luckily, we can enter into the recover model and apt-get update;apt-get dist-upgrade to the latest core 2.6.20-16-generic.
Key of the GPU problem is to apt-get install xserver-xorg-video-intel and to vim the /etc/X11/xorg.conf and change the [drive "intel"].

reboot, enjoy!
[/SIZE]

---

