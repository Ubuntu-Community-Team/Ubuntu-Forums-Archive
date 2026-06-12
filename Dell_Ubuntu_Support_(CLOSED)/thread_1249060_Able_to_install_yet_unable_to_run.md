---
title: "Able to install yet unable to run"
date: 2009-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gray0005 on 2009-08-24
[FONT=Arial][SIZE=2]I have installed Xubuntu 9.04 from two separate disks and I have gotten the same exact problem two times.  So, I’m guessing that it is not the disks.  I have successfully installed Xubuntu into the hard disk and the computer knows to boot to xubuntu when I start up.  Here are the prompts I see. (The plus signs signify new lines)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Starting up…[/SIZE][/FONT]
[FONT=Arial][SIZE=2][0.972002]… MP-BIOS bug: 8254 timer not connected to IO-APIC ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Loading, please wait…++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Gave up waiting for root device. Common problems: ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Boot args (cat/proc/cmd line) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Check rootdelay =(did the system wait long en enough?) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Check root= (did the system wait for the right device?) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Missing modules (cat /proc/ modules; Is /dev) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]ALERT! /dev/disk/by-uuid/175fd1df-b7a7-4a00-a984-8fbeb1fe88 does not exist. Dr opping to a shell![/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]BusyBox v1.10.2 (Ubuntu 1:1.10.2ununtu7) built-in shell (ash) ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Enter help for a list of commands ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2](initramfs) _ ++++[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]From here it stays with a flashing curser.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]So..  Apparently there is a way to edit the boot sequence so that apic is disabled and apparently this has fixed the problem for other people.  If anyone knows how to do this, please walk me through the process.  I am not the best with computers, so if you could write your response as if you're communicating with a six year old that would be appreciated.  Thanks, linux is an attractive idea to me because of it ethical and social appeal.  If anyone could help me become a part of the community it would be appreciated! -Chris[/SIZE][/FONT]

---

### Post by ugm6hr on 2009-08-25
How did you install Xubuntu - LiveCD or Alternate?

If Live, did you have to use any special settings?

If you are confident that noapic will resolve this issue:

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and press "e". Then you will see something like:

```
title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            329f6102-cd49-421b-a2c1-e4ed1f4d4a4c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=329f6102-cd49-421b-a2c1-e4ed1f4d4a4c ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

```

Select the line (with arrow keys) which begins with the word "kernel" and press "e" to edit it.

Add the word **noapic** to the end of the line and delete the quiet and splash (so that you can see what is happening behind the scenes) so that it looks like this: 

```
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=329f6102-cd49-421b-a2c1-e4ed1f4d4a4c ro noapic
```

Then press Enter and "b" to boot.

If that works, post back and I will explain how to make it permanent.

Just so you are aware, there are also nolapic and noacpi settings.

---

### Post by Gray0005 on 2009-08-27
my Xubuntu actually works from the live cd without any special settings.  I was also able to succsessfully install.   I figured out how to try to boot with either no apic or the other options and tried with either selected or both.   I still get the exact same error that I origianlly posted, minus the no apic part. still no luck.  I am running an old dell server with a SCSI BIOS and I keep hearing that the SCSI might be the problem, that xubuntu might lack the drivers I need.  I'm not sure.

---

### Post by ugm6hr on 2009-08-28
Your initial error does look like a HD issue; so likely it is a SCSI driver problem, or a specific problem relating to your HD.

---

### Post by Gray0005 on 2009-08-28
Thanks, I think you're right. The HD worked under XP so I'm going to look for drivers that might work for ubuntu. Thanks so much, you've helped me narrow the problem down quite a bit.

---

