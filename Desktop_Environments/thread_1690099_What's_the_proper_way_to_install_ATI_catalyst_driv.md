---
title: "What's the proper way to install ATI catalyst drivers?"
date: 2011-02-17
forum: Desktop Environments
---

### Post by penn919 on 2011-02-17
I've been trying to install the ATI Catalyst_11.1 proprietary driver for the past two days unsuccessfully. I've been using the instructions in **[this]("http://www2.ati.com/relnotes/Catalyst_11.1_Linux_Installer.pdf")** pdf from AMD's website, but it really hasn't done me any good. Despite the fact that the installation wizard says the install completed, nothing changes once I reboot.

I read somewhere that it was possible to install it via the "Hardware Drivers" utility. Is that true? If so, how can I go about doing that.

At the moment I've got the "ATI fire gl" driver activated, but playing videos in fullscreen is painfully slow and I'm hoping AMD's proprietary driver can help.

btw, My system can run pretty much any video (HD or not) in fullscreen under Windows 7. I want the same to be true under Ubuntu.

System Specs:

Model: Acer Aspire T160
CPU: AMD Athlon 64 3800+ (Socket 939)
Mobo: FC51GM (Foxconn WinFast 6100K8MA-RS)
Bios: Pheonix Technologies R02-B1 (From Acer)
RAM: 4 GB (dual Channel)
GPU: PowerColor ATI RADEON HD 4550 (512MB)
HDD (1): 160 GB
HDD (2): 120 GB
Optical Drive: CD-RW\DVD-Rom Combo
Optical Drive: DVD+RW Drive
OS:Ubuntu 10.04 Lucid Lynx \ Windows 7 Home Premium 64-bit

---

### Post by mcduck on 2011-02-18
The Ati FireGL driver *is* the proprietary AMD driver.

---

### Post by penn919 on 2011-02-18
Really!? Then how come I still can't even play standard definition videos in full screen without choppiness? Also, i can't seem to enable desktop extra effects; I already tried Compiz, it doesn't work either.

---

### Post by coffeecat on 2011-02-18
> **penn919 said:**
> GPU: PowerColor ATI RADEON HD 4550 (512MB)

Did you try the default open source driver before you installed the proprietary one? I have a Radeon HD4350 card on this machine. I use the open source driver and a 1920x1200 24" monitor. I get good compiz effects and I can play HD videos without stuttering or lagging.

If you want to try the open source driver, the proprietary one can be tricky to uninstall and some packages for the OS drive need reinstalling. More here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by penn919 on 2011-02-19
I followed the instructions from the page you linked to, and I was able to successfully install the default open source driver, but it doesn't seem to perform any better. someone recommended that I use VLC, and it definitely improves video performance, but it doesn't really compare to the performance I get under Windows 7, and compiz still doesn't work.

I personally think it must be a compatibility issue with my Graphics card because I've tried just about everything. I've been getting more acquainted with Ubuntu and I was hoping to eventually use it as my primary OS but I'm not so sure about that if I can't straighten out this video thing.

I'm throwing in the towel for now, but thanks for the help anyways. I appreciate it.

---

