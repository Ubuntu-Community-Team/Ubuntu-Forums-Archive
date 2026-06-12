---
title: "Help on two disks"
date: 2011-12-01
forum: Desktop Environments
---

### Post by smartcard on 2011-12-01
Hello, I am new to Linux / Ubuntu.

I have installed on a PC the Ubuntu 11.04 ("Natty Narwhal") to use it with VirtualBox host.

I have 2 x 250GB disks in this PC.

I want to use only one disk and want to remove the 2nd, but when I physically remove the 2nd disk, the system is not booting.

Please find attached screen shots of both disks.

Need your help.

---

### Post by gordintoronto on 2011-12-01
sda claims it is part of a RAID setup, so you can't use just one disk.

Do you mean you have installed Ubuntu *under* Virtualbox, or that you will install Virtualbox in Ubuntu?

Most likely, your best bet would be to remove one disk, then install Ubuntu, setting it up as described here: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by smartcard on 2011-12-01
> **gordintoronto said:**
> 
Do you mean you have installed Ubuntu *under* Virtualbox, or that you will install Virtualbox in Ubuntu?

I have installed Virtualbox in Ubuntu.

> **gordintoronto said:**
> sda claims it is part of a RAID setup, so you can't use just one disk.
Is there a way to disable or remove the RAID without re-installing Ubuntu?

---

### Post by smartcard on 2011-12-02
I need to know, if there is a way to disable or remove the RAID without re-installing Ubuntu?

---

### Post by Azyx on 2011-12-02
> **smartcard said:**
> Hello, I am new to Linux / Ubuntu.

I have installed on a PC the Ubuntu 11.04 ("Natty Narwhal") to use it with VirtualBox host.

I have 2 x 250GB disks in this PC.

I want to use only one disk and want to remove the 2nd, but when I physically remove the 2nd disk, the system is not booting.

Please find attached screen shots of both disks.

Need your help.

Which disk do you try to remove? sda have booth FAT and a raid-component? Probably are the boot-loader on the disk you remove? Do you know there the Ubuntu-system are?
/Cheers

---

### Post by smartcard on 2011-12-02
> **Azyx said:**
> Which disk do you try to remove? 
First I tried removing sda and then sdb,  both cases did not go well until I have both drives connected to the PC.

Is there a way to remove RAID?

Or, how can I take an image of my PC and totally transfer to a new disk?

---

### Post by Azyx on 2011-12-02
> **smartcard said:**
> First I tried removing sda and then sdb,  both cases did not go well until I have both drives connected to the PC.

Is there a way to remove RAID?

Or, how can I take an image of my PC and totally transfer to a new disk?

I think it's confusing if you can boot from the disk and take the status from your disk, or have you boot from cd/dvd/usb? sda are mounted, but not sdb. 

I'm not sure where you have your system? If it's on the raid-flagged device? Why do you have a FAT-partition?

In may cases it's only a flag who says if it' a raid-component, but I'm not sure if it's only to remove it?

---

### Post by smartcard on 2011-12-02
> **Azyx said:**
> I think it's confusing if you can boot from the disk and take the status from your disk, or have you boot from cd/dvd/usb? sda are mounted, but not sdb.

Booted while both disks are connected to the PC nu cd/dvd/usb.

---

### Post by Azyx on 2011-12-02
> **smartcard said:**
> Booted while both disks are connected to the PC nu cd/dvd/usb.

I don't know, but have you tried to boot from cd/dvd/usb with only one disk inserted and when you get the choose to try 'boot from first harddisk'? I don't know why one partition are a raid-component, but I trhink it's only are a flag, that youy may change in gparted, but i'm not sure.

---

### Post by smartcard on 2011-12-07
Okay I have got a new Drive now.  Please some one help me to transfer the Ubuntu Installs of my  existing drives to the new drive.  

I think a image transfer will not work since the RAID mess-up as discussed in this thread.

---

### Post by Azyx on 2011-12-07
> **smartcard said:**
> Okay I have got a new Drive now.  Please some one help me to transfer the Ubuntu Installs of my  existing drives to the new drive.  

I think a image transfer will not work since the RAID mess-up as discussed in this thread.

I think you don't have really explaind your problem or what you have done by your self to solve it?

 Where do you have the Ubuntu-install now?   

As I asked before, did you try to both from ubuntu-live-CD? If you can, there are a few things you can try, for example fix the bootloader, fix the RAID-flagg on the disk etc. I you can't fix the disk but read it, you probably what to copy the home-dolder, so you can save config-files for applications, document, and so on.

/Cheers

---

