---
title: "Random failure to boot into X"
date: 2014-11-10
forum: Desktop Environments
---

### Post by sorceror171 on 2014-11-10
Sometimes, my Xubuntu system won't boot into X. Instead I just get a text-mode console login prompt. I can login, but 'startx' just fires up a black screen. If I can boot into X, though, things seem fine.

It's random and unpredictable. For a while I thought some update or another might have fixed it, but lately it's come back with a vengeance. Earlier today, I had to reboot five times before I got the graphical login prompt. This evening, only twice.

Xubuntu 14.04 (for now), Nvidia GF560Ti with Nvidia drivers, Core i7-2600K, 16GB RAM. Happened both when I was using pure standard disk drives, and after I moved the system partition to an SSD.

I'm not even quite sure what logs to look at. A recent .xession-errors looks like:

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (2855) terminated with status 1
```

Suggestions on what to look at?

---

### Post by kc1di on 2014-11-11
boot logs are kept in /var/log/boot.log
you can look at that file and it may hold a clue to what's causing x to crash. 
I would suspect that perhaps x is trying to be started before your graphics driver is being loaded.
but look a the log file and see if anything obvious appears there.
good Luck.

---

### Post by sorceror171 on 2014-11-13
Well, it hasn't happened again since then, but I will keep that in mind when the time comes. I don't think I'll have to wait too long. Thanks.

---

### Post by sorceror171 on 2015-02-07
> **sorceror171 said:**
> Well, it hasn't happened again since then, but I will keep that in mind when the time comes. I don't think I'll have to wait too long. Thanks.

The problem has returned with a vengeance. I cannot get X started with any kernel past 3.13.0-43-generic. 3.13.0-44-generic and 3.13.0-45-generic will not start up X, period.

There are only a few differences in boot.log:

From a good boot, there are the unique lines:
```
* Starting ACPI daemon                                                [ OK ]
* Starting OpenSSH server                                             [ OK ]
```

From a bad boot, the above lines are not present, but there are these entries:
```
* Starting Fix-up sensitive /proc filesystem entries        [ OK ]
* Stopping Fix-up sensitive /proc filesystem entries        [ OK ]
```

Looking at the kernel logs, a successful boot has the line:
```
nvidia 0000:01:00.0: irq 61 for MSI/MSI-X
```

...but no such line is present in the kernel logs from a bad boot. No other obvious errors.

And in the Xorg.0.log, from a bad boot, there's:
```
[     7.733] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[     7.733] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[     7.733] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[     7.733] (EE) NVIDIA(0):  *** Aborting ***
```

Does anyone have any idea what's going wrong, and how to fix it? Or at least how to diagnose it?

---

