---
title: "Ro resume from suspend and no grub menu"
date: 2024-11-20
forum: Desktop Environments
---

### Post by Autodave on 2024-11-20
New machine running Win11.  2TB nvme.  I installed Xubuntu on a partition of 200G.  Win11 is still good and machine boots to Win11.  Grub does not appear at all.  I can boot into Xubuntu 24.04 by going into the boot menu and picking it.  Don't know if this is related, but once Xubuntu goes into suspend more, it will not wake up.  All that I get is a cursor in the middle of the screen.  I can move the pointer around, but that's all.

---

### Post by Bashing-om on 2024-11-20
Autodave :D

Just a thought - as UEFI Bios booting is not compatible.
Did you install Xubuntu in bios mode ?
Boot Xubuntu and execute:
```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

```
will tell you if you're booted via UEFI - or Not.

[INDENT]Maybe - Oh Noes
[/INDENT]

---

### Post by Autodave on 2024-11-20
~$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
UEFI

---

### Post by Bashing-om on 2024-11-20
Autodave; Well :D

Next thought - what does grub think ?
```

sudo update-grub

```

[INDENT]in the process ...[/INDENT]

---

### Post by Autodave on 2024-11-20
Nope....booted right inti Win11.....no grub.

---

### Post by Bashing-om on 2024-11-20
Autodave
```

efibootmgr -v

```

Show an entry for Ubuntu ?

[INDENT]which way did he go, George[/INDENT]

---

### Post by tea for one on 2024-11-21
> **Autodave said:**
>  Grub does not appear at all.  I can boot into Xubuntu 24.04 by going into the boot menu and picking it.
Can you show us /etc/default/grub?

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"]# Do you have this line?[/COLOR]
```

---

### Post by Autodave on 2024-11-21
> **Bashing-om said:**
> Autodave
```

efibootmgr -v

```

Show an entry for Ubuntu ?
[INDENT]which way did he go, George[/INDENT]


$ efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Windows Boot Manager    HD(1,GPT,58fb5917-c613-4d4a-a5eb-02853a459bef,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d000000f0170100000010000000040000007fff0400
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 17 59 fb 58 13 c6 4a 4d a5 eb 02 85 3a 45 9b ef 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
    data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 f0 17 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0001* Ubuntu    HD(1,GPT,58fb5917-c613-4d4a-a5eb-02853a459bef,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 17 59 fb 58 13 c6 4a 4d a5 eb 02 85 3a 45 9b ef 02 02 / 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
dave@dave-GamingPC:~$

---

### Post by Autodave on 2024-11-21
> **tea for one said:**
> Can you show us /etc/default/grub?

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR=#0000FF]# Do you have this line?[/COLOR]
```

I have that line:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
#GRUB_DISABLE_OS_PROBER=false

---

### Post by tea for one on 2024-11-21
> **Autodave said:**
> I have that line:
Indeed, you do.
```
#GRUB_DISABLE_OS_PROBER=false
```
But the line has the comment symbol [COLOR="#0000FF"]#[/COLOR], which renders it inactive.
Can you remove the comment symbol and update-grub?

Also, change the following:-
```
GRUB_TIMEOUT_STYLE=menu # change hidden to menu 
GRUB_TIMEOUT=5 # change 0 to 5
```

---

### Post by Autodave on 2024-11-21
What or how do I edit that?  Everything that I have tried tells me that it is read only and I don't have permission.  I tried emacs and gedit....no good.  Tried editing it in a terminal and couldn't.

---

### Post by yancek on 2024-11-21
Your efibootmgr output in post 8 shows entries for both windows and ubuntu and the boot order shows windows as first so if you want to boot from Grub, both Ubuntu and windows, you need to change that entry to put Ubuntu first.  Updating Grub isn't going to help if you don't boot with it.

---

### Post by tea for one on 2024-11-21
> **Autodave said:**
> What or how do I edit that?  Everything that I have tried tells me that it is read only and I don't have permission.  I tried emacs and gedit....no good.  Tried editing it in a terminal and couldn't.
You will need elevated privileges.
```
sudo nano /etc/default/grub

```Make your changes, Ctrl o to save and Ctrl x to exit, then
```
sudo update-grub
```

---

### Post by Autodave on 2024-11-21
And exactly how do I put Ubuntu first?  I really don't want to screw up Windows.....or Xubuntu.

---

### Post by tea for one on 2024-11-21
> **Autodave said:**
> And exactly how do I put Ubuntu first?  I really don't want to screw up Windows.....or Xubuntu.
In either your UEFI settings or PC Boot menu (not grub), can you put Xubuntu/Ubuntu in pole position?

---

### Post by Autodave on 2024-11-21
In either your UEFI settings or PC Boot menu (not grub), can you put Xubuntu/Ubuntu in pole position? 				

Nope.

---

### Post by yancek on 2024-11-21
I don't see anything in your posts indicating what manufacturer your hardware is.  On some, you should be able to use efibootmgr to set and change the order.  The page at the link below discusses it and the last post in the thread gives an example that worked.  Change it to suit your computer.

[https://bbs.archlinux.org/viewtopic.php?id=268349](https://bbs.archlinux.org/viewtopic.php?id=268349)

---

### Post by Autodave on 2024-11-21
The MB is an MSI.  Both Win and Xubuntu are on the same nvme 2T.

I read through that link you gave and I would have NO idea where to start.

---

### Post by tea for one on 2024-11-22
> **Autodave said:**
> In either your UEFI settings or PC Boot menu (not grub), can you put Xubuntu/Ubuntu in pole position? 				
Nope.
When you access your UEFI settings (MSI), do you have:-
Boot Option 1 UEFI Hard Disk > UEFI Hard Disk Drive BBS Priorities (or similar)?

---

### Post by yancek on 2024-11-22
>  I read through that link you gave and I would have NO idea where to start. 				

If you are referring to the link I posted (post 17) it is the last post which has an example entry which you could have used and changed it to suit your computer.  Since you currently have windows first (Boot0000) you simply need to change it to put Xubuntu (Boot0001) first as below.  You can add all the other entries shown but I don't think it 
would be necessary.

```
sudo efibootmgr -o 0001,0000
```

That is a lower case Letter -o in the command above for 'order'.  You should not need the Boot part shown in the efibootmgr output nor should you include the asterisk and do not put spaces after the comma for entries.  If this does not work, post back with the exact output results.  You still haven't indicated what hardware manufacturer you have but I will say that efibootmgr is not likely to change the boot order on an HP device.

---

### Post by Autodave on 2024-11-22
This is a Cyberpower desktop, MSI MB, 2t nvme, RTX 4080 super.  Dunno what else I can tell you.

---

### Post by Autodave on 2024-11-22
The sudo efibootmgr didn't work.

---

### Post by Autodave on 2024-11-25
bump

---

### Post by Dennis N on 2024-11-26
> **Autodave said:**
> The sudo efibootmgr didn't work.

I also have an MSI system that does not change the boot order with efibootmgr. You need to change it in the UEFI bios. The image attached shows where that's done in the Advanced settings, bottom center of the screen where you see "Fixed Boot Order".

---

### Post by tea for one on 2024-11-26
@ Dennis N
Your image shows Boot Option #1 UEFI Hard Disk - Do you click this to access UEFI Hard Disk Drive BBS Priorities?

I don't have an MSI device but I have a Mini PC where the UEFI settings have a similar structure (BBS Priorities) to prioritise the choice of OS.

---

### Post by Dennis N on 2024-11-26
> **tea for one said:**
> @ Dennis N
Your image shows Boot Option #1 UEFI Hard Disk - Do you click this to access UEFI Hard Disk Drive BBS Priorities?

I don't have an MSI device but I have a Mini PC where the UEFI settings have a similar structure (BBS Priorities) to prioritise the choice of OS.

You would click on "Boot Option #1" and a select dialog pops up and you choose which OS you want to boot first. Then you repeat for "Boot Option #2", and as many as you want to set. You don't have to set all the Boot Options.

That image is not my computer. Its from Google Image Search. But the screen in the photo is the same as mine.

In post #21, you mention "MSI MB" = MSI Motherboard?

---

### Post by Autodave on 2024-11-26
> **Dennis N said:**
> I also have an MSI system that does not change the boot order with efibootmgr. You need to change it in the UEFI bios. The image attached shows where that's done in the Advanced settings, bottom center of the screen where you see "Fixed Boot Order".

Been there, but I don't see it.  I have tried the USB Hard Disk....putting that first, but still boots to Win11.  And nothing else there sounds correct.  What am I missing?  My screen does look exactly like your pic that you posted.

---

### Post by Dennis N on 2024-11-26
OK, that image in post #24 is not quite right. I looked at the UEFI in my computer, and correct matching images are attached below. In image 1 below, there is another section at the very bottom that says "UEFI Hard Disk Drive BBS Priorities". Click on that and you go to another screen (image 2 below) where you set the boot options for the device selected in "Fixed Boot Order".

I remember now that this setup confused me too when I had to go in there to set the order. It was a long time ago when I last did this. Sorry for the confusion.

(both images from Google Image Search)

---

### Post by tea for one on 2024-11-26
> **Dennis N said:**
> You would click on "Boot Option #1" and a select dialog pops up and you choose which OS you want to boot first. Then you repeat for "Boot Option #2", and as many as you want to set. You don't have to set all the Boot Options.

Apologies, Dennis N, I wasn't asking for help because I already understand about OS boot selection within BBS priorities.
I was trying to establish if the MSI UEFI settings were comparable to the UEFI settings in my PC.
It does seem that they are similar but not identical.

In post 19, I was trying to verify this feature with the OP

Here are my images (via a camera)

---

### Post by Autodave on 2024-11-26
OK.....found that finally and changed it....I now boot into Xubuntu.  However, I still have no grub menu....I have to pick the boot menu when booting to get to Win11.  What next?

---

### Post by tea for one on 2024-11-26
Please return to post 7 and post 10
After editing, don't forget to run ```
sudo update-grub
```

---

### Post by Autodave on 2024-11-26
It works finally!!!!!  Thanks to all of you who helped!!!!!!!!!

---

