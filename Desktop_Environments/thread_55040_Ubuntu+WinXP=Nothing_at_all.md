---
title: "Ubuntu+WinXP=Nothing at all"
date: 2005-08-07
forum: Desktop Environments
---

### Post by fresco on 2005-08-07
Hi

Some time ago I got rid of my XP and installed Ubuntu. But situation forced me to install WinXp again.
So I decided to use free space (which now is hda4, see cfdisk output*). Win setup program formatted free space without any errors, then copied all need files and restarted computer (to start second stage of setup).
And what I got when pc booted? All I could see was a "NTLDR is missing, press any key to restart" message.
Well, I thought I might fix the situation by running Win 
Recovery console and rewriting MBR. ....it didn't help. I tried to copy \I386\ntldr and \I386\ntdetect.com to E:\ (The partition where setup copied its files) - same message.
Then I tred to toggle nearly created NTFS partition active using grub from KNOPPIX. The message I got after that was "Cannot load operating system".

So... now what I have is unbootable Ubuntu, unbootable Win Setup and none knowledge  about fixing this.     :-)

I believe this is the right place for looking for smart people. I hope this thread will be usefull for others experiencing similar problems. :wink:

Thank any of you,
peace.

*
Yeap, my HDD is a mess, but right now it is not the main problem!   :grin:
---------------------------------------------
cfdisk output using KNOPPIX
---------------------------------------------
Name        Flags      Part Type  FS Type          [Label]        Size (MB)
------------------------------------------------------------------------------
hda1        Boot     Primary  Linux ext3       [/]             10043,07
                            Logical   Free Space                           0,01*
hda5        NC        Logical   Linux swap                         468,85*
                            Logical   Free Space                           0,04*
hda3                    Primary   FAT16            [           ]    2146,77*
                            Logical   Free Space                        2105,68
hda6                    Logical   NTFS             [^B]             22101,33
hda4                    Primary   NTFS                              3142,06
                                      Unusable                             8,23

---

### Post by roland on 2005-08-07
[QUOTE=fresco]Hi

Some time ago I got rid of my XP and installed Ubuntu. But situation forced me to install WinXp again.
So I decided to use free space (which now is hda4, see cfdisk output*). Win setup program formatted free space without any errors, then copied all need files and restarted computer (to start second stage of setup).
And what I got when pc booted? All I could see was a "NTLDR is missing, press any key to restart" message.
Well, I thought I might fix the situation by running Win 
Recovery console and rewriting MBR. ....it didn't help. I tried to copy \I386\ntldr and \I386\ntdetect.com to E:\ (The partition where setup copied its files) - same message.
Then I tred to toggle nearly created NTFS partition active using grub from KNOPPIX. The message I got after that was "Cannot load operating system".

So... now what I have is unbootable Ubuntu, unbootable Win Setup and none knowledge  about fixing this.     :-)

I believe this is the right place for looking for smart people. I hope this thread will be usefull for others experiencing similar problems. :wink:

Thank any of you,
peace.

*
Yeap, my HDD is a mess, but right now it is not the main problem!   :grin:
---------------------------------------------
cfdisk output using KNOPPIX
---------------------------------------------
Name        Flags      Part Type  FS Type          [Label]        Size (MB)
------------------------------------------------------------------------------
hda1        Boot     Primary  Linux ext3       [/]             10043,07
                            Logical   Free Space                           0,01*
hda5        NC        Logical   Linux swap                         468,85*
                            Logical   Free Space                           0,04*
hda3                    Primary   FAT16            [           ]    2146,77*
                            Logical   Free Space                        2105,68
hda6                    Logical   NTFS             [^B]             22101,33
hda4                    Primary   NTFS                              3142,06
                                      Unusable                             8,23[/QUOTE]

I see you have a KNOPPIX-cd, which will get you a lot further :) I don't really know why Windows refuses to start, but I heard somewhere that Windows needs to be on the first partition of the first harddisk to run properly. Maybe the Windows MBR recovery tool you used, tried to let Windows think it had to start from the first partition, which is your Ubuntu disk.

I am a LILO user, which is an alternative to GRUB, but what you could try is the following. Have KNOPPIX started, and open a root terminal. Mount your first hard drive like this and cd there: ```
mount -t ext3 /dev/hda1 /mnt/hda1
cd /mnt/hda1
```

Check with ls if your first partition is correctly mounted. If so, type ```
chroot .
``` This changes the root directory (/) to the current dir, so everything you do is done like it would be from a correctly booted Ubuntu. Make sure the GRUB configfile is still correct, and the Windows partition is correctly mentioned in it. After checking this, execute the command ```
grub-install /dev/hda1
``` and restart your computer.

Things *should* be working now, I have written all this only by thinking and reading the GRUB manual. Like I said, I'm not a GRUB user, so I really hope it works out. Don't hesitate to ask any more questions.

---

### Post by Freddy on 2005-08-07
Think that XP is less forgiving about where you put the root and your C partition must be hda1, otherwise it can't boot, you also wrote over your GRUB when you reinstalled you'r XP, you have to boot up with your knoppix cd and reinstall it and make the necessary configurations.

/Freddan

---

### Post by fresco on 2005-08-07
MANY THANKS TO ROLAND!!!!

Everything worked fine! Now I'll try to continue Win setup.
What can I say man... When nothing works, Linux will come to help!  :) 

Thank this forum too!

---

