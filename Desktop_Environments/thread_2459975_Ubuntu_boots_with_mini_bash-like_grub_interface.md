---
title: "Ubuntu boots with mini bash-like grub interface"
date: 2021-03-30
forum: Desktop Environments
---

### Post by Feddy on 2021-03-30
I have both ubuntu 18.04 and windows 10 on my computer (gigabyte aorus wifi z390). From few weeks ago (probably after a system update, don't remember clearly), the  computer always boots to the command line. The only way I can do to go  to regular boot option screen is to first get into BIOS and then exit.  How can I avoid doing this everytime?

---

### Post by CatKiller on 2021-03-30
It sounds like your UEFI is trying to boot the wrong bootloader (Windows update changing the order, maybe?) or is booting in the wrong mode - Legacy/CSM vs UEFI or vice versa. Those are the things I'd check first. Also that RAID hasn't been enabled instead of AHCI, and that Windows hasn't re-enabled Fast Startup.

---

### Post by yancek on 2021-03-31
You make reference to a 'system update' but do not indicate which system (Ubuntu or windows) you did the update on?
You say the computer always boots to a command line, what exactly do you see and is this attempting to boot Ubuntu or windows or both?
Were you previously able to boot both Ubuntu and windows and if so, was it from the Grub bootloader?
Can you run from Ubuntu:  sudo efibootmgr -v and post this output?

---

### Post by Feddy on 2021-04-01
> **CatKiller said:**
> It sounds like your UEFI is trying to boot the wrong bootloader (Windows update changing the order, maybe?) or is booting in the wrong mode - Legacy/CSM vs UEFI or vice versa. Those are the things I'd check first. Also that RAID hasn't been enabled instead of AHCI, and that Windows hasn't re-enabled Fast Startup.

Well, I didn't change boot order in bios. Will check the booting mode. I don't have RAID so never touch the option in bios.

---

### Post by Feddy on 2021-04-01
> **yancek said:**
> You make reference to a 'system update' but do not indicate which system (Ubuntu or windows) you did the update on?
You say the computer always boots to a command line, what exactly do you see and is this attempting to boot Ubuntu or windows or both?
Were you previously able to boot both Ubuntu and windows and if so, was it from the Grub bootloader?
Can you run from Ubuntu:  sudo efibootmgr -v and post this output?

Please see the screenshot.
 [IMG]https://i.ibb.co/yBXdL1c/grub.png[/IMG]

Previously I was able to see the grub boot menu and select either Ubuntu or Windows from there.

The command returns:
```

root@big9:~# efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0000,0004,0006
Boot0000* Windows Boot Manager    HD(2,GPT,f2d5f829-72e5-4dcb-b4f3-27018a7f3d10,0x109000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0002* ubuntu    HD(2,GPT,f2d5f829-72e5-4dcb-b4f3-27018a7f3d10,0x109000,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0004* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/USB(3,0)/USB(0,0)/HD(1,MBR,0x0,0x20,0x1dd17e0)..BO
Boot0006* UEFI: HTTP IP4 Intel(R) Ethernet Connection (7) I219-V    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(b42e99a42f16,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO

```

---

### Post by yancek on 2021-04-02
You are not answering the questions.  First question I posted was which systems was the update on, no answer.  Correct answer would be Ubuntu, Windows or don't know.  Which was it?

In your initial post, you indicate that you are able to boot by going into the BIOS and then exiting.  That makes no sense to me as it would seem necessary to do something while in the BIOS before exiting.  What do you do?  The output of efibootmgr you posted shows that you have efi entries for Ubuntu (Boot0002) and windows (Boot0000).  When you select either of these in the BIOS, are you able to boot that specific OS?

---

### Post by Feddy on 2021-04-07
> **yancek said:**
> You are not answering the questions.  First question I posted was which systems was the update on, no answer.  Correct answer would be Ubuntu, Windows or don't know.  Which was it?

In your initial post, you indicate that you are able to boot by going into the BIOS and then exiting.  That makes no sense to me as it would seem necessary to do something while in the BIOS before exiting.  What do you do?  The output of efibootmgr you posted shows that you have efi entries for Ubuntu (Boot0002) and windows (Boot0000).  When you select either of these in the BIOS, are you able to boot that specific OS?

Sorry for having missed your first questions. I definitely updated Ubuntu, I also updated Windows, likely.

I know it doesn't make sense. What I do now to boot the system is, exactly: 
[LIST=1]
[*]press the power button; 
[*]press F2 or Del to enter BIOS; 
[*]press Esc and Enter to exit BIOS without saving; 
[*]select either Ubuntu or Windows from the Grub screen. 
[/LIST]
I do nothing in BIOS. If I don't enter BIOS, it won't bring up the Grub menu, instead it shows the mini bash like command line interface. This happens when I select Ubuntu as the first boot option in BIOS.

When I select Windows as the first boot option, the computer boots with Windows smoothly.

---

### Post by tea for one on 2021-04-08
Do you know the location of your EFI partition?

As a **suggestion**, it may be worth a shot at restoring grub to the EFI partition in a running session (not a live session).

If you follow your own procedure to boot into Ubuntu, here is the terminal command:-

```
sudo grub-install --efi-directory=/boot/efi /dev/[COLOR="#0000FF"]sda1 [/COLOR]
```

Your partition may not be sda1, if your drive is nvme, it may be nvme0n1.

If there is no error message, then run
```
sudo update-grub
```

**Before** attempting this, if your are unsure of your EFI location, please post here the output of:-
```
sudo parted -l
```

---

### Post by yancek on 2021-04-10
Your efibootmgr output shows entries for Ubuntu and windows but that is minimal information.  If you did an update on Ubuntu it should have run update-grub, do you remember if it did?  If not try that.   Otherwise I would suggest you get the boot repair software from the link below and use the 2nd option described on the page to download it and when you run it, use ONLY the Create BootInfo Summary option so you don't mess things up more than they currently are and then post the output you get here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

