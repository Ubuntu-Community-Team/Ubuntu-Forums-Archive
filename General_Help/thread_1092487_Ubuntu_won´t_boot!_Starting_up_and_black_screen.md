---
title: "Ubuntu won´t boot! Starting up and black screen"
date: 2009-03-10
forum: General Help
---

### Post by Ni85 on 2009-03-10
hey everybody
today i turned on my laptop after a month away from home.
among the updates, i found two new kernel versions (2.6.27-12 and 13), which i installed together with other updates, and i have to admit that i don´t know if among them there was anything for my graphic card or drivers (flgrx for ATI Radeon).
after rebooting, i see the grub page and then this
```
Starting up...
_ (blinking)
```
then the screen becomes all black and nothing happens at all.
i tried to do what had worked a few times before when i had the same problem: from recovery mode
```
sudo dpkg-reconfigure xserver-xorg
```
but also after this, if i try to start gnome desktop manager, the command line reappears ```
root@tado-laptop:~#
``` without anything happening, and the screen starts blinking every 5 seconds or so.

i also tried to boot the old kernel, but i have the same problem..
does anyone know how to help me??
i really don´t know how to solve this...

thanks a lot

---

### Post by kryptikos on 2009-03-10
Sounds as if you might need to grab the ATI driver and build it against your kernel version. 

Fastest way is to pull it straight from ATI for your card type:

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx"). Transfer it with a USB stick and then extract and follow their installation instructions. I've had to do that before with cantankerous Radeon cards to get it to work with updated kernels.

---

### Post by Ni85 on 2009-03-10
ehm.. how do i do it?
i mean.. i can copy it on a USB drive using my girlfriend´s laptop, but how do i install it on mine? will it even read my usb stick in recovery mode?
thanks for your help

---

### Post by Ni85 on 2009-03-10
i can´t figure it out..
and i am getting quite desperate..

---

### Post by Ni85 on 2009-03-10
anybody with any idea?
i can´t use my laptop at all......

---

### Post by Cuba71 on 2009-03-10
I know my comments won't help since I'm going through a similar situation.
I've been running Ubuntu from a flash drive for about a month, finally last week I decided to install it in my hard drive, and the black screen after the login comes on and freezes.

In addition I've spent over $100 in books and spent long hours doing some developments, and I'm afraid I'll loose everything and I'll have to go back to Vista

---

### Post by Ni85 on 2009-03-10
hey
sorry to hear that
there must be a way to solve this though. in my case everything was working rather smoothly until this morning!
i really hope somebody can help

---

### Post by Cuba71 on 2009-03-10
I have ubuntu loaded to a flash drive that allows my to boot up, but I haven't found how to recover the data from my hard drive.

This was a wubi install.

---

### Post by Ni85 on 2009-03-10
don´t know how to help you, but mine is a different problem.
anyone with ideas or solutions?
i can´t use my computer....

---

### Post by MaxIBoy on 2009-03-11
First of all, you may not need to mess with the flash drive. Simply install a text-mode web browser such as links (run "apt-get install links,") and use it normally to download the drivers and install them. If you're not on the Internet from the command line, try "ifup eth0" to have it try to set up your internet connection automatically. If that doesn't work, it's probably not worth the trouble of messing around with it and the flash drive will be good enough.

To mount the flash drive on the computer, follow these steps:

[LIST=1]
[*]Know what the filesystem type is on your flash drive (FAT16, FAT32, NTFS, whatever.) If the filesystem is any kind of FAT (which it probably is), you will be able to mount it as VFAT. Windows will tell you if  you right click the flash drive in "my computer" and click "properties," or "information," or something like that. I can't remember, it's been a while.
[*]If /mnt is empty, create a new directory inside of /mnt with a name like "usb" or something. If /mnt has any empty difectories in it, you can use one of those.
[*]Plug in the flash drive and wait a couple of seconds.
[*]Run the command "dmesg | grep -i usb" in the terminal. "Dmesg" is a log of all the system messages. The pipe symbol takes the output of "dmesg" and uses it as the input of "grep," where grep is a search program. In this case, we're using "grep" to search for the word "usb." The "-i" parameter tells grep to ignore uppercase/lowercase differences.
[*]Using that, you should find out where in /dev the flash drive is. You're probably going to find something that starts with "sd," like "/dev/sda," or "/dev/sda1."
[*]Run the command "mount -t filesystem_type /dev/whatever_your_flash_drive_is /mnt/whatever_destination_you_chose
[*]cd to /mnt/whatever_destination_you_chose, and it will all be there.
[/LIST]

---

### Post by Ni85 on 2009-03-11
hey
first of all thanks for helping me!
i tried to install links, but i can´t make my internet work from the command line.

i am not sure i understand what you mean on point 2: > If /mnt is empty, create a new directory inside of /mnt with a name like "usb" or something. If /mnt has any empty difectories in it, you can use one of those.

what is /mnt? where exactly should i create the "usb" directory?

when i run ```
dmesg | grep -i usb
``` the output is a long one.
i will copy a section of it: 
```
[306.616163 (each line starts with a number)] usb 7-4: new high speed USB device using ehci_hcd and address 5
[number] usb 7-4: configuration #1 chosen from 1 choice
[] scsi8 : SCSI emulation for USB Mass Storage devices
[] usb-storage: device found at 5
[] usb-storage: waiting for device to settle before scanning
[] usb-storage: device scan complete
[] usb 7-4: USB disconnect, address 5

```

consider i can´t see the entire output, but it seems like it´s repeated at least from number 3 ("device found at 3) to 6, with the scsi growing from "7" to "9".

i tried to run a cd/dev/sd and hit TAB, which gave me ```
sda sda1 sda3 sda4 sdb sdb1
```

i´m not very good at these things, sorry if i nees some extra patience...

thanks again

---

### Post by MaxIBoy on 2009-03-11
Well, in UNIX-like operating systems, everything is in one directory structure, whereas in Windows you have the C:\ drive seperate from the D:\ drive, etc. 

So when you mount a volume, you mount it somewhere inside this unified filesystem. The top level is /, then if you have other partitions they'll appear inside of / (for example, my other Linux install appears for me in /media/disk, and I have a seperate partition set to use for /home.) 

The traditional place (you can put it in other places, but it's traditional to put them in /mnt) to mount flash drives is in /mnt, as in /mnt/flashdrive1, /mnt/flashdrive2, or whatever names you choose for them. If the flash drive is not mounted, /mnt/flashdrive1 will look like a simple empty directory. So if /mnt is empty, create an empty directory inside of /mnt to use as the mount point for the flash drive. 

Either "mkdir /mnt/whatever" or "cd /mnt" and then "mkdir whatever", both will work.



Also sorry, I forgot you're in full textmode and dmesg probably won't fit on your screen. Pipe it through to less ("dmesg | grep -i usb | less") or pipe it through to a file and look at the file at your leisure ("dmesg | grep -i usb > /home/yourUserName/somefile.txt") and that should solve that problem.



However, there may be a shortcut. Using tab completion on /dev/sd was an inspired idea, actually. I'm assuming /dev/sda is an internal SATA drive, because it has multiple partitions. Unless you've partitioned that flash drive, you could probably just go for /dev/sdb1.

---

