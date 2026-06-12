---
title: "Ubuntu 7.10 on Dell Vostro 1000"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by mara9ato on 2008-02-03
Since [this post]("http://ubuntuforums.org/showthread.php?t=628213") didn't apply to my own system, I've decided to share my own flawless way to get Ubuntu 7.10 up and running decently on my Dell Vostro 1000:

1) Boot the system with the ethernet adapter properly wired to a working Internet router with DHCP service and the Gutsy Gibbon CD in the drive. Install accordingly;

2) As soon as you log in, open the terminal and type:

```
sudo nano /etc/usplash.conf
```

Change the line which says:

```
yres=1024
```

to:

```
yres=800
```

Then type:

```
sudo update-initramfs -u
```

3) Follow the Update Manager's instructions to update your system. Reboot after the process is complete;

4) Go to System / Administration / Restricted Drivers Manager and enable the ATI accelerated graphics driver. Reboot;

5) Go back to the Restricted Drivers Manager and enable the Firmware for Broadcom 43xx chipset family. Make sure you download the suggested file from the Internet when prompted. Click on the network applet left to the sound volume applet and you shall see any available wireless networks available, as well as the signal quality. Click on it to activate it;

That's it. Now you have a fast and working video adapter, working wireless connection and a fast and working boot splash.

What does not work: The bright adjustment function keys (you should adjust it at boot time, while in grub) and the Visual Effects. I strongly don't recommend installing xserver-xgl to get the effects to work, because although it does this job, it breaks the keyboard layout (no problem if yours is a US keyboard or if you reconfigure it on Gnome) and most annoying, it breaks your touch pad, missing the advanced settings. After all, effects are cool, but what you need is a useful system.

Good luck!

---

### Post by borahshadow on 2008-02-12
Hey is there anything that does not work for you? I'm thinking about buying this laptop and was curious. How well does suspend and hibernate work. Is the network reliable? Did you ever get the brightness keys working? Thanks

---

### Post by mara9ato on 2008-02-12
This is a fine system. But hibernation and suspend doesn't work. The wireless network also doesn't work if you go far away from your access point. This seems to be a problem with all systems with the Broadcomm wireless adapter (default on most Dells). Also, the brightness function doesn't work after BIOS boot time. You also won't get visual effects unless you don't mind using the touchpad's tapping enabled. I have moved back to Windows XP because I really can't stay a few meters close to the access point all the time, I and need Internet connection from my bedroom. I would definitely not buy another PC though, because I really love this one. I hope they get it right with the wireless drivers as well as the xgl stuff soon so I can try Ubuntu on it again. I'm currently running a clean installation of Debian in Microsoft Virtual PC for my Linux needs. Cheers and good luck!

---

### Post by borahshadow on 2008-02-13
ok thanks

---

### Post by unxplained on 2008-02-13
The firmware for the bcm43xx actually didn't work for me. I followed the guide using ndiswrapper on linux.dell.com. Check it out here: [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")

The brightness keys also don't work for me yet.

Also the visual effects are kinda fishy. I also chose not to have them yet until there are more stable drivers for the radeon xpress 1150 available.

---

### Post by borahshadow on 2008-02-13
I was just doing some research to see if I could help fix anything before I bought this laptop and found this [https://bugs.launchpad.net/ubuntu/+bug/159255]("https://bugs.launchpad.net/ubuntu/+bug/159255") If somebody could test it the bug report said it works. Hope it helps

---

### Post by unxplained on 2008-02-22
> **borahshadow said:**
> I was just doing some research to see if I could help fix anything before I bought this laptop and found this [https://bugs.launchpad.net/ubuntu/+bug/159255]("https://bugs.launchpad.net/ubuntu/+bug/159255") If somebody could test it the bug report said it works. Hope it helps

I can confirm that it now works! Just replace the original files (after creating backups of course) with the ones "james" uploaded.

Brightness keys work like a charm now :)

---

### Post by feminaexlux on 2008-02-28
> **borahshadow said:**
> I was just doing some research to see if I could help fix anything before I bought this laptop and found this [https://bugs.launchpad.net/ubuntu/+bug/159255]("https://bugs.launchpad.net/ubuntu/+bug/159255") If somebody could test it the bug report said it works. Hope it helps

Works for me too. I have been looking for this for a long time!

---

### Post by borahshadow on 2008-03-13
Hi again
Well I bought this laptop recently and have finally got everything working. I started out with hardy to see how it works. Unfortunately even with the newest video driver suspend works but resume does not. There were a few other bugs with hardy so I decided to come to gutsy. However the brightness keys work out of the box in hardy.

Anyway I installed gutsy and got all the updates done and then had to quit for the night. The next day I tried to boot up and something had borked my GRUB and it was giving me a file not found error. I just had to reinstall errr. Once I reinstalled and got a few things set up the way I like them I tried to get my wireless working. I didn't even have an option in my restricted drivers manager for my NIC so I was forced to go the ndiswrapper route. The guide said to get the latest driver from dell for your laptop so I did that but it didn't work. I tried the one in the guide but it didn't work I tried changing ndiswrapper versions but I finally found [This Post]("http://ubuntuforums.org/showpost.php?p=4143330&postcount=3")and used the driver that JamesGu said to and it worked. :)

Wow sorry to be kinda long winded. Do any of you know what wireless card is in your Vostro? Mine is a 1395 which I suspect that dell used to ship the 1390 which is maybe why none of the ways that worked for the rest of you guys worked for me.

Good to see the brightness fix worked for you guys it worked for me too.

---

### Post by tastefulasever on 2008-05-28
For those who want the copy and paste version:

Open a terminal, copy and paste this all at once.

```
wget http://launchpadlibrarian.net/11081245/video_brightnessdown.sh && wget http://launchpadlibrarian.net/11085094/video_brightnessup.sh && sudo chmod +x video_brightnessdown.sh && sudo chmod +x video_brightnessup.sh && sudo chown root:root video_brightnessdown.sh && sudo chown root:root video_brightnessup.sh && sudo mv /etc/acpi/video_brightnessdown.sh /etc/acpi/video_brightnessdown.sh.bak && sudo mv /etc/acpi/video_brightnessup.sh /etc/acpi/video_brightnessup.sh.bak && sudo mv video_brightnessdown.sh /etc/acpi/video_brightnessdown.sh && sudo mv video_brightnessup.sh /etc/acpi/video_brightnessup.sh
```

This downloads the new scripts, makes them executable, changes their ownership to root, makes backups of the old scripts, and copies the new ones in their place.  Sorry it's not elegant, but this will get it done fast.

---

### Post by borahshadow on 2008-05-28
Wow that is a simple work saver. BTW I thought I'd mention that suspend/resume and hibernate work mostly flawlessly in Hardy. There is the occasional hick up but it works 100% better than not at all :)

---

