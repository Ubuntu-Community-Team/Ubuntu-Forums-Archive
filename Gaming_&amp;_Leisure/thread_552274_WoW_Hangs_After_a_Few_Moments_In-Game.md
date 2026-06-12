---
title: "WoW Hangs After a Few Moments In-Game"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by Blamdarot on 2007-09-16
Hello,

I'm brand new to Linux and I've got Ubuntu Fiesty running on my machine. I am running World of Warcraft via Wine and I'm able to log in and get into the world.

The problem: system seems to hang with a few moments of the world appearing.

I have read every how to I can find on the internet. And I've found a bunch of people that report this same issue. 

However, they are all running ATI cards and the solutions have them making xorg.conf changes that appear to be ATI specific. I have an NVIDIA card.

I will be very grateful for any help.

Thank you,
Dena
P.S. I installed WoW by copying the director from a Windows partition on a HDD that I suspect is on it's last legs. No definitive problems with it yet, just a hunch and the fact that it's a 5 year old Maxtor.

---

### Post by hikaricore on 2007-09-16
Did you install the proper drivers for your card?

Which NVIDIA card do you have and how did you install said drivers?

---

### Post by Blamdarot on 2007-09-16
> **hikaricore said:**
> Did you install the proper drivers for your card?

Which NVIDIA card do you have and how did you install said drivers?

Thanks for getting back to me so quickly.

I am running a GeForce 7300 GT.

Yesterday, I installed the drivers by following the instructions on the NVIDIA website (specifically on this page: [http://www.nvidia.com/object/linux_display_amd64_100.14.11.html](http://www.nvidia.com/object/linux_display_amd64_100.14.11.html)). I downloaded the file; exited the Xserver ("sudo /etc/init.d/gdm stop"); then ran the file (sudo sh <path to file>). When I installed it, I was at the same point of getting WoW to work as I am right now. After that, I couldn't boot properly. When I booted, Xserver would fail to start and I'd get a warning about the driver version not matching in the various files.

After that, I* completely reinstalled Ubunutu *and I haven't done the above described update. If you think I should update those drivers, please provide me with instructions on how to completely remove them if they bork my system again.

Thanks again!

~Dena
P.S. I have a 64-bit AMD Processor.

---

### Post by hikaricore on 2007-09-16
Depending on what version of Ubuntu you're using there's a workaround for the driver mismatch issue.

For some reason the Feisty kernel refuses to acknowledge random blacklisted modules, so instead of doing it the normal way, we have to do this manually.  After that you need to install  the Nvidia drivers.  Just because you can't boot past command line does not mean your system is borked.  X is not that hard to reconfigure, and rarely requires a complete Linux reinstall.

Also unless you have a specific reason for running a 64bit version of Linux on your 64bit processor I advise against it.  Due to the number of odd problems you'll have, but if you don't care to heed this advice, more power to ya.

**[COLOR="DarkRed"]And _NO_ I will not provide removal instructions.[/COLOR]**

From the command line (ctrl+alt+F1 to get to a real CLI interface).

Login and run:

```

cd /lib/linux-restricted-modules/$(uname -r)
sudo rm nvidia* -R
```

If you get no errors, move on. (stopping X/gdm first):

```
sudo /etc/init.d/gdm stop
```

Install your Nvidia drivers which you downloaded from the Nvidia website, assuming they're on your desktop:

```

cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```

When it prompts asking if it can configure your X server say **YES**.

And if you get any errors write them down or something so you can post them on the Nvida forums. :p

Simply restart GDM at this point:

```
sudo /etc/init.d/gdm start
```

or reboot:

```
sudo reboot -t now
```

---

### Post by Blamdarot on 2007-09-16
Update:

There has been some unexplained improvement. Last night (well, 6:45 this morning), it was behaving as described: hangs shortly after login to game world.

Just now, I was able to login-fly around a world with lots of missing graphics and it lasted more than several minutes. I then changed the Resolution (in-game) and disabled Shader effects (also in-game). The missing graphics appeared and I spent a few more moments without a hang. Then I logged out to make sure the video settings were saved to the config file.

The only thing I did (and I've been keeping notes) since I shutdown this morning was set my preferences for GAIM. I can't imagine that has anything to do with it.

I'm going to try to install a few of my more necessary mods, and see how long I ca n remain ingame without a hang.

!Dena

---

### Post by Blamdarot on 2007-09-16
Set backs:

Immediately after my last post, I launched WoW in the same way and it crashed (I pressed alt-F2 and used the xkill to end WoW). I removed the addons and tried again. Crash. I recopied my windows /wtf/config file and made the updates for Linux. No improvement.

I've rebooted. I've cleared the WoW cache. Verified there are no addons. Checked the lines I added to the config file:
SET SoundOutputSystem "“1&#8243;"
SET SoundBufferSize "“150&#8243;"
SET gxApi "“OpenGL”"

I don't know what else to do.

Also, I noticed that each time I launch WoW after a crash, the framerate in the login screen and character selection screen gets worse and worse. Is there a memory leak? Or some process that isn't ending when it should?

Thanks very much for trying to help this noob!

~Dena

---

### Post by Blamdarot on 2007-09-16
> **hikaricore said:**
> Depending on what version of Ubuntu you're using there's a workaround for the driver mismatch issue....

I didn't see your post until a few minutes ago.

I did what you suggest, but the installer didn't work. There error said that I "do not appear to have libc header files installed on [my] system. Please install your distribution's libc development pack".

I assume I need to get this via the synaptic package manager? (That's what I did yesterday.) But since yesterday ended up with a mess, I'll wait until you can confirm that for me.

Thank you very much for your help.

~Dena

---

### Post by Blamdarot on 2007-09-16
After a reboot, it failed to boot to the xserver with the following error:

FATAL: Could not open '/lib/module/2.6.20-16.generic/volatile/nvidia.ko' No such file or directory.
NVIDIA: Failed to  load the NVIDIA kernel module!
NVIDIA: *** ABORTING ***

I copied a back up of my xorg.conf to /etc/X11/xorg.conf and was able to get back into the xserver.

Thank you for all your advice!

!Dena

---

### Post by Blamdarot on 2007-09-16
I've decided to take your advice about installing 32-bit on my AMD 64-bit machine.

I'll post again if I have more trouble.

!Dena

---

### Post by Blamdarot on 2007-09-16
> **Blamdarot said:**
> I've decided to take your advice about installing 32-bit on my AMD 64-bit machine.

I'll post again if I have more trouble.

I'm having more trouble. Well, the same trouble. WoW hangs and sometimes hangs the system (or at least the xserver) after a minute or two in-game.

Here is what I've done:
1. removed all partitions using gpartion on the live CD
2. installed i386 Feisty allowing the installer to handle the partitioning
3. booted to the harddisk and installed the OS updates as prompted
4. made backup copies of xorg.conf and sources.list
5. installed Wine via the Synaptic Package Manager
6. rebooted to make sure xserver still started
7. ran "winecfg" command and changed the emulated OS to XP
8. did the registry hack described under "Registry configuration" here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
9. shutdown machine,  connected my old windows HD, booted
10. copied my World of Warcraft folder and other personal files to my Ubuntu /home directory
11. shutdown, disconnected HDD, booted
12. removed all addons from the World of Warcraft/Interface/AddOns folder
13. added 3 lines to config.wtf:
[INDENT]SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"[/INDENT]
14. attempted to launch WoW via wine with the -opengl parameter
15. error message "Unable to Start 3d Acceleration"
16. System-Administration-Restricted Drivers
17. Enabled "NVIDIA accelerated graphics driver"
18. rebooted as advised by the Restricted Drivers utility
19. made a second back up of my xorg.conf file
20. ran WoW from terminal: wine WoW.exe -opengl

The system hung after about a minute in game world. I was unable to get a response with alt-F2, ctrl-alt-backspace, or alt-sysrq-i or e.

21. followed your previous instructions for updating NVIDIA drivers

The command "sudo ./<NVIDIA file name> did not work for me. I resorted to "sudo sh <NVIDIA file name>. Was that alright?

22. used the command you provided to reboot
23. backed up the xorg.conf file
24. ran nvidia-settings but didn't change anything
25. ran WoW: wine WoW.exe -opengl

The game hung after about 10 seconds in the world. I was able to use alt-F2 and xkill the application.

Please advise me on what to do. I'm getting rather desperate.

Thank you very much.

~Dena

Edit: I managed to successfully login with a different character. Ran a round for a few minutes without a hitch. Until I hear more, I'm going to try modifying the config.wtf file (after making a backup copy).

---

