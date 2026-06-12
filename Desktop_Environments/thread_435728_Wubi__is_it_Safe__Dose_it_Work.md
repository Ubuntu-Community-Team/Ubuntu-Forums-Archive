---
title: "Wubi  is it Safe ? Dose it Work ?"
date: 2007-05-07
forum: Desktop Environments
---

### Post by victorash on 2007-05-07
I want to run Ubuntu and Windows XP PRO. on my PC . I want to set  a Dual Boot system, I would like Like to hear from   anyone who is using  Wubi it sounds very simple to set up Dual Boot System. But is good as they claim ....

Thanks
Alan

---

### Post by Otkon on 2007-05-11
It actually was the only way I could get Ubuntu to cleanly install/start on My computer. With the Live CD I had graphics card and acpi/apic/lapic BIOS issues that led to a lot of frustrating trial and error and random guessing at boot menu options until "vga=771" did the trick. But I almost plotzed when Wubi zipped right through the boot up and installed in about 10 minutes with just minimal and standard input from Me.

Make sure you clean up and defrag your hard drive. I would suggest a couple of times. Once before you even download Wubi and the ISO, and again after you choose "Manually reboot later" when Wubi has installed. I downloaded the ubuntu-7.04-alternate-i386.iso separately ***before*** I ran Wubi because the transfer from inside Wubi was very slow. If you put Wubi and the ISO in the same temporary folder and run Wubi, it will automatically find the Ubuntu image and copy all it needs to the C:\wubi directory and Windows root. 

I have found that the majority of installation problems with Ubuntu start with a bad copy or a bad burn of the ISO. The rest are usually BIOS or video-card related. 

Also be careful of your BIOS boot sequence. I have a USB external hard-drive with no OS since it is for storage. At one point, after Ubuntu installed, I rebooted and got an ERROR LOADING OS message . I couldn't even get into the Windows XP or Ubuntu selection menu. I thought the system was hosed. But for some reason the BIOS had set the USB drive as FIRST BOOT and upon seeing it powered up with no OS, it stopped and didn't move to the next bootable drive in the sequence. I reordered it to boot off of (C:) first and everything worked again.

---

### Post by ultrageeky on 2007-05-29
I used Wubi to install Ubuntu without any difficulties. I've since changed the Wubi installation to Kubuntu and made many other changes to the original install without any major issues (bear in mind that I'm very new to Linux/Ubuntu and have had to learn via forums and Linux orientated websites).  The only issue I had with the installation was with the NVIDIA drivers but this seems to be usual with any Ubuntu install.

If you're a new Ubuntu user then I suggest the following programs:

[COLOR="Magenta"]Automatix2[/COLOR] - a GUI which eases the installation of important, commonly needed programs (if used to install NVIDIA driver and the GUI fails to load post restart use "automatix-nvidia-restore" to re-set to default VGA driver);

[COLOR="Magenta"]Easyubuntu[/COLOR] - a GUI which eases the installation of important, commonly needed programs;

[COLOR="Magenta"]Envy[/COLOR] - best program for installing NVIDIA and ATI VGA drivers (remember to use "envy -t" to activate the textual installer should the GUI fail to load upon restart);

[COLOR="Magenta"]VLC[/COLOR] - Good media player (better in Linux than in Windows (maybe MS deliberately cause faults for non-MS supported software)).

Hope this helps.

---

### Post by ultrageeky on 2008-03-23
To any new comers who read this page:

The latest version of Ubuntu/Kubuntu and family (version 8.04) has Wubi built into the Live CD so use the latest live CD instead of the standalone Wubi program.

Regards.

---

### Post by Mehashi on 2008-03-29
I used wubi successfully to install and run ubuntu 7.04 and was happily enjoying dual boot on one hard drive, but problems for me came upon the upgrade to 7.10. All went well and the upgrade finished but after a reboot, I had no internet, or network at all. 

I tried and tried but only having limited stuff printed off (and no net to get advice with) I had to use a live cd for a clean install of 7.10, now on its own hard-drive. 

Dual boot worked nicely for me both ways!
^_^

---

### Post by ultrageeky on 2008-04-01
I had problems with my network settings when I installed 7.10 from scratch.  I had to tinker with network settings and mnaually locate my prefered wifi signal.  I think the problem was inherent with 7.10, at least, according to its reviews.

---

