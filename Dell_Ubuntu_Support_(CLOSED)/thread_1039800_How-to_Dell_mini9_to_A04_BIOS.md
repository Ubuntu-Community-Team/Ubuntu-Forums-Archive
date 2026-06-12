---
title: "How-to: Dell mini9 to A04 BIOS"
date: 2009-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BigKenW on 2009-01-14
These directions worked for me so I figured I would post them. To follow my directions you need any variant of Windows Vista. It was pretty easy. You need a USB flash drive. I used a 4GB drive. Most of the directions below come from: 

[http://www.techarp.com/showarticle.aspx?artno=431](http://www.techarp.com/showarticle.aspx?artno=431)

How-to:
====================
Download the [Automated Installation Kit (AIK) for Windows Vista]("http://technet.microsoft.com/en-us/library/cc748933.aspx"). The AIK weighs in at approximately 1.2GB! Burn the downloaded image to DVD.

[B]
Formatting The USB Key[/B]

1. Insert your USB key into your Windows Vista system. Note that you can't do this with a Windows XP system because your USB key will not be listed as a disk when you follow the steps below.

2. Start a command prompt by going to Start -> All Programs -> Accessories -> Command Prompt.

3. Type in the following commands (in bold) and press Enter after each command. The comments follow below and italicised. Please exclude them when you type the commands.

    &#8226; **diskpart**

    &#8226; **list disk**

       - This lists the disks available in your system. Check whether disk 1's size tallies with that of your USB key

    &#8226; **sel disk 1**

       - This selects the disk number of your USB key. Change accordingly to reflect your USB key if you have multiple drives on your Vista system. If in doubt, type 'list vol' and check the size of your USB key and compare it with the list from 'list disk'

    &#8226; **clean**

       - This will delete everything in your USB key, so before you do this, make sure this is your USB key and not your hard drive!

    &#8226; **create par primary**

       - This creates a primary partition in your USB key

    &#8226; **sel par 1**

       - This selects the newly created partition

    &#8226; **act**

       - This makes the partition active

    &#8226; **format fs=fat32**

       - This formats the selected partition with FAT32 filesystem

    &#8226; **assign**

       - This assigns the USB key to a drive letter

    &#8226; **exit**

At this point, your USB key will be empty and formatted with the FAT32 filesystem. Now, we need to insert WinPE into the USB key and make it bootable.

**Installing WinPE 2.0**

1. If you already have Windows Vista OPK installed, skip this step. Otherwise, download and install Windows Vista AIK into your Windows XP PC (not your Windows Vista system).

2. Open the Windows PE Tools Command by going to Start -> All Programs -> Windows OPK / Windows AIK -> Windows PE Tools Command Prompt.

3. Now, you need to run the Copype.cmd script. This script requires two arguments - hardware architecture and destination location. To run this script, type the following in the command prompt :

    Copype.cmd x86 c:\winpe_x86

    x86 - this can be used in most x86 systems
    amd64 - for systems using AMD 64 processors
    ia64 - for Intel Itanium systems

Running the script above creates a winpe_x86 folder in drive C: and copies all the necessary files for that architecture (in this example, x86) into the folder. You can choose to change the folder name, and drive letter.

3a. Go to Dell.com and using your service code download the BIOS executable to your PC.

4. Create a folder at c:\winpe_x86\iso\ called DellBios.

4a. Copy the downloaded BIOS executable to c:\winpe_x86\iso\DellBios

5. Insert the USB key into the PC and run the following command.

    xcopy c:\winpe_x86\iso\*.* /s /e /f e:\

    In this example, e:\ is the drive letter of the USB key. Feel free to change if it's using a different drive letter.

FINISHED!

[B]
Updating the BIOS[/B]

1. Boot the mini9 with the USB drive. You will be presented with a Command Prompt.

2. Type C: and press ENTER

3. Type CD DellBios and press ENTER

4. Type DIR and press ENTER

5. Type the name of the BIOS file. The update will run. When finished, type EXIT at the command prompt and Windows will reboot the PC. The BIOS will now be at A04.

Hope this helps.

DISCLAIMER: I claim no responsibility for bricked systems. Upgrade at your own risk.

---

