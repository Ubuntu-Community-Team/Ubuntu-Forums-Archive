---
title: "hibernate &amp; suspend do not work"
date: 2008-09-13
forum: Desktop Environments
---

### Post by dancer58 on 2008-09-13
Ubuntu Hardy with the latest updates
motherboard is asus p5b-plus

These have not worked in Hardy since alpha2 or 3

hibernate:
when I try to hibernate it reboots right away and goes to login screen

suspend:
appears to suspend but will not come back. I use a usb keyboard and mouse. both are dead

They both work in winxp

---

### Post by kerry_s on 2008-09-13
add> acpi_sleep=s3_bios
to your kernel boot line.

hibernate use's swap, so you need at least a gig of swap. i use a 2gig swap so i have room to leave office stuff and come right back to it.

---

### Post by dancer58 on 2008-09-13
I also have 2 gig of swap

thanks

---

### Post by eddielgarcia on 2008-09-13
Could we be more specific with adding that option to the kernel boot line?  Could maybe an example be posted.  I have had the same problem since I've installed Ubuntu.  I can not put my machine to sleep it just shuts down and my Mother Board doesn't like that, it'll beep with a failure message.  It never did that with Windows so I doubt it is hardware.  
Hibernation worked until I installed restricted drivers for my ATI card, now it displays an error message before hibernating, shuts down my machine, and never wakes up. Still working on that issue.  Thanks!

ed-

---

### Post by andrewkirk on 2008-09-13
I also would like to try the solution suggested by kerry_s, but where is the 'kernel boot line' and how do you add something to it? (instructions designed for a complete novice would be great, as I have never had the courage to go anywhere near my kernel, even if I knew where it lived).

My config is Hardy Heron with latest updates, on an Asus P5GC-MX motherboard. 
I have installed and configured uswsusp to try to fix the problem but it doesn't help.

Hibernate saves the hibernation file and shuts down, then immediately restarts.
Suspend also appears to stop for a fraction of a second then restart.  

I have unplugged LAN cable, all usb peripherals and mouse and keyboard (the latter two after issuing the suspend command), as well as disabling wake-on-LAN and wake-on-anything in BIOS but the rotten computer still bounces straight back up! It hibernates and suspends just fine on winxp.:confused:

It's all very sad because the inability to suspend is the only thing that's stopping me from making ubuntu the default OS on our family  computer.  It's too noisy to leave on all the time, not to mention the energy that wastes.

---

### Post by kerry_s on 2008-09-14
press> alt+f2
type> gksudo gedit /boot/grub/menu.lst

look for your boot line, mine looks like this:
```
kernel		/boot/vmlinuz-2.6.18-6-k7 root=/dev/hda2 ro vga=794 acpi_sleep=s3_bios 

```

---

### Post by cdtech on 2008-09-14
Trying this now.......

---

### Post by cdtech on 2008-09-14
This didn't work for me. :(

**My solution:**
The trick is to get gnome-power-manager to use "/etc/acpi/sleep.sh force" instead of whatever it uses. 
I did this by editing:
```
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```
and replacing (I just commented the first line and added the next):
```
/usr/sbin/pm-suspend $QUIRKS
with
/etc/acpi/sleep.sh force
```
around line 74.

Now my "sleep" works with the lid switch and to hibernate I use the command line.

I made a couple of aliases to sleep and to hibernate from the command line:
```
alias sleep='sudo /etc/acpi/sleep.sh force'
alias hibernate='sudo /etc/acpi/hibernate.sh force'
```

Hope this helps ya.....

---

### Post by dancer58 on 2008-09-14
I tried "acpi_sleep=s3_bios" but it did not work so I tried

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
I changed
/usr/sbin/pm-hibernate $QUIRKS
with
/etc/acpi/hibernate.sh force

Now hibernate works

Thanks

I also tried the same with suspend but it does not work. 

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
I changed
/usr/sbin/pm-suspend $QUIRKS
with
/etc/acpi/sleep.sh force

I wonder if it has to do with the fact that I have a usb keyboard and a wireless usb mouse on a hub. 

I checked winxp and keyboard and mouse are also dead but power button restores from suspend. Also noticed that the power light blinks in winxp but not in ubuntu

---

### Post by andrewkirk on 2008-09-14
Thank you very much for your menu.lst solution kerry_s. My hibernate now works like a charm, via s2disk.

Now if only I can find a way to make suspend work. The PC still bounces back up when I try to suspend by pressing the power button, menu suspend, or keyboard sleep button, and if I execute s2both, it hibernates rather than suspends (which I don't think is what s2both is supposed to do).

---

### Post by kerry_s on 2008-09-14
> **andrewkirk said:**
> Thank you very much for your menu.lst solution kerry_s. My hibernate now works like a charm, via s2disk.

Now if only I can find a way to make suspend work. The PC still bounces back up when I try to suspend by pressing the power button, menu suspend, or keyboard sleep button, and if I execute s2both, it hibernates rather than suspends (which I don't think is what s2both is supposed to do).

sounds like your not on the supported list.
in a terminal:

sudo s2ram

if it says your not supported

sudo s2ram -f

if you get a black screen at resume, press ctrl+alt+f2 then ctrl+alt+f7

i always get the black screen and have to switch tty's, bug in s2ram.
s2ram is very buggy which is why i don't use it, i only use the s2disk.

---

### Post by andrewkirk on 2008-09-16
How does one get hold of s2ram?
It doesn't seem to be in Hardy Heron - 'command not found'. It's not in the uswsusp package either.

I tried 
   sudo /etc/acpi/sleepbtn.sh force 
and the computer went to sleep but then bounced straight back up, just like it does with every other method I try for putting it to sleep. 

I've also tried installing the package 'powersaved', which I saw recommended somewhere as a means of improving power management, but that didn't seem to help.

When the computer bounces back up it gives me some error messages:

[    0.844227] i8042 kbd 00:0a: activation failed
[    0.844331] i8042 aux 00:0b: activation failed
[    3.402429] hub 5-0:1.0: over-current change on port 1
[    3.506775] hub 5-0:1.0: over-current change on port 2
[    3.793985] hub 5-0:1.0: over-current change on port 3
[    3.897849] hub 5-0:1.0: over-current change on port 4
[    4.001738] hub 5-0:1.0: over-current change on port 5
[    4.105635] hub 5-0:1.0: over-current change on port 6
[    4.209527] hub 5-0:1.0: over-current change on port 7
[    4.313412] hub 5-0:1.0: over-current change on port 8

I wonder if that could be anything to do with it.

From looking at dmesg I see that there's a message saying 'CPU1 is down' and various messages about CPU0 but nothing saying CPU0 is down.  I wonder if it could be that only one of the two CPUs is going to sleep.

---

### Post by houbysoft.xf.cz on 2008-09-16
> **kerry_s said:**
> add> acpi_sleep=s3_bios
to your kernel boot line.

hibernate use's swap, so you need at least a gig of swap. i use a 2gig swap so i have room to leave office stuff and come right back to it.

Just a little thing, I might be wrong but AFAIK you don't need a gig of swap, you don't need two or three. You just need enough to put all your RAM in it. So, in order for hibernate to work,

your RAM amount < your SWAP space.

Make sure it works for you. For example, if you have 4 gig RAM, a 1 gig swap space is not enough.

---

### Post by ehellmer on 2008-10-06
I was also able to get hibernate to work, by editing the file. However, I was also not able to get the suspend to work.

---

### Post by tarps87 on 2008-10-07
> **houbysoft.xf.cz said:**
> Just a little thing, I might be wrong but AFAIK you don't need a gig of swap, you don't need two or three. You just need enough to put all your RAM in it. So, in order for hibernate to work,

your RAM amount < your SWAP space.

Make sure it works for you. For example, if you have 4 gig RAM, a 1 gig swap space is not enough.

There's a general rule that if you plan to hibernate it must be at least 1 1/2 time the size of your ram, all the data/bits on your RAM must be stored in it and also any thing already in there due to paging so the ideal is twice the size of your ram but 1 1/2 times should work for most

---

### Post by veluvalisr on 2008-11-03
Hi,

I have installed 8.10 on the weekend and having an issue with Hibernation.

I have logged in as an Administrator and then I hibernated my machine.
When I restarted it, my permission were restricted like I can not connect to the wireless network, not able to move my taskbars and soon.

Also, I have the same suspend issue which I will try the suggestion tonight.

Please help.

Thank you,
Ravi.

---

### Post by tarps87 on 2008-11-04
> **veluvalisr said:**
> I have logged in as an Administrator

What do you mean by logged on as Administrator, do you mean root?
It is suggested that you do not login as root which is why by default Ubuntu does not have a root user. Instead you should use the sudo command to access root privileges.

---

### Post by veluvalisr on 2008-11-04
Hi,

Sorry for my language, I mean to say I logged in with a user who has  Administrative permissions.

Also, I tried all the suggestions of adding files to sleep.d folder but still when I put my system to suspend mode and when I try to wake it up my screen won't be active.

Thanks & Regards,
Ravi.

---

### Post by sionghua on 2008-11-07
same problem with 8.10 here, press hibernate goes straight to reboot, and then ask me for password to resume from the hibernation.

---

### Post by tarps87 on 2008-11-07
when you have administrative permissions you should be able to use sudo to 'activate' these remissions i.e. ```
sudo apt-get install somePackage
``` to install some package.
I the the case of your network you do not need administrative permissions, have you got the password for the network stored? It is possible that if it is the network manager is not requesting this from the keyring (the central place where your saved passwords are stored). If this is the case it is possibly a bug.
What do you do to try and connect to the wireless network?

---

