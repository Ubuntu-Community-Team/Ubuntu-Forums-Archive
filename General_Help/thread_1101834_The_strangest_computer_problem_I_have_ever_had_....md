---
title: "The strangest computer problem I have ever had ..."
date: 2009-03-20
forum: General Help
---

### Post by Cov(enant) on 2009-03-20
So, I have a PC running the Windows Vista x86 version.

I tried to install Windows Vista x64 but all went wrong in a wired kind of way.


Here is what has happened ...

**1.** I installed Windows Vista x86 one year ago on a 1TB SATA HDD and it was working fine ever since.

**2**. Yesterday I disconnected my 1TB HDD and connected an old, empty 100GB PATA HDD where I tried to install Vista x64.

**3.** The installation process went half way through when it froze at one point. 
After having tried it unsuccessful 100 times to make it work, I then disconnected the old 100GB HDD and re-connected the 1TB HDD again, to boot up my Windows Vista x86.

**5.** I wouldn't run anymore and the following error message came up:

> Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language setings, and then click "Next".
3. Click "Repair your computer".

File: \Boot\BCD

Status: 0xc0000001

Info: An error occured while attempting to read the boot configuration data.**6.** The Vista DVD, which I used one year ago, is not bootable anymore and I don't know why.
Meaning, I cannot use this DVD to repair my installation!

**7.** I then disconnected the 1TB HDD and re-connected the old 100GB HDD and installed Ubuntu. The process went smooth and speedy.

**8**. Then I switched off the system and re-connected the 1TB SATA HDD as a secondary drive in addition to the 100GB HDD.

**9.** After booting up Ubuntu, the File Browser does find the additional 1TB HDD but when trying to access it, the following message comes up:

> Cannot mount volume.

Details:
$LogFile indicates unclean shutdown ... Mount is denied because NTFS is marked to be in use.
Choose one action:

**a.** Disconnect the external devices by clicking on the "Safely remove hardware" icon in the Windows taskbar, then shut down Windows cleanly.

**b**. If you don't have Windows then you can use the "force" option for your own resposibility.
For exmaple type on the command line: mount -t ntfs-3g/dev/sdal/media/disk -0 force

... or add the option to the relevant row in the /etc/fstab file: /dev/sda1 /media/disk ntfs-3g force 0 0**10**. My problem is how to repair the bootsector of my 1TB HDD with Vista x86, so that I can boot from it again.
Without being able to boot from the Vista DVD (Methode 1), the only other way is the way described from step 6 onwards at Methode 2:

> **Method 1: Repair the BCD store by using the Startup Repair option**

You can use the Startup Repair option in the Windows Recovery Environment to repair the BCD store. To do this, follow these steps:
[LIST=1]
[*]Put the Windows Vista installation disc in the disc drive, and then start the computer.
[*]Press a key when you are prompted.
[*]Select a language, a time, a currency, and a keyboard or another input method, and then click **Next**.
[*]Click **Repair your computer**.
[*]Click the operating system that you want to repair, and then click **Next**.
[*]In the **System Recovery Options** dialog box, click **Startup Repair**.
[*]Restart the computer.
[/LIST]


**Method 2: Rebuild the BCD store by using the Bootrec.exe tool**

If the previous method does not resolve the problem, you can rebuild the BCD store by using the Bootrec.exe tool in the Windows Recovery Environment. To do this, follow these steps:
[LIST=1]
[*]Put the Windows Vista installation disc in the disc drive, and then start the computer.
[*]Press a key when you are prompted.
[*]Select a language, a time, a currency, and a keyboard or another  input method, and then click **Next**.
[*]Click **Repair your computer**.
[*]Click the operating system that you want to repair, and then click **Next**.
[*]In the **System Recovery Options** dialog box, click **Command Prompt**.
[*]  Type Bootrec /RebuildBcd, and then press ENTER.
[LIST]
[*]If the Bootrec.exe tool runs successfully, it presents you with an installation path of a Windows directory. To add the entry to the BCD store, type Yes. A confirmation message appears that indicates the entry was added successfully.
[*]If the Bootrec.exe tool cannot locate any missing Windows installations, you must remove the BCD store, and then you must re-create it. To do this, type the following commands in the order in which they are presented. Press ENTER after each command.Bcdedit /export C:\BCD_Backup
ren c:\boot\bcd bcd.old
Bootrec /rebuildbcd
[/LIST]
 
[*]Restart the computer.
[/LIST]

**Method 3: Rebuild the BCD store manually by using the Bcdedit.exe tool**

If the previous method does not resolve the problem, you can rebuild the BCD store manually by using the Bcdedit.exe tool in the Windows Recovery Environment. To do this, follow these steps:
[LIST=1]
[*]Put the Windows Vista installation disc in the disc drive, and then start the computer.
[*]Press a key when you are prompted.
[*]Select a language, a time, a currency, and a keyboard or another input method, and then click **Next**.
[*]Click **Repair your computer**.
[*]Click the operating system that you want to repair, and then click **Next**.
[*]In the **System Recovery Options** dialog box, click **Command Prompt**.
[*]Type the following command, and then press ENTER:cd /d Partition:\Windows\System32
**Note **Partition represents the letter of the partition on which Windows Vista is installed. Typically, this is partition C.
[*]Type the following command, and then press ENTER:bcdedit /enum all
In the Windows Boot Loader section of the output from this command, note the GUID that is listed for **resumeobject**. You will use this GUID later.
[*]Type the following command, and then press ENTER:bcdedit -create {bootmgr} -d "Description"
**Note **Description represents the description for the new entry.
[*]Type the following command, and then press ENTER:bcdedit -set {bootmgr} device partition=Partition:
**Note **Partition represents the letter of the partition. Typically, the letter is C.
[*]Type the following command, and then press ENTER:bcdedit /displayorder {GUID}
**Note **GUID represents the GUID that you obtained in step 8.
[*]Type the following command, and then press ENTER:bcdedit /default {GUID}
**Note **GUID represents the GUID that you obtained in step 8.
[*]Type the following command, and then press ENTER:bcdedit /timeout Value
**Note **Value represents the time  in seconds  before the Windows Boot Manager selects the default entry that you created in step 12.
[*]Restart the computer.
[/LIST]
The questions is, can I access / modify / repair the BCD Store on the 1TB HDD via the Ubuntu platform at all ?

If you know where to go from here or have any other idea of what I could possibly try, would you mind helping me please ?

Thank you very much !


PS: This was a lesson for me not to play around when things work fine.
Once I'm able to recover Vista again, I will dedicate an HHD only for the OS while keeping the 1TB HDD as data storage only.
Should have done it this way much earlier, but you know what they say:
You only start missing something when you lost it.

---

### Post by cariboo on 2009-03-20
I would suggest trying the [Windows Vista Recovery Disk]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") linked at the bottom of the page.

Jim

---

### Post by Cov(enant) on 2009-03-20
OMG, I think that is exactly what I need !!
Thank you very much for that and I will report back as soon as I can.

Incredible really.

---

### Post by Cov(enant) on 2009-03-21
**1.** Remember, I installed Ubuntu on my 100GB HDD. 
Then I downloaded the WINDOWS VISTA RECOVERY DISC (thank you cariboo !!) and burned it with the help of BlindWrite onto an empty CD.
 
**2.** Then I reset the system and changed the BIOS to boot from the DVD drive..
After save and restart, the system booted from the CD and it became dark (on the screen) & quiet for a while.
First I thought it was frozen again because even the LED of the HDD stopped completely for minutes.
 
**3.** On the screen suddenly appeared an option where you could select to repair the OS on a particular drive.
The HDD was working for a while like it was finding out what OS had a problem, but after another minute it gave me the option to repair and reboot without selecting anything.
It did something for a while, then it rebooted and my trusted Windows Vista came up slowly, step-by-step..
 
It took ages and I was just watching every little move on the screen and listening to every little noise the HDD made.
I think my heart stopped beating for a couple of seconds prior to the appearance of my trusted wallpaper.
A few seconds later the Everest readings and RocketDock came up as the final part of the boot-up process.
I'm not a strong believer tbh, but I think I fold my hands to pray.
 
Amen :biggrin:

---

### Post by bendib on 2009-04-19
to create a mount point, first open terminal and type sudo mkdir /media/disky (assuming that's what you want the folder named) and to mount it, sudo mount -t ntfs-3g (assuming that ntfs is the file system) /dev/sdb1 (assuming that is the device ID) /media/disky -o force
to unmount it, sudo umount /media/disky
No, not unmount, umount.

Or... you could solve everything by just going to linux all the way.

---

