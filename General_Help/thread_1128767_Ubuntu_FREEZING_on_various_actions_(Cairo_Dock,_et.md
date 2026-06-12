---
title: "Ubuntu FREEZING on various actions (Cairo Dock, etc)"
date: 2009-04-17
forum: General Help
---

### Post by Mike_IronFist on 2009-04-17
Well, I switched to the Jaunty RC (doing a fresh install). I was getting sick of Intrepid freezing on me for random things and the problem seemed to be solved with Jaunty. Now the only thing that causes any freezes is when I try to edit my Cairo-Dock. On earlier installs I'd get freezes from other weird things (using an incompatible theme, trying to delete stuff in the trash by highliting a group of stuff and pressing "delete") 

If it's any clue, the lockups are PURELY graphical. Most of the time I can move the mouse, and once it locked up when I was burning a disc. However when my disc drive stopped moments later, I found my disc successfully burned. (As in I hard reset and put it in, and found out it had burned perfectly and was totally usable.) From this I assume the system is still functioning when my desktop locks up, despite the gui freezing up entirely.

Here's the output from the lspci command.

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

Please help me. I love Ubuntu but it's been so cruel to me.

---

### Post by Mike_IronFist on 2009-04-18
Bump. Please, I need serious help with this. If I don't get this solved it might drive me back to Windows.

---

### Post by Mike_IronFist on 2009-04-18
I'm going to keep bumping until I get a some help. This is a SERIOUS PROBLEM. Someone help me?

---

### Post by Mike_IronFist on 2009-04-18
So once again. Stop ignoring me people. BUMP.

---

### Post by Shazaam on 2009-04-18
How much memory (ram) do you have? Do you have the correct video card drivers installed?

---

### Post by brendan4linux on 2009-04-18
+1 to the previous post - does it ever freeze in windows, or just during this specific function in Ubuntu?  It doesn lead me to believe something is messed up with your video card/drivers as well.  When it freezes up, are you able to press CTRL+ALT+F3 and get to a console prompt?

If you expect immediate attention, I would purchase some kind of support, or yes, go back to windows, if that's what works for you.

---

### Post by balaknair on 2009-04-19
Hello Mike_IronFist

The reason you're not getting any replies may be because no-one who's seen your post here knows how to fix the problem, and because with Jaunty you'd be better off posting in the Jaunty testing and discussion forum rather than in the general help section.
[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

Re: your problem with Compiz+Cairo-
 I've been using/testing Jaunty for a while now, had similar issues with Compiz on nVidia 8400GS(pressing Alt-tab with Compiz widget layer enabled would freeze the GUI, though stuff would go on in the background, music would continue to play, and the only way out was with a hard reset). With recent updates however, most issues have been resolved, so you might want to try running *sudo apt-get update && sudo apt-get dist-upgrade* and restart the system.
The bug, it seems was with the nVidia drivers
[http://ubuntuforums.org/showthread.php?t=1107581](http://ubuntuforums.org/showthread.php?t=1107581)


Alternative- If you don't use funky Compiz effects like 3D cubes, wobbly windows and widget layer, disable Compiz and use Metacity Compositing, it works just fine for Screenlets, Cairo dock, Gnome-Do and Avant Window Navigator.
In a terminal type *gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true*

---

### Post by Mike_IronFist on 2009-04-22
> **balaknair said:**
> Hello Mike_IronFist

The reason you're not getting any replies may be because no-one who's seen your post here knows how to fix the problem, and because with Jaunty you'd be better off posting in the Jaunty testing and discussion forum rather than in the general help section.
[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

Re: your problem with Compiz+Cairo-
 I've been using/testing Jaunty for a while now, had similar issues with Compiz on nVidia 8400GS(pressing Alt-tab with Compiz widget layer enabled would freeze the GUI, though stuff would go on in the background, music would continue to play, and the only way out was with a hard reset). With recent updates however, most issues have been resolved, so you might want to try running *sudo apt-get update && sudo apt-get dist-upgrade* and restart the system.
The bug, it seems was with the nVidia drivers
[http://ubuntuforums.org/showthread.php?t=1107581](http://ubuntuforums.org/showthread.php?t=1107581)


Alternative- If you don't use funky Compiz effects like 3D cubes, wobbly windows and widget layer, disable Compiz and use Metacity Compositing, it works just fine for Screenlets, Cairo dock, Gnome-Do and Avant Window Navigator.
In a terminal type *gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true*
Thank you. I'll give all that a look.

---

### Post by Piraja on 2009-04-23
There seem to be quite a few people reporting ramdom freezes on Jaunty ([here]("http://ubuntuforums.org/showthread.php?t=1132204") for instance is a closed thread), including me.

A few moments ago I decided to disable all desktop effects (Preferences > Appearance ... or metacity --replace) and use **Xcompmgr instead of Compiz** to get transparency. So far so good. Might be worth trying, and it's always a good idea to see if there are bug reports about the issue at Launchpad.

---

### Post by ar0n on 2009-04-26
I solved the problem by installing the newest nvidia drivers.

In syslog I found a lot of similar lines:
```

NVRM: Xid (0002:00): 6, PE0000 1248 00f8f8f3 0000fdc4 00f8f8f3 00f8f8f3

```

Looks like it was posted when the freezing occurred.

Go to this link and add the repositories listed:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

or manually download and install the pkgs listed here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

---

### Post by SigmaSanti on 2009-04-27
I have had many problems with my nvidia 8200, most which have been fixed in newer and newer nvidia drivers.
Jaunty has been unstable for me also, with random crashes when resizing windows with flash player, notifications appearing over windows, and many more. 
Thanks for starting this thread, I will report back if any of this stuff helps.

---

