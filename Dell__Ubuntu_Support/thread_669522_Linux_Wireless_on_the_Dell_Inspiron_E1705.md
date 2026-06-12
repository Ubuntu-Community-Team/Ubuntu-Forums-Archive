---
title: "Linux Wireless on the Dell Inspiron E1705"
date: 2008-01-16
forum: Dell  Ubuntu Support
---

### Post by Tekuzo on 2008-01-16
I just got a new laptop to replace my compaq presario R4000, and this is a wonderful machine compared to my old one. So I made a 2nd partition to put linux on it. I put on my distro of choice, Fedora and i got everything but the wireless working pretty quickly. No matter what i did, I couldnt get the wireless card to work.

i do the old LSPCI command to see what my wifi card is, and the output was:
 0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

So, it was not the intel wireless card (which most of them seem to have come with), I didn't think that it was a big deal, cause i have gotten broadcom cards to work in linux before (the compaq had one, and i got it to work in both ubuntu and fedora core 5)

I go and do the usual things, I install network manager and dispatcher and wpa_supplicant

So then i go to the dell web page and i download the driver files for my laptop, i unzip them, and then i run the command "bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys" it gave me an error message about the firmware being version 4 and it wouldnt work, i don't remember the exact details. So i go to the bcm-fwcutter weg page, and i check out my card. It said that my card was supported, so i check out the site some more, and there is firmware for download on the site. I download that firmware and try again, still no luck.


If somebody could help me out i would really appriciate it, I am going to take this thing home and install ubuntu 7.10 on it and try again then check back here.

---

### Post by irish8890 on 2008-01-16
Follow directions from these threads:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Disable wireless security on your router when you try to connect.  I have been able to connect without WEP/WPA.  I have MAC filtering to only allow my laptop.  For security you can try:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Good Luck!

John

---

### Post by memoryproblems on 2008-01-17
If your on Gutsy (7.10) you might find some advice here: [https://help.ubuntu.com/community/WifDocsi/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifDocsi/Driver/bcm43xx/Gutsy), if not, you can navigate to your version from [https://help.ubuntu.com/community/WifDocsi/Driver/bcm43xx](https://help.ubuntu.com/community/WifDocsi/Driver/bcm43xx)

Basically, you can do this under restricted drivers manager, although my laptop, which utilizes the same wireless card, has been having some problems with this driver. I think there might be a problem with the kernel, because my keyboard will stop working whenever my wireless card is on, however my networking works like a charm, I just can't use my keyboard. (I wrote more info about this problem here: [http://ubuntuforums.org/showpost.php?p=4149950&postcount=4](http://ubuntuforums.org/showpost.php?p=4149950&postcount=4)

If anybody has any advice to the problem I've been having with the keyboard, I'd love to hear it, but Tekuzo, that should get your wireless card working, I don't know if you'll have keyboard problems like me, but if you do, at least know that your not alone. You might be able to try out NDISwrapper, I did that, however my connection wouldn't seem to persist, it would lose it easily and then refuse to reconnect. Maybe you'll have more luck with that then I did.

-Denis

---

### Post by Tekuzo on 2008-01-17
well what actually happened was i was installing ubuntu yesterday like i said i was going to. I boot up the OS for the first time after its been installed, and there is this little popup bubble in my system tray, it was saying that my GPU and my broadcom wireless card were not working properly, so i click the bubble, and it offers to go out and install the drivers for my 7900GS, i allow it to, and then i have working 3d. then i look at what it is sayinig about my broadcom card. It says that the bcm43xx driver is installed but i don't have firmware, so it asks me if it should use one on my hard drive (i had back luck with the actual dell driver) or if it should go out and download the wl_apsta-3.130.20.0.o driver. I allow it to, and it just started to work. It made me soo happy, so im probably going to copy all the contents of the /lib/firmware directory and throw the firmware that i need into a fedora 8 install to see if i can get it working.

---

