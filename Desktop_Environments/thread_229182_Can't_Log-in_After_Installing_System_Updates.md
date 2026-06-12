---
title: "Can't Log-in After Installing System Updates"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Geomas on 2006-08-04
I booted up my computer today (4 August) and was soon informed by Ubuntu (6.06) that updates were available. After installing them, a notice said that a re-boot was necessary, so I re-booted.

However, after the re-boot, I can no longer log in using my user name and password. After entering my password, a couple lines flash by quickly on a black screen. The first line indicates the computer name and it ends  in "tty1". Then the log-in screen appears again.

The update I installed was very recent, as I use this computer regularly and promptly install updates as they become available.

What could be the cause of this problem, and how might I go about fixing it? I'm a novice when it comes to Linux, and I've only been using Ubuntu for about a month. Finding myself locked out of my computer has been a very unpleasant surprise. (I have re-booted in Windows so that I can post here.)

Some additional details:

A USB hard drive was attached to my computer at the time I re-booted (but my BIOS is not set to boot from a USB device).

I had the backup application Keep open and had set source and backup destinations, but was not running a backup when I re-booted the computer after installing system updates.

---

### Post by mlind on 2006-08-04
You need to disable splash screen to see where boot process fails. Usually problem like this is caused by upgrading a kernel, but not the graphic card's drivers which causes Xserver fail to start.

Can you login to tty1 using your username and password and trying command
```

sudo /etc/init.d/gdm restart

```

To disable splash sreen temporarily, hit ESC before computer starts executing Ubuntu (initrd image) on boot, then select most recent kernel from the list and press 'e' -key. Edit the kernel line and remove keyword 'splash', then press enter and 'b' for boot.

---

### Post by Geomas on 2006-08-04
mlind,

Thank you for your suggestion. Unfortunately, it did not solve the problem. To be sure, it does indeed appear that my computer is loading the Gnome Desktop Manager at startup. The default, brown-colored login screen appears, accompanied by the sound of a drumroll. I enter my user id and then my password, then a text screen very briefly appears on the screen, and then the brown login screen appears again, along with the drumroll sound. An infinite loop.

I also tried booting in "recovery mode," and at the bash I was able to login using my user id and password, so it's clear that those have not been wiped out.

What might I try next?

---

### Post by Geomas on 2006-08-04
More on this problem: I found that if I start the computer in recovery mode, and can enter the command line startx and it launches. But the following "Warning" screen appears:

> **Power Manager**
This program cannot start until you start the dbus *system* service.
It is **strongly recommended** that you reboot your compter [sic] after starting messagebus.

What does this mean? How does one start the dbus system service? And could this be related to my inability to login in the normal way?

---

### Post by mlind on 2006-08-04
Some update has definetly broken something..
Can you find anything from output of **dmesg** (command) or from /var/log/messages or ~/.xsession-errors ?

Press trl+Alt+F1 key combination, and login to tty1. Then use these commands and review if there's any errors related to gdm daemon dying/restarting
```

less ~/.xsession-errors
dmesg | less
less /var/log/messages

```

---

### Post by Geomas on 2006-08-04
mlind,

Before reading your latest reply, I was able to finally solve the problem, which arose from the fact (of which I was unaware) that the boot partition had become full. While logged in as root, I deleted some files, then rebooted, and Ubuntu started up normally. :)

Thank you for taking the time to help me troubleshoot this problem!

---

