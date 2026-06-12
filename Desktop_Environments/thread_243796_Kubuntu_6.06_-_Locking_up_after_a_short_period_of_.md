---
title: "Kubuntu 6.06 - Locking up after a short period of inactivity?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Airjoe on 2006-08-25
My linux box has been on the fritz lately. I wasn't sure if it was the machine or the OS, but once I stopped getting the BIOS screen, I knew I had to tinker around with the box itself. 

I finally got everything working after about 3 hours continuous work, loaded up Kubuntu, logged in, and then went back to my Windows PC. I could connect to the linux box via SSH or through the website it hosts just fine. Around 15 minutes or slightly more later, I go to connect again, and I can't. So, I switch (phsyically, I don't have a KVM box) the monitor, keyboard, and mouse over to the linux box, and notice that I can't move the mouse or type. So, I do a reboot, and leave everything hooked into the linux box this time. Alright, fine, I can connect to the internet. I go and take a shower. I come back 15 minutes or so later, and can't move the mouse or type with the keyboard.

Does anyone have any idea of what's wrong or what could be causing this? Or even how to find out? 

Thanks so much!
Airjoe

---

### Post by Metacarpal on 2006-08-25
Theory:
Set your screen saver to blank screen/none, or to some really low-end type (like scrolling text).  Also, set your power management settings to Do Nothing across the board.

If you're having hardware difficulties (which not seeing your BIOS on boot would imply), then some features such as ACPI sleep modes, and possibly the 3D graphics handling needed for some screen savers, might be shot.

---

