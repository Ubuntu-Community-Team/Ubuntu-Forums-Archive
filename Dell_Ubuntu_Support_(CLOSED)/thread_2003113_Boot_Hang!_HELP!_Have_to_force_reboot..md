---
title: "Boot Hang! HELP! Have to force reboot."
date: 2012-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lJ9%3MR&gt;sa on 2012-06-13
I have a Dell Optiplex GX260 that is having boot problems. It didn't have these problems with Xubuntu 11.10. I currently have Xubuntu 12.04 installed, and when I boot the computer sometimes the screen shows the kernel message "stop save kernel messages" or something like this "edit sbined(not sure) /etc/.....(don't remember since I'm not in front of the computer)." Sometimes it'll boot but takes 5 minutes. If I force reboot by holding down the power button and turning on the computer, sometimes it will boot right into Xubuntu in about 30 sec no issues. Most of the time that's what I get(above). I don't have access to the computer right now (computer is not located in my house) so I can't post any boot logs (also don't know how or where to look on the hard drive). Please help me. I've been going nuts to try to figure out the problem. I've tried Lubuntu, Linux Mint, and Xubuntu. Couldn't get Linux Mint to load off my USB live drive all the way (weird, right?), but everything else loaded just fine. Of course after the install it was a 1:5 chance of getting it to boot successfully.

SPECS (As much as I can recall):
Intel Pentium 4 2.4GHZ Processor
1GB DDR RAM
CD-RW/DVD-ROM Drive
80GB Western Digital HDD
D-Link AirPlus Xtreme G DWL-G520 PCI Wireless Card (shows ath5k driver in Ubuntu)(maybe I need to blacklist other atheros? That's one of my suspicions of my boot problems.)

[COLOR=Red]
[/COLOR][SIZE=4][COLOR=Red]PLEASE HELP!!!!!!!!!!!!! PLEASE!!!![/COLOR][/SIZE] :(:(:(

EDIT:
One reason for this post was that I couldn't remember the boot messages. I had set GRUB to boot with out "quiet splash" kernel tags on purpose for that reason. 
Sorry for getting kind of crazy (deleted those sentences) I was getting frustrated since I couldn't find a problem like mine anywhere on the Internet. Sorry. ;)

---

### Post by wilee-nilee on 2012-06-13
First I will say accusing the forum like this will cut out many users from even wanting to help.

Second not every problem gets fixed, and may be, due to not enough information. You have to get orientated to what info needs to be posted.

There is a tool commonly used to fix boot problems, use it to get the bootinfo summary and post the HTTP address.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Post it to this thread.
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

I would edit that post to a more friendly one honestly. ;)

---

### Post by QIII on 2012-06-13
If I might add ...

I took a look at the other thread you started.  You jumped the gun a couple of times with your bumps.  Please give it 24 hours.

Remember that we are all volunteers here, we don't get paid, we have wives, kids, grandkids and jobs.  We live all around the world and might not even be awake when you post.

None of us knows everything there is to know and the person with just the right answer may not get to your post immediately after you leave it.  That doesn't mean nobody is willing to help.

Biting the hand before it feeds you is rarely a good way to have your belly filled.

---

### Post by drs305 on 2012-06-13
We really need more information to help. The next time it happens please try to get the exact error messages.

One boot message that includes "/etc" may be that an entry in "/etc/fstab" isn't mounting.  You can inspect that file and make sure the UUIDs and mount points are correct.

Are you familiar with the fsck checks that are accomplished periodically (used to be every 30 boots I think). If you reboot often it may be accomplishing an fsck check on your partitions. This can take some time but a message should be visible indicating a check is being run if this is the case.

---

