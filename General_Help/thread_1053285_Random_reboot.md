---
title: "Random reboot"
date: 2009-01-28
forum: General Help
---

### Post by MrSkate333 on 2009-01-28
I installed Ubuntu on my computer about a month ago, and now my computer is randomly rebooting.  Sometimes it'll happen after my computer has been on for hours or sometimes it will reboot before it even fully boots up.  There's no warning about the reboot either; nothing slows down and everything seems fine, then the screen goes black and the next thing I see is the splash screen when my computer boots up.  How can I fix this?

Thanks in advance.

---

### Post by khedron on 2009-01-28
Hmm, might not be a software problem but a hardware problem. Have you tried running Windows on that computer? If so, does the same thing happen?

I inherited an old computer (it had Win2000) and installed Linux on it. It would reboot whenever it had to use the CPU a lot for more than 10 mins. Turns out the CPU fan had failed and it was overheating.

---

### Post by MrSkate333 on 2009-01-28
I used to use Windows on this computer and I never had this problem.

---

### Post by khedron on 2009-01-28
With such an intermittent fault, it's hard to pinpoint any one point of failure. If it's a software problem, there might be something in the log.

Look through /var/log/syslog to see if there are any warnings or errors that look like they might have caused a crash. Try
```
tail /var/log/syslog
```and look for errors.

If you can't see anything, could you attach /var/log/syslog to a post straight after your computer has crashed like this?

Are there any possible external factors that could affect this? e.g. running a resource-heavy program (like in my case) or temperature changes in the house.

Trying to run Windows now (if it's still installed) might be helpful to see if it *is *a hardware failure. Kind of like a scientific control.

---

### Post by MrSkate333 on 2009-01-28
```
Jan 28 15:43:53 MAILBOXES kernel: [  388.125087] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 28 15:43:53 MAILBOXES kernel: [  388.125105] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan 28 15:43:53 MAILBOXES kernel: [  388.125107]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 28 15:43:53 MAILBOXES kernel: [  388.125109]          res 51/c0:c0:c0:c0:c0/00:00:00:00:00/c0 Emask 0x1 (device error)
Jan 28 15:43:53 MAILBOXES kernel: [  388.125114] ata2.00: status: { DRDY ERR }
Jan 28 15:43:53 MAILBOXES kernel: [  388.126168] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan 28 15:43:53 MAILBOXES kernel: [  388.126180] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan 28 15:43:53 MAILBOXES kernel: [  388.126182]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 28 15:43:53 MAILBOXES kernel: [  388.126184]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
Jan 28 15:43:53 MAILBOXES kernel: [  388.126188] ata2.00: status: { DRDY ERR }
Jan 28 15:43:53 MAILBOXES kernel: [  388.126212] ata2: soft resetting link
Jan 28 15:43:53 MAILBOXES kernel: [  388.304206] ata2.00: configured for PIO4
Jan 28 15:43:53 MAILBOXES kernel: [  388.304241] ata2: EH complete
```

I don't know if there's really anything in there, but I believe that is about when my computer last rebooted.

The temperature in my house is fairly moderate, and as I stated before, my computer will restart before it even fully boots up again, so I doubt it has anything to do with a resource-heavy program.  I unfortunately don't have windows on this computer anymore.

---

### Post by MrSkate333 on 2009-01-28
```
ray@MAILBOXES:~$ tail /var/sys/syslog
tail: cannot open `/var/sys/syslog' for reading: No such file or directory
ray@MAILBOXES:~$ tail /var/log/syslog
Jan 28 16:33:10 MAILBOXES pulseaudio[5560]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 28 16:33:10 MAILBOXES pulseaudio[5560]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 28 16:33:10 MAILBOXES pulseaudio[5560]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jan 28 16:33:12 MAILBOXES kernel: [   67.108011] eth0: no IPv6 routers present
Jan 28 16:33:12 MAILBOXES gnome-session[5433]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type' 
Jan 28 16:33:12 MAILBOXES gnome-session[5433]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop 
Jan 28 16:33:23 MAILBOXES gnome-session[5433]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan 28 16:33:23 MAILBOXES pulseaudio[5560]: module-x11-xsmp.c: X11 session manager not running.
Jan 28 16:33:23 MAILBOXES pulseaudio[5560]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 28 16:33:29 MAILBOXES python: hp-systray(init)[5686]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

```

That is my syslog right after my computer just rebooted.

---

### Post by khedron on 2009-01-28
There doesn't seem to be anything in what you have posted that could have caused the crash. 

To be honest, with no obvious cause of the crash, all I can give you is general advice.

Start by checking your system disk for errors:
```

sudo touch /forcefsck
sudo reboot

```
This will reboot your system and check the root harddrive, so save your work before you run this.

---

### Post by khedron on 2009-01-28
Weird, apparently other people might be experiencing the same thing.
[http://ubuntuforums.org/showthread.php?t=1053233](http://ubuntuforums.org/showthread.php?t=1053233)

It might be worth monitoring that thread to see if they find any solutions.

---

### Post by loudog23 on 2009-01-29
I have the same issue since update of ubuntu of yesterday. (the new kernel finishing by *-11)

I use GRUB for dual booting.
I cam back from work, so the computer was cold, so i boot, get into grub, select the latest version of ubuntu, when it gets to "STARTING UP..." the system reboot by itself. i've tried the *-11 with the fail-safe option (in grub) and same thing happens. 

If i start an older version of the kernel (*-9) it is ok. 
I've tried to start un windows XP, no problem.
The only thing i did not try is the memtest.

Thank guys.

---

### Post by skydiver|goose on 2009-01-29
I had a similar problem, it turned out to be over heating, I just had to set my laptop with the last 2" of the notebook hanging off the table so it could get more adequate ventilation

---

### Post by khedron on 2009-01-29
Ah, ok, so try an older kernel version. Do this:
```
sudo nano /boot/grub/menu.lst
```Change the line specifying the **default **number.

This number is the position of the option you want, minus one.
E.g. I have the following lines in my menu.lst:
```

title Windows 2000
...
title    Ubuntu 8.10, kernel 2.6.27-11-generic
...
title    Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
...
title    Ubuntu 8.10, kernel 2.6.27-9-generic
...
title    Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)

```At the moment I have **default 1** (to load the second option). Change this to **default 3**, or whatever it is on your system.

---

### Post by MrSkate333 on 2009-02-02
Thanks for all of the help, but nothing is working. The different kernels did nothing.  I'm beginning to think it might be a hardware problem because my computer sometimes restarts before ubuntu even boots up.

---

