---
title: "Grub/Boot Menu unusable/inaccessible at boot time on fresh install."
date: 2024-07-19
forum: Desktop Environments
---

### Post by dreadstorm2 on 2024-07-19
This is actually a kind of half-solved issue. But the last part is the relevant problem.

Upon first install co-existing with Windows 10, I found that when restarting, the system doesn't bring up the boot menu. First, I had to [ESC] to show what's going on during boot. No biggie. Once inside Linux, I installed the Grub Customizer app. Fixed the timeout from 0 to 15, and did a few other customizations, such as menu order, setting default, and so on. That much got solved.

Then there's that initial blank-out. I shouldn't have to hit [ESC] to see my boot menu, it should jump right into it, right? I'm assuming it's some sort of "splash" screen that's supposed to be there, but it's a blank, black screen. And when booting up, there is no boot menu, only that blank screen.

Now, the problem is, in order to even see anything prior to login, I still have to hit [ESC] a  number of times just to see the Grub loader menu. I'm almost sure once  is enough, but my natural impatience with badly configured things forces  me to keep pounding on it until I get to see what I want to see.

What I need to do is eliminate that blank, black screen so that the boot menu shows up for it's predefined time without having to hit any keys or anything. This is the only computer in the house (aside from tablets and phones) that uses Internet. Is there a fix for this badly-configured startup sequence, or will I end up having to wait for another release that puts an end to these unnecessary steps?

I installed Windlows 10, then Xubuntu on a later primary partition on the same SSD. Version 24 LTS. During install, I tried both methods, Installing along-side Windows, and manually assigning the partitions, both with the same result. Grub timeout=0 and the blank splash screen that hides everything.

Again, I fixed the timeout, I need to eliminate the blank-out that hides everything at startup.

---

### Post by oldfred on 2024-07-19
Not a fan of grub-customizer, it replaces grub's scripts with its own proxy files.
And the only way to remove it is a total reinstall of grub after removing all its files & grub files.

It is not really difficult to manually edit grub to make changes.

Change timout style setting, should give menu with every boot.
sudoedit /etc/default/grub
GRUB_TIMEOUT_STYLE=menu

I like to see boot process (it is in log file), not just logo.
Using arrow keys navigate to and delete quiet and splash
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT=""

If os-prober finds Windows, it should automatically show menu.
But if you did not install both systems in UEFI boot mode (or both in old BIOS mode), grub cannot boot both installs.
Also Windows must be working. Or fast startup/hibernation must be off, bitlocker off and chkdsk not required.
[/COLOR]
[/FONT]

---

### Post by yancek on 2024-07-20
You have not indicated whether both Xubuntu and windows actually boot when you get to the menu?  Answering the questions in post 2 should also be helpful. You may need to get and run boot repair to give enough information.

---

### Post by dreadstorm2 on 2024-07-22
I am sorry. I didn't want to seem a pest with this, so I allowed some time for responses.

Yes, when I machine-gun the [ESC] key, the boot menu shows up, and all the menu items are there, including Win10, and they all boot fine. (Yes, I needed to weak a few things in Win10 first.) But since this is a machine that uses internet for the whole house, other users aren't savvy enough to know some of these tricks so I have to eliminate the blank splash.

Out of habit, I debloated Win10, locked it down, and disabled <snip>, store, and other things before adding Linux into the mix. Hibernation is always disabled, sleep is always disabled, and a number of other "All Users" tweaks are added. The system uses an Asus Z77-A motherboard (before Asus went into the dumper), and SSDs are set to IDE mode, rather than AHCI. Fast Startup and SmartConnect are also disabled. (I find most "Smart" things are rather stupid, honestly.) Also, all sleep settings are disabled in BIOS - I don't let any of my machines go to sleep, they're either on and in use, or shut down. Other than these, all other BIOS settings are default from "Optimal" mode.

Unfortunately, I don't know enough about Linux to dig up any logs or such. Yet, anyway. I'm working on it though. :)  I'll go ahead and wipe the Linux install right away and put it back on, to eliminate the Grub Customizer. Best to start fresh anyway, with a warning like that about the tool.

---

### Post by yancek on 2024-07-23
I've not used Grub Customizer but have seen a lot of threads here by people who had problems after using it.  If you have only one OS (Xubuntu for example) you won't see a menu, that's default behavior but if you have windows and Xubuntu, you should see it.  Set the timeout to a few seconds which can be easily changed in the Grub files.  If you are not familiar with bootloaders and Grub specifically, you might bookmark the link below to the Grub online Manual which has all the information you will ever need about it.

 [https://www.gnu.org/software/grub/grub-documentation.html](https://www.gnu.org/software/grub/grub-documentation.html)

Another useful piece of software is the boot repair script which you can use to gather information on the system and boot files.  Best to use it to gather information which is explained at their site at the link below.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

