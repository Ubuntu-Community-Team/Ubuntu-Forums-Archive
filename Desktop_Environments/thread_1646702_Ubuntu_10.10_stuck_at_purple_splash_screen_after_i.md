---
title: "Ubuntu 10.10 stuck at purple splash screen after installation"
date: 2010-12-16
forum: Desktop Environments
---

### Post by yonyz on 2010-12-16
Hi,

Yesterday I booted into the Ubuntu 10.10 CD, and hit the Try Ubuntu button. Ubuntu booted fine from the CD, and after trying it for a few minutes, I decided to install it.

I already had (and still have) Windows 7 installed, so, using the Ubuntu Installer, I shrinked the C (system) partition of Windows by roughly 14 GBs. 10 of which used for Ubuntu itself, and the other 4 as Swap Area.

Installation went fine, and I was asked to reboot - and so I did. However, upon restarting, I was 'welcomed' by a stuck, purple splash screen. So I used Recovery Mode, and updated my Ubuntu. That didn't change anything.
I rebooted, started Ubuntu without the "splash quiet" commands, and instead used the "nomodeset" command. I logged in my Ubuntu user, and ran the StartX command. It didn't work, and I was given a few errors, including "no screen found", "Fatal server error", and something along the lines of "no NVIDIA module found (...,0)".

So what's wrong with the NVIDIA driver, really?
And how can I fix it?

I have an NVIDIA GTS 250 GPU.

---

### Post by yonyz on 2010-12-16
Ok, I'm following a short guide posted on YouTube. Since I have no access to the GUI (gnome) of ubuntu, I need to know how to add the right repositories, using the terminal,  in order to be able to download the nvidia-xconfig utility. Thanks.

---

### Post by yonyz on 2010-12-16
Alright, I was able to solve the problem by manually installing the latest NVIDIA driver using a few command lines. Thanks for anyone who checked the thread, hoping they would be able to help. :)

---

