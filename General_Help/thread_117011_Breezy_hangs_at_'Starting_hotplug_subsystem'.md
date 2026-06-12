---
title: "Breezy hangs at 'Starting hotplug subsystem'"
date: 2006-01-14
forum: General Help
---

### Post by sanjuro on 2006-01-14
I am trying to install Breezy on a new PC. The specs are:

P4 LGA775 2.8 GHz
Intel D915GLVG
DDR400 512 MB x 2
....

There are no USB devices attached currently and I have also disabled the USB controller in BIOS. However, after the first reboot during install everything stops at 'Starting hotplug subsystem'.

I have tried this couple of times with different parameters like noapic nolapic acpi=off and also the noprobe usb thing. Same result.

Any ideas or I have to install Windoze on the system (no problems till now installing XP) ?

---

### Post by bernardfrancois on 2006-01-18
[QUOTE=sanjuro]Any ideas or I have to install Windoze on the system (no problems till now installing XP) ?[/QUOTE]

If you're that motivated to start using linux, you won't get very far. It will take some time to discover everything and start appreciating a powerful operating system.

Did you try waiting for a few minutes? I had a similar problem, I asked a friend to have a look at it, and he just waited :)

You can also try to disconnect most hardware (except what you need; screen, keyboard, mouse) and see if it solves anything.

Or you can just try a different distribution. But it's worth trying because Ubuntu is very good for linux-newbies as well.

---

### Post by CzarAlex on 2006-01-18
Do you have onboard sound? I had a smiliar problem. Startup would hang at the part..turns out my onboard sound card was not recognized. I had to go in to the bios, and disable it..of course then I had no sound until I installed a generic PCI sound card.

When you start up next, JUST as it starts to check the hotplug system, hit CTRL+C. That will bypass that step. Ya cant wait long or itll get stuck and hang. Do it as soon as ya see it on the screen and see if that works, if so, then i would try disabling the sound card.

---

### Post by sanjuro on 2006-01-26
@bernardfrancois: This is not my PC and I have a lot of other uses for my time than to try different distributions and options to make Ubuntu work on any one PC. FYI, I has been using it since Warty in my office and Breezy in my home and the installation was pretty smooth so far in all the cases.

@CzarAlex: That actually worked. But after bypassing that stage, the system threw 'segmentation fault'. For a few days we used Windoze on the system but I managed to rope in a more knowledgeble guy and he seems to have compiled a new kernel (or something, I don't know) and now Ubuntu runs just fine on the system. Thanks for the help !

---

