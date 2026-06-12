---
title: "Urgent: No Option to Boot to Ubuntu on Start-up"
date: 2006-07-20
forum: Desktop Environments
---

### Post by shivari on 2006-07-20
I just installed Ubuntu 6.06, but when I boot-up there's no option to boot into Ubuntu like in previous versions.  My computer would automatically boot into XP.  No other OS is displayed.

My XP is in disk 1 partition 1
Ubuntu is in disk 1 parition 2

Is there a way to add ubuntu in the windows boot.ini file?

This is the XP boot.ini (ignore spaces in Windows and Microsoft, etc., just the forum)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=AlwaysOff

---

### Post by philippe_carlo on 2006-07-20
I suspect you did not install grub onto the mbr. Booting with the live cd and running grub-install on /dev/hda should get you going again, I think.

---

### Post by shivari on 2006-07-20
How do I do that, I can't access Ubuntu in XP?  Do i boot with the CD.

I don't have a Livecd.  The 6.06 I have is downloaded and then burned into a CD.

---

### Post by Malac on 2006-07-20
[SIZE=2][COLOR=Black]You will first need a bootable dos disk with fdisk on it.
FreeDOS fdisk (can be downloaded, google for it) is a lot better than MS fdisk IMHO
Boot off this then set partition 2 as active.
I think this is option 2 on the main menu in fdisk.
Remove Floppy
Once that is done do this:
Reboot, you should enter into Ubuntu and login
-------------------------------------------
[/COLOR][/SIZE][FONT=Verdana][SIZE=2][COLOR=Black]If for some reason you have not got GRUB loaded on /dev/hda2 you wil need to install it in Ubuntu:
Open Terminal, type:
[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=Black]```
sudo GRUB
``` at the GRUB> prompt type:
[/COLOR][/SIZE][SIZE=2][COLOR=Black]```
root (hda0,1)
setup (hda0,1)
quit
``` ---------------------------------------------[/COLOR][/SIZE]
[SIZE=2][COLOR=Black]open a terminal and type :
```
df
``` this should show you were /boot is
in your case probably /dev/hda2
Then ```
mkdir win
sudo mount /dev/hda1 /home/
```[/COLOR][/SIZE]```
[COLOR=Red]*yourusername*[/COLOR][SIZE=2][COLOR=Black]/win[/COLOR][/SIZE]
[FONT=Verdana][SIZE=2][COLOR=Black]dd if=/dev/hda2 of=[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=Black]/home[/COLOR]/[/SIZE][COLOR=Red]*yourusername*[/COLOR]/[FONT=Verdana][SIZE=2][COLOR=Black]win/BOOTSECT.UBU bs=512 count=1[/COLOR][/SIZE][/FONT]

```[SIZE=2][COLOR=Black]
Reboot to floppy disk
Reset Active partition to 1
Remove Floppy.
Reboot into WindowsXP.[/COLOR][/SIZE][COLOR=Black][SIZE=3][FONT=Verdana]
[/FONT][/SIZE][/COLOR][SIZE=2][COLOR=Black]Insert the DOS floppy disk
Copy the BOOTSECT.UBU file from A:\ to C:\
Open the System Properties window
Click the Advanced tab
Under Startup and Recovery, click Settings
Click Edit to open the boot.ini file in Notepad
Add this line to the end of the file and save:
C:\BOOTSECT.UBU="Ubuntu 6.06 LTS"
Close the Startup and Recovery settings, open it again, and Linux should now
appear in the operating system drop-down menu.
[/COLOR][/SIZE][FONT=Verdana][SIZE=2][COLOR=Black]Reboot and test it out.

[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Black]Hope this helps.
[/COLOR][/SIZE][/FONT]

---

### Post by shivari on 2006-07-20
I'm sorry.  Unfortunately I don't have a floppy drives or disks.

---

### Post by sp4zzj4zz on 2006-07-20
I used a USB pen drive to copy the boot sector. Im sure you could also use a USB hdd too.

---

### Post by shivari on 2006-07-20
My external hard drive is being used for back-ups.  I can't reformat it.  I don't have a usb flash.

with Ubuntu 5.10, i was able to boot to linux.  i should have just done an upgrade instead of a clean install.

---

### Post by shivari on 2006-07-20
Ubuntu and XP are installed on a sata drive, but for some reason to boot to Ubuntu I have to select the PATA drive in bios and to boot to XP i have to select SATA drive in bios as my boot device.  Why did Ubuntu install boot files in the PATA drive instead of the SATA drive which is where I installed ubuntu?

---

