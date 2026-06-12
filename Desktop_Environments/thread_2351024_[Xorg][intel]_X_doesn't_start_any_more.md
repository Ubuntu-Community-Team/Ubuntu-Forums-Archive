---
title: "[Xorg][intel] X doesn't start any more"
date: 2017-01-30
forum: Desktop Environments
---

### Post by olivier-godart-gmail on 2017-01-30
Hi,

I've got a strange issue that prevents my laptop from booting.

I made a lot of tests to try to figure it out but with no success.

My Ubuntu version is 16.04.1 LTS (Xenial Xerus), installed last month, and it did boot fine previously.
I didn't do anything fancy with the x server configuration.

It might be relevant to say that my whole system is installed on a very fast usb key, with root partition encrypted, and it boots from an initial root disk on the boot partition.

I've tried to boot using different kernels, to boot in single-user mode, and then run startx, to boot on different hardware, with no luck.

I can see a few crashes in the logs (zenity, bamfdaemon, unity-greater, xorg), but I don't know if it's a cause or a consequence of my issue.

One thing that may be strange, is that I've got 3 Xorg log files each time: Xorg.0.log, Xorg.1.log and Xorg.failsafe.log.
Does it mean that 3 concurrent instances of Xorg try to start at once? If it's the case, I don't have a clue why the additional instances are started (failsafe is probably because the normal instance fails, but the second instance, I don't know).

In the lightdm logs, I can see the error: ```
Fatal server error:
(EE) no screens found(EE)
```, which seems to be the cause of the trouble, but the laptop screen is there and works fine in text mode (and I tryed with the key in another laptop, so it's not a hardware problem). 

I'm attaching a few log files, but please let me know if something relevant is missing.

Thanks a lot if you can help!

---

### Post by DuckHook on 2017-01-31
> **olivier-godart-gmail said:**
> I've got a strange issue that prevents my laptop from booting.Your post is quite confusing. You state that your stick won't boot, yet you later state that you can read its encrypted logs, and use text mode. Are you saying it boots properly using a different machine?
> It might be relevant to say that my whole system is installed on a very fast usb key, with root partition encrypted, and it boots from an initial root disk on the boot partition.Again, please clarify&#8230; How can a root disk be on a boot partition? Partitions reside on disks; not the other way around. As for the boot partition, is it on the laptop HDD or does the stick have a separate boot partition?
> 
I've tried to boot using different kernels, to boot in single-user mode, and then run startx, to boot on different hardware, with no luck.How can you boot using different kernels or especially into single-user mode if your root partition is encrypted and you presumably can't boot from it? Are you booting another install and trying to chroot into your stick?
> I can see a few crashes in the logs (zenity, bamfdaemon, unity-greater, xorg), but I don't know if it's a cause or a consequence of my issue.Again, I don't understand how you can read your logs at all.
> One thing that may be strange, is that I've got 3 Xorg log files each time: Xorg.0.log, Xorg.1.log and Xorg.failsafe.log.Setting aside my other questions for the moment, this is entirely normal. Logs are rotated. The current log displaces the old one and the old one gets renamed to what you see.
> Does it mean that 3 concurrent instances of Xorg try to start at once?No> If it's the case, I don't have a clue why the additional instances are started (failsafe is probably because the normal instance fails, but the second instance, I don't know).Actually, the failsafe log is the one generated the last time you ran the system in failsafe mode.
> In the lightdm logs, I can see the error: ```
Fatal server error:
(EE) no screens found(EE)
```, which seems to be the cause of the trouble, but the laptop screen is there and works fine in text mode (and I tryed with the key in another laptop, so it's not a hardware problem).At this point, I'm assuming that you actually *can* boot, at least into another machine. In other words, you can boot after all, but cannot launch X.> I'm attaching a few log files, but please let me know if something relevant is missing.Your logs are massive and I didn't bother to read through them. Without going through them, I would suggest the following (based on the assumption that you actually have access to your OS):

[LIST=1]
[*]***Backup your important data.*** Your most critical task is protecting your data, so offload it onto your HDD or onto another USB drive. After that, the problem of reviving X is just a fringe benefit. The USB stick can be trashed for all you then care.
[*]Log in
[*]```
rm ~/.Xauthority
```
[*]reboot
[/LIST]
If that doesn't work, you can explore other options.

---

### Post by olivier-godart-gmail on 2017-02-01
Thanks for replying and sorry if my post was too confusing. I can boot but not launch X

The system boots, but when it tries to start the graphic mode, it fails, then I see the plymouth again, but the system doesn't respond any more (tried esc, ctrl-alt-f1, ... only the sysrq works).
The only way I can actually boot is in single-user mode, by editing the grub command.
> How can a root disk be on a boot partition? Partitions reside on disks;  not the other way around. As for the boot partition, is it on the laptop  HDD or does the stick have a separate boot partition?
Sorry I actually meant initial ramdisk (initrd). Boot and encrypted root are both on the usb key. (the idea being that it can be plugged in any computer, so I don't have to reinstall ubuntu each time I have a new employer)
This did work very well for more than a month, but then last week, I had a strange issue with evince that couldn't open any pdf, so I thought I would reboot, and then it failed.

I can read the logs by either booting another linux instance (on my old laptop), and mounting the disk, or by booting in single-user.
I know logs are rotated, but my Xorg.0.log and Xorg.1.log have timestamps that overlap, and I think Xorg log files are rotated to Xorg.?.log.old, the number in the log file name doesn't seem to be due to rotation.

I tried failsafe, but it failed too, but the failsafe log is also generated when I try the normal boot.
.Xauthority is not the issue: I've already removed it. I even tried with a completely empty home folder.

---

### Post by DuckHook on 2017-02-02
You don't mention it, but I assume that, because you have access, you are now backed up. Do not do any of the following unless your data is backed up and safe. The following actions may end up messing up your installation even further. I assume that you are free to try all sorts of things, including things that may make your system unbootable and will require a re-install.

[LIST=1]
[*]Try <Ctrl>+<Alt>+<F1> first thing when the login screen comes up. In other words, do ***not*** try to boot into your DE. Switch to a console instead. Does this work?
[*]If not, you will have to boot into recovery mode. I assume this is what you mean by "single user" mode.
[*]Let's see if your disk or inodes are full:```
df -h
``````
df -i
```You don't need to post back this output. Just let us know if you see any problems. They must still have space.
[*]If still plenty of space for files and inodes, then:```
sudo apt clean && sudo apt autoremove
```
[*]You use this as a portable stick, so I assume you have no special video drivers installed? If you do, disable them. This can be done by adding such drivers to */etc/modprobe.d/blacklist.conf* then rebooting.
[*]You've already tried purging .Xauthority. Now let's try to purge compiz:```
rm -r ~/.compiz
rm -r ~/.cache/compizconfig-1
dconf reset -f /org/compiz/
setsid unity
sudo reboot
```
[/LIST]
Try these first. If you still have problems, we will try something else

---

