---
title: "how to put a file onto usb flash drive?"
date: 2009-03-12
forum: General Help
---

### Post by jesse c on 2009-03-12
Im trying to make a flash stick to use to update a bios for my eee pc.I have down loaded the bios file from asus support site onto my ubuntu desktop and now need to make a usb flash drive to boot into my eee netbook.Ive successfully created usb iso drives with system/applications menu but this method doesnt seem to wok with bios file.Can somebody give me a step by step procedure.I have an'Ubuntu For Non Geeks' book but the chapter on using files starts by saying 'at this point everybody knows how to drop and drag files' and glosses over the actual steps.This is my first computer and while i know how to click the mouse and 'drag' stuff around on the monitor,i dont know when/what/or where things get draged to to get things done so please be very detailed.Sorry if im asking too much

---

### Post by SunnyRabbiera on 2009-03-12
It should be very simple, on the file you want to grab hold down the right mouse button and you will see it moves the file on your screen.
To do what you need to do simply open the location of your file and your flash drive and with a simple move you can drag and drop your file.
Drag and drop is very easy, like I said hold down your right mouse button and then when you get into your flash drive simply let go of the mouse button.

---

### Post by kmac on 2009-03-12
Insert Flash Drive into USB port

Open "Computer" from the places menu. 

Locate your Flash Drive (i.e. SanDisk Cruzer Micro 4GB)

Double click your flash drive.

This should display the files on your flash drive.

Minimize the window with your flash drive.

Right click on the file on your desktop that you want to copy.

Click 'copy'

Re-open the window with your flash drive files.

Right-click on empty space below your listed files.

Click 'paste'

Wait for file to be copied.

Enjoy portable fileage.

---

### Post by kmac on 2009-03-12
By the way, if dragging and dropping is an issue, I recommending getting more familiar with computers before attempting to flash BIOS. There lies a danger in doing this and can severely damage your machine.

---

### Post by Nano_ext3 on 2009-03-12
As he state above its very easy.  Open up the flash drive by insertint it into the laptop or by double clicking its mouted icon on the desktop.  Just drag the BIOS update file into the window of the flash drive.  

BUT, by the sounds of it, you need to "boot" into your flash drive, and then run the file correct?  If you have windows its faily easy with HP's Flash Utility and some 98 boot files, or DOS files.  

**I did find this guide , on how to update the BIOS on an EeePC:**


[http://wiki.eeeuser.com/howto:updatebios](http://wiki.eeeuser.com/howto:updatebios) (this must be done on linux by the looks of it)


[B]
If you only have linux follow these steps:[/B]

**One Guide I found useful:** ([http://www.ve3syb.ca/software/bootableusb.html](http://www.ve3syb.ca/software/bootableusb.html)).  If you open up terminal and do a "sudo fdisk-l", you can note which device is your USB stick based on how large the disk is.  Your USB drive will typically have its very own entry at the bottom of fdisk so that will probably be it.  Typically it is something like "/dev/sdb1/"

**There is also a guide here for doing this with grub **([http://www.mayrhofer.eu.org/Default.aspx?pageid=45](http://www.mayrhofer.eu.org/Default.aspx?pageid=45))

**A guide to do this with "mkboot" **([http://people.ofset.org/~ckhung/p/mk-boot-usb/index.php](http://people.ofset.org/~ckhung/p/mk-boot-usb/index.php))



**If you have a windows partition (boot into it ):**

[LIST=1]
[*]  Download the HP flash AND the 98 boot files from [http://files.extremeoverclocking.com/file.php?f=197] HERE ]("http://files.extremeoverclocking.com/file.php?f=197")
[*]  Insert the  flash drive
[*]  Run the ulility
[*]  Select Format (fat32) and the option to "make MS-DOS startup disk"
[*]  Point the program via the browse button to your "98 boot files", which must be un-zipped first
[*] Click start
[*] There you have it, now copy your BIO update to the flash drive
[*] Reboot and make sure BIOS is set to boot from USB or select the optin at startup to get your boot menu and select USB.
[*] You should get a prompt now.  Browse by doing a "dir" command and you should see the BIOS file.
[*] Run the BIOS file "BIOS-UPDATE.exe"
[*] That should work.
[/LIST]




As you can see, its a little easier to make a DOS bootable flashdrive from windows.  **If you have a utility from your motherboard company that needs put on the flash drive I suggest adding that in addition to the BIOS file**, as it will most likely be required to "run" that tool from the Flash drive , which will then ask for the location of the BIOS file.  Check and see if there are instructions on how to do this on an Eee PC.


This seems like alot, but take your time and see what you can make of this information.


Cheers!


-Nano

---

