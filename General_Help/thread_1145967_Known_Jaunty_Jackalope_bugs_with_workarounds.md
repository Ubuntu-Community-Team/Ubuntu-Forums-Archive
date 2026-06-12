---
title: "Known Jaunty Jackalope bugs with workarounds"
date: 2009-05-02
forum: General Help
---

### Post by frodon on 2009-05-02
[COLOR=DarkOrange]**Disclaimer : The purpose of this thread is just to list known [SIZE=3][B]Jaunty Jackalope**[/SIZE] bugs [SIZE=5]_and give the corresponding workarounds and launchpad entries_[/SIZE][/COLOR]. [COLOR="Teal"]All discussions about the bug or the workaround itself must go in the thread dedicated to the bug.[/COLOR][/B]

[SIZE=4][COLOR=Red]**_Please do not list bugs here without any workaround_**[/COLOR][/SIZE]


-------------------------------------------------

**[SIZE=4]>>>>>> Official Release Notes : <<<<<<[/SIZE]**


[color=navy][size=4]Note: The release notes list know bugs and bug reports and solutions (if any). Please read the release notes before installing or upgrading to Jaunty (Ubuntu 9.04).[/size][/color]

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

**_Performance regressions on Intel graphics cards_**:
- Bug Report: [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards")
- Workaround: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

**_Nvidia non-root permissions bug_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7201482&postcount=3](http://ubuntuforums.org/showpost.php?p=7201482&postcount=3)

**_Camera doesn't mount when connected and switched on_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

**_Remote Desktop (vnc) screen freezes when remote host is 9.04_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7214210&postcount=5](http://ubuntuforums.org/showpost.php?p=7214210&postcount=5)

**_Jaunty 9.04 Blind to XP's Shared Network Printer_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7214797&postcount=6](http://ubuntuforums.org/showpost.php?p=7214797&postcount=6)

**_Editing calendar events to recur forever corrupts the calendar the event is tied to_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/362318](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/362318)
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/372503](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/372503)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7258995&postcount=18](http://ubuntuforums.org/showpost.php?p=7258995&postcount=18) or the one proposed in bug report.

**_wubi installer's pyrun.exe says "no disk"_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7276236&postcount=19](http://ubuntuforums.org/showpost.php?p=7276236&postcount=19)

**_mdadm software raid breaks on intrepid-jaunty upgrade_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7220050&postcount=19](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19)

**_Grip can't eject CD and also rips slow_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/grip/+bug/382013](https://bugs.launchpad.net/ubuntu/+source/grip/+bug/382013)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7374309&postcount=28](http://ubuntuforums.org/showpost.php?p=7374309&postcount=28)

**_2.6.28-11 causes data corruption on some 64 bit installations_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)

**_update-manager doesn't show updates, even after 1 week_**
- Bug Report: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)
- Workaround: [http://ubuntuforums.org/showpost.php?p=7487577&postcount=34](http://ubuntuforums.org/showpost.php?p=7487577&postcount=34)

-------------------------------------------------



Fell free to propose other known Jaunty Jackalope bugs to be listed here but **[COLOR=Red]think to provide a link to the workaround and a link to the  corresponding launchpad entry.[/COLOR]**

Other ubuntu version "known bugs" threads :
[Intrepid Ibex known bugs]("http://ubuntuforums.org/showthread.php?t=966436")
[Hardy Heron known bugs]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by icedfusion on 2009-05-02
BUG:
====
Installing the 64bit version of Jaunty I found the install would just hang at the splash screen(ok for 32bit which was odd).
Found that as I did not have a floopy drive installed, the install would continual check for fd0

WorkAround:
==========
Disable the floppy drive in the bios.

---

### Post by dcstar on 2009-05-02
The permissions of the /dev/nvidia files cause errors when processes are launched with non-root privileges on my 64-bit 9.04 desktop system.

In my case I get Direct Rendering errors when launching a Direct Rendering enabled VM inside VMware Server, but running glxinfo without sudo shows the error:

NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).

I have found many other posts with the same issue (including people using Wine), and here is my current workaround since reinstalling the 180 driver package did not fix it:

```
gksudo gedit /etc/rc.local
```
Add the following before "exit 0":

```
chmod 666 /dev/nvidia* &
```

Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249)

---

### Post by The Cog on 2009-05-03
**Camera doesn't mount when connected and switched on.**

Many people have reported this bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)

**Quick fix:**
Use the command:
> sudo killall gvfs-gphoto2-volume-monitor
then connect the camera.

**Long-term fix:**
Prevent the process from starting. Use the command:
> sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

---

### Post by Just_SomeGuy on 2009-05-04
Remote Desktop (vnc) screen freezes when remote host is 9.04 although mouse clicks and key commands still reach the target machine.

The bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

The workaround:
Disable Compiz on the remote machine 
System -> Preferences -> Appearance -> Visual Effects = None

---

### Post by celem on 2009-05-04
[BUG]-------------
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273)
When adding a printer attached to and shared on my Windows XP box with System->Administration->Printing, New->Network Printer->Windows Printer via SAMBA, Browse - you get right up to where clicking the little gray diamonds should reveal a networked printer and Poof the dialog crashes and is gone.

[WORKAROUND]------
Used the Windows box IP address instead of Browsing for the printer. This permits you to go to the next steps and create a printer, although it won't work yet, i.e.  test page won't print. Next click the change URI button for the printer path name and it will present another opportunity to Browse. This time it will find the Windows printer, correctly changing the path and then the test page will print and the printer is setup.

---

### Post by generic_idea_machine on 2009-05-04
> **Just_SomeGuy said:**
> Remote Desktop (vnc) screen freezes when remote host is 9.04 although mouse clicks and key commands still reach the target machine.

The bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

The workaround:
Disable Compiz on the remote machine 
System -> Preferences -> Appearance -> Visual Effects = None


How is that a workaround?

Just when I was truly beginning to appreciate all that compiz had to offer. (80$ video card, 4 gigs of memory later).

---

### Post by frodon on 2009-05-05
First post updated, thank you for your really useful reports.

---

### Post by tad1073 on 2009-05-05
Why nothing addressing all the issues with wireless?

---

### Post by dli8ilb on 2009-05-06
[BUG]-------------
[https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176](https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176)
opening alarm-clock causes screen to freeze

[WORKAROUND]------
[https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176/comments/82](https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176/comments/82)
install Alarm Clock 0.9.19 from getdeb

---

### Post by frodon on 2009-05-06
> **dli8ilb said:**
> [BUG]-------------
[https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176](https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176)
opening alarm-clock causes screen to freeze

[WORKAROUND]------
[https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176/comments/82](https://bugs.launchpad.net/ubuntu/jaunty/+source/alarm-clock/+bug/321176/comments/82)
install Alarm Clock 0.9.19 from getdebThe bug report says fix commited, i guess there should be a packet in the repo or soon available in the repo which fixes it

---

### Post by cprofitt on 2009-05-06
Some users are experiencing a shutdown hang when their wireless card is loaded.

The work around is to disable the card:

I prefer to use the following:

```

sudo ifconfig wlan0 down

```

note: This make the assumption that your wireless card is wlan0

---

### Post by Tipped OuT on 2009-05-08
[BUG]

Able to switch to cube caps (in desktop cube) as if it was another desktop.

---

### Post by Don1500 on 2009-05-08
> **Tipped OuT said:**
> [BUG]

Able to switch to cube caps (in desktop cube) as if it was another desktop.

I can do the same with the cylinder, only the top. The cap acts like a desktop withour panels. (I haven't tried alt-F2 yet, just thought of it)
But you can get out of that desktop with ctrl-alt left mouse.Is this even a bug? Does it really matter? I uses it as a fast way to lock the screen, as long as I don't show anyone how to get out of it, it's locked.

---

### Post by blueorder on 2009-05-09
> **The Cog said:**
> **Camera doesn't mount when connected and switched on.**

Many people have reported this bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)

**Quick fix:**
Use the command:

then connect the camera.

**Long-term fix:**
Prevent the process from starting. Use the command:

I see, from the gphoto [website]("http://www.gphoto.org"), that libgphoto2 has been upgraded to 2.4.5 on 4/2/09 (we currently have 2.4.2 installed). Maybe a bug fix is in there? Reading the release notes, it is not obvious to me if this was addressed.

---

### Post by Brandon Williams on 2009-05-10
[BUG 349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)
==========

Jaunty's UNR desktop-switcher does not work.

WORKAROUND
==========

Described [here](http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html), and in the bug report. Install the custom version of desktop switcher that the developer links to in a comment in the bug report.

---

### Post by frodon on 2009-05-11
In the launchpad bu report the bug is tagged as fix commited so i guess a fix will soon hit the repositories if not done yet.

---

### Post by jespdj on 2009-05-11
> **cprofitt said:**
> Some users are experiencing a shutdown hang when their wireless card is loaded.

The work around is to disable the card:
See [this thread](http://ubuntuforums.org/showpost.php?p=7149271&postcount=22) for a workaround that doesn't require you to manually unload the driver every time before you shut down.

---

### Post by kozlovsk on 2009-05-11
Evolution hangs and calendar data gets irreversibly corrupted when attempting to modify recursive event. Discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=1153619").

Workaround: do not modify, just delete and make a new one.

---

### Post by Omicron Machine on 2009-05-11
Hello,

I'm not sure if this is a Jaunty bug, but I know it worked on Hardy and Intrepid, and still works on my sister's machine, which runs Vista. I'm sorry I don't have a work around for it, but due to the nature of the problem, this is the closest place to post it I have. You see, the Ubuntu forums won't let me post a new thread. I was trying to get some help on wireless and the forums won't let me post a new thread. It logs me out when I click, "New Thread", so, obviously, I can't get help with this normally. I've been waiting in IRC most of the day, and some of yesterday, but no one's been on. If you can help, please PM me, I think I can do that. And, of course, feel free to delete this post.

---

### Post by chiques on 2009-05-12
BCM4311 Broadcom Wireless Card looses functionality after upgrading. When running ***#lshw -C network*** the logical name for the wireless card is gone. 

```
root@user-laptop:/# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:6f:b1:9c:ba:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@user-laptop:/# 
```

I have browsed these forums but I haven't found a work around yet. If I do, I will verify it and post a link to it.

---

### Post by GuiGuy on 2009-05-12
[Poor SATA performance]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730") continues to plaque many of us.

---

### Post by brntoki on 2009-05-12
Total system freezes, seemingly tied to networking.

Current workarounds include:

[INDENT]1. Boot Windows.
2. Before Turning on the computer, decide not to and go out and get some exercise instead.[/INDENT]

---

### Post by lisati on 2009-05-14
Bug: Wubi repeatedly complains "no disk" with "Cancel, Try again, Continue" on some systems with card readers
Launchpad entry: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

One work-around: Use Windows' "Safely remove hardware" to disconnect card reader and try again
Another work-around: Bypass Wubi and install Ubuntu into its own partition

---

### Post by frodon on 2009-05-14
First post updated, thanks all for your feedback.

---

### Post by Brandon Williams on 2009-05-14
> **frodon said:**
> First post updated, thanks all for your feedback.

It would be good to list the desktop-switcher bug in the first post, too. It is not fixed in Jaunty, yet. So far it only has a fix release for Karmic. There have been a fair number of questions about this in the forums.

Edit: Never mind, I see now that the issue has been added to the release notes.

---

### Post by frodon on 2009-05-14
> **Brandon Williams said:**
> Edit: Never mind, I see now that the issue has been added to the release notes.Thanks for the update i was adding it when i saw your edit.
When i first looked at the bug report it was not clear for me than the fix wasn't available for jaunty.

---

### Post by FIONEX on 2009-05-16
ATI driver with new Ubuntu 9.04 will give a delay when maximizing or minimizing windows.  That's due to a patch that was removed from Xorg for the sake of intel cards.  Go figure...make ubuntu less compatible with 40% of the cards in the market (ATI) in order to make it compatible with 10% of the cards?  Anyways, here's the steps to fix it.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

---

### Post by johnraff on 2009-05-16
**Software packaged with Jaunty**
I'm not sure if this thread is suitable for problems caused by software in the repositories being updated, but as a result of moving to Jaunty two issues came up:

**lftp**
The version of lftp in Jaunty (3.7.8-1) crashes with a segfault when doing "mput -d", ie recursive upload. A serious problem, reported in [Debian bugs]("http://osdir.com/ml/debian-bugs-closed/2009-05/msg01776.html"), but nothing in Launchpad so far. The version of lftp in the Karmic repos (3.7.13-1) seems to have fixed this.

Workaround: install [lftp 3.7.13-1]("http://packages.ubuntu.com/karmic/lftp") from the karmic repository. This needs the karmic versions of [libtasn1-3]("http://packages.ubuntu.com/karmic/libtasn1-3") and [libgnutls26]("http://packages.ubuntu.com/karmic/libgnutls26") too. It seems to have worked for me, but this involves messing with your system so be careful.

**espeak**
Espeak is behaving oddly, hanging or cutting off some words. ([Launchpad]("https://bugs.launchpad.net/ubuntu/+source/espeak")).

Workaround: pipe its output to aplay:
```
espeak "hello" --stdout | aplay
```
(There may yet be other espeak issues related to pulse or portasound, which I'm not using.)

---

### Post by LO Matt on 2009-05-17
Upon upgrade to Jaunty from Intrepid, there are problems w/ mdadm RAID arrays not being able to mount, caused by an overwritten mdadm.conf file.  

The following forum post/thread gave me the fix:  [http://ubuntuforums.org/showpost.php?p=7220050&postcount=19]("http://ubuntuforums.org/showpost.php?p=7220050&postcount=19")

The bug report: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298")

---

### Post by jfh on 2009-05-18
> **frodon said:**
> Thanks for the update i was adding it when i saw your edit.
When i first looked at the bug report it was not clear for me than the fix wasn't available for jaunty.


As I understand it, the "workaround" to avoid the "Exception Processing Message c0000013 Parameters 7bb6bf7c, etc.etc,etc" on tryng to install 9,04 is to disable some of the hardware components in my computer, or else create a another partition on my hard drive just for Ubuntu.  Some workaround! Maybe we should just buy another computer so Ubuntu could have one to itself.  I had installed and used an earlier version in Virtual Box until I got tired of being referred to "Terminal" whenever some slight problem arose (I learned on DOS, and had quite enough of that, thanks very much).  Maybe one thing we should be grateful to Ubuntu/Linux for is to make us appreciate Windows.

---

### Post by upptown on 2009-05-19
> **jfh said:**
> As I understand it, the "workaround" to avoid the "Exception Processing Message c0000013 Parameters 7bb6bf7c, etc.etc,etc" on tryng to install 9,04 is to disable some of the hardware components in my computer, or else create a another partition on my hard drive just for Ubuntu.  Some workaround! Maybe we should just buy another computer so Ubuntu could have one to itself.  I had installed and used an earlier version in Virtual Box until I got tired of being referred to "Terminal" whenever some slight problem arose (I learned on DOS, and had quite enough of that, thanks very much).  Maybe one thing we should be grateful to Ubuntu/Linux for is to make us appreciate Windows.

Yet another objective, reasonable, open minded comment.  I remember many times I had to remove hardware from my box to get Windows to install then install the hardware afterwards.  Need I remind you that Vista required video and memory upgrades to get the "full" experience or that one of the first steps in troubleshooting a cranky Windows system is to use "Run" to access msconfig and disable services/startup applications?  Every OS has it's issues.  At least I don't have to pay for the privilege when I use Linux.

---

### Post by Don1500 on 2009-05-19
> **Brandon Williams said:**
> It would be good to list the desktop-switcher bug in the first post, too. It is not fixed in Jaunty, yet. So far it only has a fix release for Karmic. There have been a fair number of questions about this in the forums.

Edit: Never mind, I see now that the issue has been added to the release notes.

When I read the first sentence I thought there was a fix for a bug I have. I can't find this mentioned anywhere else so I'll post it here.

UBUNTU > 9.04 > ext4 partition > Radion 9600 with the OSS drivers.
When using Compiz No problem rotating to the other desktops. But using the switcher in the lower panel to switch desktops and the panels (Top and Bottom) dissapear. only way back is to reboot. Oh yes you can rotate the cube all you want and the panels still don't come back. Is this a known bug?

---

### Post by Arup on 2009-05-25
The camera not recognized bug can be easily solved by selecting the camera to normal mode instead of PTP. Works fine with my SONY W5DSC and my SONY-Minolta Alpha 900.

---

### Post by xXeHPiCXx on 2009-05-26
For me my start up time has increased.

---

### Post by matey3 on 2009-05-28
No Known Workaround for Display settings:

Display and/or Monitor drivers cannot be changed/modified/set/reset in 9.04.
xorg.conf is obsolete and No GUI solutions either!

Plug and Pray...

---

### Post by TheExplorer on 2009-05-29
Probably a **bug** in Xorg: there is a strange behaviour when right-clicking a link in **Firefox**. It randomly opens up different windows, dialogues etc. (for saving or bookmarking).

Workaround: install [Mouse Gestures]("https://addons.mozilla.org/en-US/firefox/addon/39") extension. It has to be enabled, but you may remove all the gestures and uncheck all the boxes to avoid their action (if you do not need them actually).

---

### Post by ActiveFrost on 2009-05-29
> **TheExplorer said:**
> Probably a **bug** in Xorg: there is a strange behaviour when right-clicking a link in **Firefox**. It randomly opens up different windows, dialogues etc. (for saving or bookmarking).

Workaround: install [Mouse Gestures]("https://addons.mozilla.org/en-US/firefox/addon/39") extension. It has to be enabled, but you may remove all the gestures and uncheck all the boxes to avoid their action (if you do not need them actually).

Actually, it's a /bug/ in all versions, not only Jaunty ( at least it gives me this "random command" feature on 8.04/8.10/9.04 ). Anyway, thanks for the trick to solve this .. hard to work if 1/5 clicks are "E-Mail this link" :D

---

### Post by dcstar on 2009-05-30
**Grip can't eject CD and also rips slow**

Grip eject code no longer works so it thinks that a new CD has been inserted and remains in a loop continually ripping the one CD unless manually terminated. Also CD ripping is very slow unless following code is used.

Bug: [https://bugs.launchpad.net/ubuntu/+source/grip/+bug/382013](https://bugs.launchpad.net/ubuntu/+source/grip/+bug/382013)

Workaround:

```
sudo hal-disable-polling --device /dev/sr0
```

This will allow the Grip eject to function, and had the "bonus" side-effect (on  my system) of significantly increasing rip speed.

This will stop the 9.04 function of mounting the drive, and can be reversed by:

```
sudo hal-disable-polling --device /dev/sr0 --enable-polling
```

---

### Post by quixote on 2009-06-01
Symptoms: [Bug #346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all") affects 64-bit installs and causes the system to freeze up randomly, not associated with any specific program.  A hard reset is the only way to regain control, and then the system usually won't boot because of filesystem corruption: missing or bad inodes reported, and so on.  Fsck has to be run manually from recovery mode to fix it, until the next time it blows up again.

This bug is not related to **ext4** filesystem corruption on i386, ie 32-bit installs, so the fix below is probably irrelevant in that case.

The cause appears to be the 2.6.28.11 kernel that comes with Jaunty.  The fix is to install a 2.6.29 kernel:
```

$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
$ sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
(or **_i386.deb if on 32bit**)
``` (Thanks to Daniel J. Blueman for the fix!)

---

### Post by Arup on 2009-06-02
The bug described above only affects few specific type of input controllers I guess as I am yet to experience a single symptom like that on either of my PCs or laptops loaded with Jaunty x64. This includes a 5400XS Intel dual quad core, a AMD Phenom on AMD chipset and a Panasonic Toughbook.

---

### Post by frodon on 2009-06-02
First post updated, thanks for your feedback.

---

### Post by quixote on 2009-06-02
*only affects few specific type of input controllers* ... I'm sure that's true (I remember something about ICH8 / 9 chipsets from the bug report), but believe me, those of who *are* affected think it's the end of the world! ;-)  There are nearly 20 bug reports that were merged with the main one.  So, yes, it affects a rather specific set of chips, but they're not that uncommon.

---

### Post by Gina on 2009-06-03
I too get random system freezes but without file corruption.  I'll try the kernel upgrade as suggested.  Thank you :)

---

### Post by Gina on 2009-06-03
Unfortunately that didn't work - couldn't get the display working (nvidia) - so I'm back to the origina kernel version.

---

### Post by twrock on 2009-06-06
> **celem said:**
> [BUG]-------------
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273)
When adding a printer attached to and shared on my Windows XP box with System->Administration->Printing, New->Network Printer->Windows Printer via SAMBA, Browse - you get right up to where clicking the little gray diamonds should reveal a networked printer and Poof the dialog crashes and is gone.


I used this modified workaround. Maybe it's a little simpler for some of us newbies than figuring out the Windows machine's IP address.

Click Main Menu>System>Administration>Printing
Click New>Network Printer>Windows Printer via SAMBA
Hit the "Browse" button. "SMB Browser" box pops up. Note the names under the headings labeled Share and Comment. (So in my case, the name under Share was MSHOME and the name under Comment was DESKTOP1.)
Cancel out of the "SMB Browser" window. Click in the entry box beside smb:// and enter those names in this form: ShareName/CommentName/
Click "Browse" again. This time the list should be populated in the "SMB Browser" popup box (after a short wait) with the names of your shared printers. Choose the one you want and proceed with the installation.

---

### Post by Bearly Able on 2009-06-06
> **quixote said:**
> Symptoms: [Bug #346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all") affects 64-bit installs and causes the system to freeze up randomly, not associated with any specific program.  A hard reset is the only way to regain control, and then the system usually won't boot because of filesystem corruption: missing or bad inodes reported, and so on.  Fsck has to be run manually from recovery mode to fix it, until the next time it blows up again.

This bug is not related to **ext4** filesystem corruption on i386, ie 32-bit installs, so the fix below is probably irrelevant in that case.

I have the same problem on 32bit Jaunty with ext3.  I've now reached the point where the filesystem corruption is preventing me booting (I have a message about Kernel panic) and I have no idea how to recover from it.  I'm about to do a fresh install of Intrepid, as there seems to be no other solution.

---

### Post by quixote on 2009-06-06
Lesley, I think sometimes it's possible to recover even when the kernel starts panicking.  I'm not sure of the best steps to follow, but start a new thread to ask about it and I'm sure there will be people who know. (A clean install is definitely the simpler solution.)  

Did you use fsck or did you just keep trying to boot until the kernel panic situation?  ```
fsck -y /dev/whichever-partition-the-boot-process-said-was-bad
``` the -y option says to answer "yes" to all questions.  I don't know enough to have any other choice anyway, so using that option makes it simpler. (Run that only on UNmounted partitions, or if prompted in a recovery console during a bad boot up.)

---

### Post by Bearly Able on 2009-06-06
Thanks for your reply, quixote.

I ran the fsck as prompted when rebooting, saying "yes" to all the fixes.  I also ran xfix from recovery mode, as I was getting X server error messages.  Both of these on numerous occasions over the past two weeks, because the freezes were becoming more and more frequent.

I've spent far too much time in the last fortnight trying to fix my computer, so I've opted for a fresh install - I *really* need to get on with my work!  I've added to the bug report at launchpad, because it does seem to be the same problem that's so-far only been reported as affecting 64-bit Ubuntu.  I understand updating the kernel should fix it, but at the moment I just want a functioning computer with no hassle, so I've installed 8.10.

---

### Post by quixote on 2009-06-07
Lesley: I realized when I saw your bug report comment that you didn't need any info on fsck. :)  At this point, we only know that updating the kernel fixes the 64-bit version, and, as you say, there comes a point when you actually need to get things done.  

They seem to be focusing on the ICH8/9 (hard disk controller?) chipset as the sticking point.  "Sudo lshw" spews out that information toward the end of its output.

---

### Post by Bearly Able on 2009-06-07
Hi quixote and thanks for that.  In some ways I'd like to have stayed with it and tried to find a fix, but I need to work and my husband needs his business e-mail (we both work from home) and it was just becoming impractical.  I've only been using Linux since February and updating the kernel seems a bit daunting at this stage.  I just might have tried it when we first had problems, if I'd realised where the trouble lay, but at the time I was blaming my Nvidia drivers.  I was also not reading forum posts about 64-bit Jaunty, as I was running 32-bit...

I'll be interested to see the outcome of this.

---

### Post by jmap82 on 2009-06-09
> **generic_idea_machine said:**
> How is that a workaround?

Just when I was truly beginning to appreciate all that compiz had to offer. (80$ video card, 4 gigs of memory later).

I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by Duckslammer on 2009-06-10
> **The Cog said:**
> **Camera doesn't mount when connected and switched on.**

Many people have reported this bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)

**Quick fix:**
Use the command:

then connect the camera.

**Long-term fix:**
Prevent the process from starting. Use the command:

This doesn't work with my Nikon D60.  I've chmod'ed the command and killall says it wasn't running anyway.  No errors are being reported in the kernel log when I plug in the camera though there is a note that it was detected.

---

### Post by azeezp on 2009-06-10
> **The Cog said:**
> **Camera doesn't mount when connected and switched on.**

Many people have reported this bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301281)

**Quick fix:**
Use the command:

then connect the camera.

**Long-term fix:**
Prevent the process from starting. Use the command:


I tried the long-term fix, after that when i mount my kodak camera, nothing happens. it is listed in lsusb, but no drive available anywhere. How do i access my camera drive?

---

### Post by mafaldaspeaks on 2009-06-10
> **celem said:**
> [BUG]-------------
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/368273)
When adding a printer attached to and shared on my Windows XP box with System->Administration->Printing, New->Network Printer->Windows Printer via SAMBA, Browse - you get right up to where clicking the little gray diamonds should reveal a networked printer and Poof the dialog crashes and is gone.

[WORKAROUND]------
Used the Windows box IP address instead of Browsing for the printer. This permits you to go to the next steps and create a printer, although it won't work yet, i.e.  test page won't print. Next click the change URI button for the printer path name and it will present another opportunity to Browse. This time it will find the Windows printer, correctly changing the path and then the test page will print and the printer is setup.

Would you know how to do this in kubuntu 8.04 which I'm using with my laptop? I need to use the HP PSC 1400 on my windows network.

I've started using samba but it can't seem to "find" the printer I mentioned above.

---

### Post by muecker on 2009-06-19
Just a thought, wouldn't you need to install the restricted modules for 2.6.29-4 (actually 2.6.29-5 is out now)?

---

### Post by paperplate9 on 2009-06-20
**Bug**: automatic updates checking not working after upgrade from Intrepid to Jaunty. `apt-get update` or update-manager 'check' works fine, however, but are manual operations.

**Launchpad**: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

**Reason**: /etc/cron.daily/apt script incorrectly chmod'ed as 644 aka not executable

**Fix**: # chmod 755 /etc/cron.daily/apt ... reboot; might help to remove /var/spool/anacron/cron.daily

---

### Post by cyberkost on 2009-06-21
> **LO Matt said:**
> Upon upgrade to Jaunty from Intrepid, there are problems w/ mdadm RAID arrays not being able to mount, caused by an overwritten mdadm.conf file.  

The following forum post/thread gave me the fix:  [http://ubuntuforums.org/showpost.php?p=7220050&postcount=19]("http://ubuntuforums.org/showpost.php?p=7220050&postcount=19")

The bug report: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298")

I suspect Jaunty is guilty of [messing my raid10 up](http://ubuntuforums.org/showpost.php?p=7480321&postcount=73) (albeit in a more subtle way), but the linked workaround does not seem to help in my situation.

---

### Post by RJ12 on 2009-06-21
> **twrock said:**
> I used this modified workaround. Maybe it's a little simpler for some of us newbies than figuring out the Windows machine's IP address.

Click Main Menu>System>Administration>Printing
Click New>Network Printer>Windows Printer via SAMBA
Hit the "Browse" button. "SMB Browser" box pops up. Note the names under the headings labeled Share and Comment. (So in my case, the name under Share was MSHOME and the name under Comment was DESKTOP1.)
Cancel out of the "SMB Browser" window. Click in the entry box beside smb:// and enter those names in this form: ShareName/CommentName/
Click "Browse" again. This time the list should be populated in the "SMB Browser" popup box (after a short wait) with the names of your shared printers. Choose the one you want and proceed with the installation.
Does this work for Vista I tried but it still crashes and closes if you need the name of workgroup and computer name I can provide it also that computer has no comment

---

### Post by jhmac77 on 2009-06-22
I installed 9.04 inside windows XP(sp3) and when I tried to boot into it I got a non word with a : after it.  I tried to enter my user name and password but it did not recognize it.  What is wrong and how do I bring up Ubuntu?  The non word looked sort of like this  interxxxxxx: but nothing could be entered after this word that would work.

---

### Post by techfanboy81 on 2009-06-23
I want to upgrade my Ubuntu 8.10 version to 9.04  but I'm quite hesitant because my 8.10 version seem working so well.  I think I have to explore more about 9.04 version before doing so.

---

### Post by huntzire on 2009-06-26
Well ever since I upgraded to Jaunty I get no DVDROM avalilablity at all. All previous versions it works fine.

I even did a fresh install, and the kicker is this, dmesg reports they are in working order, but no device files.

They are both EIDE based, and ill provide documention for which ever need you wish, its a really bummer to not have DVDROM support.

AMD althon x2 64bit
3 gigs of memory
Ubuntu jaunty

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-15
not sure if its a bug as such

since upgrading the mouse no longer works straight off, have to unplug it, and then put it back in (USB) and it works fine then

also, when shutting down, just prior to switching off the onboard speaker on the MB goes nuts and makes a racket.

---

### Post by hawthornso23 on 2009-07-16
On clicking Reload:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

---

### Post by hawthornso23 on 2009-07-16
> **FIONEX said:**
> ATI driver with new Ubuntu 9.04 will give a delay when maximizing or minimizing windows.  That's due to a patch that was removed from Xorg for the sake of intel cards.  Go figure...make ubuntu less compatible with 40% of the cards in the market (ATI) in order to make it compatible with 10% of the cards?  Anyways, here's the steps to fix it.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

At step 7 , on clicking Reload:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

***** added subsequently *****
... however closing synaptic and then running update manager completed the update ... albeit with some grumbling about unsigned packages. Logged off and on. Works. Fix recipe could do with editing as process did not follow predicted path. But fix is good.

---

### Post by Tak11 on 2009-07-17
I'm affected by this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366805](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366805)

I have an hda-intel chipset, and on upgradeing to jaunty my sound breaks. I've tried every possible fix, i searched 3 days xD

anyone know a work around? =( I really want to upgrade to jaunty, but had to downgrade my system.

---

### Post by VastOne on 2009-07-17
> **quixote said:**
> Symptoms: [Bug #346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all") affects 64-bit installs and causes the system to freeze up randomly, not associated with any specific program.  A hard reset is the only way to regain control, and then the system usually won't boot because of filesystem corruption: missing or bad inodes reported, and so on.  Fsck has to be run manually from recovery mode to fix it, until the next time it blows up again.

This bug is not related to **ext4** filesystem corruption on i386, ie 32-bit installs, so the fix below is probably irrelevant in that case.

The cause appears to be the 2.6.28.11 kernel that comes with Jaunty.  The fix is to install a 2.6.29 kernel:
```

$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
$ sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
(or **_i386.deb if on 32bit**)
``` (Thanks to Daniel J. Blueman for the fix!)

I have seen the same freezes on every kernel of Jaunty and future kernels all the way to 2.6.30.1 with identical hardware or minute differences. On two duplicate machines and even a duplicate (dd'd) install, one freezes non stop and the other has never frozen one time.  The only common is that all 6 machines are 64 bit

---

### Post by quixote on 2009-07-17
Yikes.  That's even worse than my situation.  I've been running problem-free using the 2.6.29 kernel I mentioned.  Maybe I was just lucky and got the only build that worked??  More likely, some combinations of hardware are even more sensitive to this thing than others.  

What I don't understand is why the powers-that-be at Ubuntu haven't slapped big warnings everywhere, as well as on every download of 64-bit Jaunty, that this problem exists!  If you can't fix it, at least make sure everyone knows!

---

### Post by trx64 on 2009-07-20
And the bug in fonts in QT4 apps?

---

### Post by mr_steve on 2009-07-22
["Empty trash" button still disabled when trash contains files.]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/376445")
Workaround: Empty trash by right-clicking on the trash applet

                   [NetworkManager Internet Connection Sharing fails to route DNS]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006")
Workaround: Manually set DNS server addresses on connected computers

---

### Post by sara_foster1 on 2009-08-07
Facing same problem ?

---

### Post by dmparksa on 2009-08-12
Hi! I'm having a really big problem with booting up the device and getting in to any programs.  I know that this post is for bugs and it's fixes, but i couldn't find this one anywhere, so i'm posting it here to ask for help.  when I turn on ubuntu, I get the log on screen and all, but after i log in, and click something, it just freezes.  the mouse moves around, but clicking doesn't work at all.  It first happended when i tried to customize some compiz settings, but now everytime i turn it on and click something, it freezes up.  I even started in safe mode, but it still doesn't work it would really be helpful if you guys can figure it out for me thank you.:P

---

### Post by dmparksa on 2009-08-13
I know that i'm not suppose to write only bugs here, but i couldn't figure it out.  I currently have windows xp and ubuntu dual booted to my laptop, because my xp caught virus, and couldn't figure it out, so i installed ubuntu with the live cd.  few days later an update came up, and i installed the beta version of 29.11.  it turns out there is a really big problem with the beta version.  unfortunately, i can't access terminal in the ubuntu, because it freezes every time i log in.  and i can't reinstall ubuntu, because my cd rom is really messed up.  any solutions for me? and yes the bug is 29.11 not working correctly and it always freezes up

---

### Post by CJ_Hudson on 2009-08-13
It's not really a bug and I've mentioned it elsewhere but thought it appropriate to mention here that my mail loads really slowly in Evolution Mail when, and only when, using my Apple 'Mobile Me' (used to be 'dot-Mac') account. I think this is solely because Ubuntu checks each e-mail very thoroughly for viruses (etc.)
It sometimes took 2-3 minutes to load one e-mail (obviously with pictures in it) so I have given up on Evolution for the mo and currently get into my Mobile Me account using my web browser (Firefox). It is roughly 5-20 times faster!
Also there is an error when uploading files to the picture gallery on my Mo. Me webspace when using Ubuntu. It gets to the end of the upload then hangs indefinitely and then reports an error.
Could anyone help? Sorry I too have just noticed you're not supposed to write just bugs here.

---

### Post by Cavsfan on 2009-08-19
> **quixote said:**
> Symptoms: [Bug #346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all") affects 64-bit installs and causes the system to freeze up randomly, not associated with any specific program.  A hard reset is the only way to regain control, and then the system usually won't boot because of filesystem corruption: missing or bad inodes reported, and so on.  Fsck has to be run manually from recovery mode to fix it, until the next time it blows up again.

This bug is not related to **ext4** filesystem corruption on i386, ie 32-bit installs, so the fix below is probably irrelevant in that case.

The cause appears to be the 2.6.28.11 kernel that comes with Jaunty.  The fix is to install a 2.6.29 kernel:
```

$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
$ sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
(or **_i386.deb if on 32bit**)
``` (Thanks to Daniel J. Blueman for the fix!)

I tried this as I thought I should as I am running Ubuntu 9.04 64 bit.
I received this error when I ran the first command - $wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb:]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb:") [B]No such file or directory

[/B]Thanks!

---

### Post by jeffmodern on 2009-09-10
Please can anybody out there help me out with this problem.
Am on ubuntu 9.04, just woke up this morning, switched on my laptop and then was hit with this problem. 
I have worked around it but can't get it done. I already have the folder "mysqld" but its empty, can't find the file "mysqld.sock"
Am suspecting out-of-date issue here, coz i've not updated/upgrade for like 75 days now due to proxy issue as well, it tells me this:

okoroaforje@mysticalrose:~$ apt-get update;apt-get upgradeE: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
okoroaforje@mysticalrose:~$ sudo apt-get update;sudo apt-get upgrade
[sudo] password for okoroaforje: 
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB              
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                  
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB
  Could not resolve ‘proxy.aust-abuja.org’
Reading package lists... Done          
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/Release.gpg](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/Release.gpg)  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘proxy.aust-abuja.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
okoroaforje@mysticalrose:~$ 

I have as well tried fixing this problem but naah, it refused.
I should be very grateful if you help me out. Thanks guys:confused:

---

### Post by chefbodini on 2009-09-18
The firmware for the keyspan usb serial adapters has been removed again.  Here's a quick work around:

This worked like a dream and here's the steps:

1. Download the [rpm]("http://rpm.pbone.net/index.php3/stat/4/idpl/12397182/com/kernel-firmware-2.6.29.1-1.rt4.1.fc10.ccrma.noarch.rpm.html")
2. Install alien
   $ sudo apt-get install alien
3. Build a .deb from the .rpm
   $ sudo alien -k kernel-firmware-2.6.29.1-1.rt4.1.fc10.ccrma.noarch.rpm
4. Install the .deb
   $ sudo dpkg -i kernel-firmware_2.6.29.1-1.rt4.1.fc10.ccrma_all.deb

At this point, I just had to plug in my keyspan 49wlc and I now have 4 new serial ports.

$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2009-09-18 15:29 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2009-09-18 13:49 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2009-09-18 13:49 /dev/ttyUSB2
crw-rw---- 1 root dialout 188, 3 2009-09-18 13:49 /dev/ttyUSB3

Full procedure at my [blog]("http://webcave.us/node/468").

---

### Post by zaduma on 2009-09-18
There is a bug currently for people with RT2500 wifi cards, not having their rate be set correctly, a work around for this is to put the following in /etc/rc.local

iwconfig wlan0 rate 54M
iwconfig wlan0 rate fixed

make sure to replace wlan0 with your device name

---

### Post by razor180 on 2009-09-18
not sure if I can post bugs here but here goes

BUG: When I use the force quit, yes it quits the application I select, but then I can't open, close, or modify applications (modifications I consider are saving files). I also can't use ubuntu to shut off/restart my pc, when I get to the prompt, it will freeze when I select an option, so I have to hard reset.

---

### Post by sraebymmug on 2009-10-01
Bug #318942   -  No sound on hp mini 1000

This work around works for hp mini 1116nr.  I haven't seen anyone post for this model yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/44)

More than likely you'll have to unmute every time that you reboot... to fix that:


[LIST=1]
[*]Get the volume settings exactly the way you want them.
[*]Paste the command *sudo alsactl store* into the terminal.
[*]Edit the /etc/rc.local file as root (*sudo nano -B /etc/rc.local*) and then add in the line *alsactl restore* before *exit 0*
[/LIST]

---

### Post by benbc on 2009-10-20
I suggest using the workaround described here. It ensures that nothing can be corrupted because you never have to run the buggy system.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122)

---

### Post by drewsus on 2009-10-20
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/)

Sometimes when I try to hibernate I get a long list of outputted errors consisting of "Write-error on swap-device"

Turns out that it has to do with compcache being enabled. You can disable it as follows (the bugreport just says to put sudo in front of the command, but I found that gave me problems, so I did it with sudo su first as shown below:

```
sudo su
rm -f /usr/share/initramfs-tools/conf.d/compcache && update-initramfs -u
exit
```

I originally read about this here:
[http://administratosphere.wordpress.com/2009/07/19/disabling-compcache-in-ubuntu-jaunty-and-related-swap-errors/](http://administratosphere.wordpress.com/2009/07/19/disabling-compcache-in-ubuntu-jaunty-and-related-swap-errors/)

So far this has fixed this issue for me!
dRewsus

---

### Post by flipper9 on 2009-11-01
I tried to create a new thread in this forum for help on a compiz error I am getting in Karmic, but the thread doesn't show up and no error message is generated.  Any ideas?

---

### Post by Puzzled Guy on 2009-11-21
BUG:
YouTube Videos won't play properly or not at all

WORKAROUND:
Use:
```
sudo apt-get ubuntu-restricted-extras
```

Hope this can help anyone besides me!

---

### Post by rvndrk3233 on 2009-12-09
> **paperplate9 said:**
> **Bug**: automatic updates checking not working after upgrade from Intrepid to Jaunty. `apt-get update` or update-manager 'check' works fine, however, but are manual operations.

**Launchpad**: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

**Reason**: /etc/cron.daily/apt script incorrectly chmod'ed as 644 aka not executable

**Fix**: # chmod 755 /etc/cron.daily/apt ... reboot; might help to remove /var/spool/anacron/cron.daily

well... I find that manually hitting refresh solves the issue, even though 'it says' it is 'up to date'.
I didn't need to mess with the script.Hit refresh a few times.

---

### Post by Red Dane on 2010-02-07
Hello"
I have a Dell inspiron B130 Laptop I had Window's xp in it and I hda it wiped off this computer! a friend showed me ubuntu and I liked it and installed it so I thought? the
problem is I dont have Drivers that the computer recognizes? If I try to down load and install it say's earror systeem not recognized ? what o I do? where do I go? please help....

---

### Post by TheOnlyMrK on 2010-02-14
_**BUG:**_ Interacting with flash on websites does not work on Ubuntu 64bit with normal Adobe Flash Player installer (flashplugin-installer).

_**FIX:**_
1. Download Adobe Flash Player **64bit** here [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
2. Uninstall "flashplugin-installer"
          ----1. Open a terminal and type "sudo apt-get remove flashplugin-installer"
          ----2. Type your password, wait for it to finish, then close the window.
3. Extract it to "/usr/lib/mozilla/plugins".
          ----1. Open a terminal and type "sudo nautilus".
          ----2. Navigate to the folder you downloaded the file.
          ----3. Right click it and select "Open with Archive Manager".
          ----4. Go to "File" then "Extract...".
          ----5. Navigate to "/usr/lib/mozilla/plugins" then click "Extract".

---

### Post by donfisico on 2010-02-26
Hi, I have a Dell Laptop, Core 2 processor and intel graphic card. I have installed Jaunty 64 bits recently. I have not experience the problems with my graphic mentioned here, but I have another very annoying problem: sometimes the Tab key actives by itself, then making me misstyping or activating things I did not have the intention to do. I have wrote a post [here]("http://ubuntuforums.org/showthread.php?t=1410026") but nobody answered me. You can not imagine how annoying can be this problem. I do not know if it is a problem of the keyboard, the mouse, some bad configuration of hardware or just a bug of Jaunty. Can somebody give me some clue or tell me if it is a bug the workaround? Thanks in advance!!

---

### Post by donfisico on 2010-03-03
I do not know why my post asking if my problem (tab key "automatic" and randonmly activated) was a bug, was deleted from this thread. My question was serious and I still have the problem. Please notify me if I have make any violation to any rule of the forum because I do not see how I dit it. Seriously!

---

### Post by TheOnlyMrK on 2010-03-03
> **donfisico said:**
> I do not know why my post asking if my problem (tab key "automatic" and randonmly activated) was a bug, was deleted from this thread. My question was serious and I still have the problem. Please notify me if I have make any violation to any rule of the forum because I do not see how I dit it. Seriously!
This thread is for posting **workarounds** for bugs, not asking how to fix a bug, if you are having a problem that is not listed here you should make your own thread and ask there.

---

### Post by donfisico on 2010-03-03
> **TheOnlyMrK said:**
> This thread is for posting **workarounds** for bugs, not asking how to fix a bug, if you are having a problem that is not listed here you should make your own thread and ask there.
Thank you very much for explaining that I promise that I would not post anything here **unless is a WORKAROUND** to a bug. Anyway I have to point out that I have made [my own thread ]("http://ubuntuforums.org/showthread.php?t=1410219")asking and detailing my problem but NOBODY answered it. It is **not my itention** to **post in threads in wich I have nothing to say.** If I have commited such a mistake here was due to that and thinking *wrongly* that my [problem]("http://ubuntuforums.org/showthread.php?t=1410219") may be a bug of Jaunty and **there would be a WORKAROUND **for it. It is very frustrating when you know you have a problem, you post a thread describing it and nobody answers you (I would be please if anybody answers me anything, at this point I do not care if the answer is something like "your thread is silly"!!).

---

### Post by saunders7777 on 2010-03-15
I am having problems posting a question and am hoping to receive some assistance.  Sorry that this is off topic here but I can't seem to find another way to receive help.  I may have even started off incorrectly.  What I did was to start off by pressing a link called New Thread on the general questions page.  I entered a questions and tried to send it but was asked for a title to the message and I cannot find a place to enter a title anywhere on the page.  Could anyone help?  If someone does respong could I ask that a response be sent to [EMAIL="evas@mountaincable.net"]evas@mountaincable.net[/EMAIL].
 
Regards
Chris Saunders

---

### Post by Elfy on 2010-03-15
> **saunders7777 said:**
> I am having problems posting a question and am hoping to receive some assistance.  Sorry that this is off topic here but I can't seem to find another way to receive help.  I may have even started off incorrectly.  What I did was to start off by pressing a link called New Thread on the general questions page.  I entered a questions and tried to send it but was asked for a title to the message and I cannot find a place to enter a title anywhere on the page.  Could anyone help?  If someone does respong could I ask that a response be sent to [EMAIL="evas@mountaincable.net"]evas@mountaincable.net[/EMAIL].
 
Regards
Chris Saunders

[http://ubuntuforums.org/showpost.php?p=4526971&postcount=2](http://ubuntuforums.org/showpost.php?p=4526971&postcount=2)

---

### Post by RaizenLegend on 2010-03-19
Hi forum, i recently became a ubuntu fan. My favorite online game is runescape and i like playing it in full screen but when i put it in full screen it makes the screen so big  it looks a little fuzzy and my desktop panels are visible. In windows vista when i made it full screen the game screen takes the whole monitor screen and the size it was 1920x1080 for ubuntu it is still 1920x1080 why does it make it look bigger and the panels shows?????? oh and runescape HD  doesn't work, every time i open it the screen goes blank i already tried turning desktop effects off but it doesnt fix it and i don't need a video card because it was working fine for vista. how do i fix all this, i really like ubuntu 9.10 and i don't wanna go back to vista. can someone  please explain how to fix all this :P-------->(STEP BY STEP)<------- /home/raizenlegend/Documents/Screenshot.png:P:P:P:P

---

