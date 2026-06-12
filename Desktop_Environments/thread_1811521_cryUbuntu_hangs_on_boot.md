---
title: ":cry:Ubuntu hangs on boot"
date: 2011-07-25
forum: Desktop Environments
---

### Post by Wolf_Fhang on 2011-07-25
A few days ago i was fooling around with ATI graphics settings and was doing some updates for Ubuntu and after i went to reboot my Desktop it kept comming up with odd symbols instead of a log in screen, then i started to try and do things with a LiveCD and screwed things up even more :confused: so now any time i attempt to boot, even into recovery mode, it stops at the line 

[ 2.573600] sd 6:0:0:3: [sde] Attached SCSI removable disk

i have tried to do multiple fixes with no avail and i am not very savvy with linux as i have only been using it under a year, so it would be awesome if anyone could help 

this is 10.10 Maverick and the 32bit version, if you need more details i will be happy to help, also i am able to boot up Ubuntu with a Live CD

Thanks in advance 

PS: this is a repost of my thread from the general help section

---

### Post by 2F4U on 2011-07-25
Do you remember what programs were updated? Maybe a kernel update after the installation of ATI drivers? Can you boot into a previous kernel?

---

### Post by Wolf_Fhang on 2011-07-25
sadly i cant remember what the updates were, i was just doing whatever updates it told me except Wine and it wasnt updates for the ATI drivers i don't think im pretty sure it was other random Ubuntu updates,

thanks for actually replying and i'll give whatever other info i can

---

### Post by Wolf_Fhang on 2011-07-26
considering after i looked into it a little it seems Busy Box booting up isnt always good so i'd like to mention i do see Busy Box start before the hang at the SCSI if that is any help

---

### Post by Wolf_Fhang on 2011-07-27
well if no one knows what the problem is could someone at least walk me through how to mount my hard drive with a Live CD?

---

### Post by dreamslides on 2011-07-27
> **Wolf_Fhang said:**
> well if no one knows what the problem is could someone at least walk me through how to mount my hard drive with a Live CD?

Don't you see it under the menu option?

---

### Post by Wolf_Fhang on 2011-07-27
well that's the thing, i went on the Places menu and clicked it and it keeps giving me an error that it is busy and i even tried terminal commands to do it but nothing seems to make it mount, idk if it was just taking a while cause its a 300GB hard drive in my desktop

---

### Post by deconstrained on 2011-07-27
Try holding down shift key after post, so that you can get into the grub menu. Look at the available kernels, and try booting into an older one if you can. Then you could try re-installing the new kernel/driver.

---

### Post by Wolf_Fhang on 2011-07-27
well actually whenever i boot it goes into the Grub menu and so far whenever i tried any of the Kernels and the recovery modes it would not boot and kept hanging at the line i said in my original post

---

### Post by Wolf_Fhang on 2011-07-31
so could anyone at least help me with the mounting of my desktop's hard drive from a live cd? if i cant fix it i wanted to get a few files i forgot to back up because they're semi important :/

---

### Post by SeijiSensei on 2011-07-31
When the CD menu appears, try hitting F6 and choosing "nomodeset".  After the X appears, hit Escape, then enter.  This avoids some video issues that can hang boots.

Also, if you're using a USB CD drive, make sure it's connected to a USB 2.0 port.

I've encountered both these problems in the last couple of days while trying to boot an Ubuntu CD image on a new HP laptop with ATI graphics.

---

### Post by gbrowning on 2011-07-31
Lucid
I installed an ATI 6850 HD. And have had nothing but problems  since the very first boot attempt.  After messing around with  a few  methods I have failed. 
    
    Current desktop environment is  not satisfying.  Machine boots and is fully functional but the display  quality is terrible, vga and the wrong proportions.

    lspci |grep vga returns 
    VGA compatible controller: ATI Technologies Inc Device 6739
    
    Monitor is found to be "unknown" and the resolution is 1152 X 864,  the monitor is really 1200X900

    History:
     Been running 10.4.3 64 bit.  Replaced Video Card with HIS Radeon  6850HD.  Installed the proprietary drivers using the guide listed above.  [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto). Catalyst reported  an incompatible card.  lspci |grep vga returned   VGA compatible  controller: ATI Technologies Inc Device 6739 just as it is doing now.
     I tried to remove the flgrx using the script on the guide and many  error messages were returned so an attempt was made to remove the files  manually. After a bit of surgery the machine failed to boot properly so I  decided to upgrade to Maverick as the open source drivers were reported  to work better.
   I used the update and upgrade commands from the terminal.
   Maverick failed to boot into GUI so I went ahead and tried to be Updated and Upgraded to Natty.
   Total failure with the machine hanging so
   Used 10.4.3 live CD to move files then tried to use 11.4 live CD to install clean system
    11.4  would not install to the mucked up drive before I cleaned it.  When it did install I lost keyboard and mouse......probably a separate  issue but may have to do with video card interrupts.
   Now I am back to a basic install of 10.4.3 and want to get the video card working properly. 
    
    Any tips?


edit
I was able to move through the GUI based upgrade and am now running Natty.  The video card is being used properly.  Finished this attempt minutes ago.  Have not had time to dig into the whys of this.

---

### Post by Wolf_Fhang on 2011-08-01
> **SeijiSensei said:**
> When the CD menu appears, try hitting F6 and choosing "nomodeset".  After the X appears, hit Escape, then enter.  This avoids some video issues that can hang boots.

Also, if you're using a USB CD drive, make sure it's connected to a USB 2.0 port.

I've encountered both these problems in the last couple of days while trying to boot an Ubuntu CD image on a new HP laptop with ATI graphics.

well that's the thing, its not the CD that hangs its the normal hard drive booting that hangs really

---

### Post by gbrowning on 2011-08-02
The hard drive you are booting from will not need to be mounted.  I am using "Classic" and to reach the file system just click "places" then "Home"  you should be able to navigate from there


   If that is not possible try this  



Open a terminal window. The terminal window  is found under the "Applications" then " Accessories" then "Terminal"


                             
   Type the command "dmesg" to determine the device name of the hard drive you want to mount.  Look for the line that mentions the name of your hard drive such as: hdd: IBM-DTLA-307020, ATA DISK drive
The device name for this disk drive would be "/dev/hdd."

                             
    
   Type the command "sudo mkdir  /mnt/driveb" to create a directory where the contents of the hard drive  can be accessed after it is mounted.  You can replace "driveb" with any  descriptive name.

                             
    Type the command "mnt /dev/hdd  /mnt/driveb" to mount the hard drive.  The contents of the drive will be  accessible in the "/mnt/driveb" directory.

                          
    Type the command "exit" to close the root session  




Hope this helps
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by Wolf_Fhang on 2011-08-03
> **gbrowning said:**
> The hard drive you are booting from will not need to be mounted.  I am using "Classic" and to reach the file system just click "places" then "Home"  you should be able to navigate from there


   If that is not possible try this  



Open a terminal window. The terminal window  is found under the "Applications" then " Accessories" then "Terminal"


                             
   Type the command "dmesg" to determine the device name of the hard drive you want to mount.  Look for the line that mentions the name of your hard drive such as: hdd: IBM-DTLA-307020, ATA DISK drive
The device name for this disk drive would be "/dev/hdd."

                             
    
   Type the command "sudo mkdir  /mnt/driveb" to create a directory where the contents of the hard drive  can be accessed after it is mounted.  You can replace "driveb" with any  descriptive name.

                             
    Type the command "mnt /dev/hdd  /mnt/driveb" to mount the hard drive.  The contents of the drive will be  accessible in the "/mnt/driveb" directory.

                          
    Type the command "exit" to close the root session  




Hope this helps
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]


that's the thing, I'm booting from a live cd not my hard drive, im trying to access my hard drive from the live cd though so i will try what you said

---

### Post by Wolf_Fhang on 2011-08-03
that did not work, the dmesg line came back with no information about my drive and when i tried any of the things you said, the mnt command was not found and i was not able to do anything

---

### Post by Wolf_Fhang on 2011-08-03
nevermind, i wound up finding back ups of the files i need and i am just wiping the hard drive so i can re install the OS

---

