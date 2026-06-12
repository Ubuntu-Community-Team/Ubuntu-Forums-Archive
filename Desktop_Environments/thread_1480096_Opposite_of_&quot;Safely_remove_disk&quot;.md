---
title: "Opposite of &quot;Safely remove disk&quot;"
date: 2010-05-11
forum: Desktop Environments
---

### Post by Sven6210 on 2010-05-11
I have an external USB disk (Western Digital MyBook) attached to my computer. As I oly use it for a kind of backup it is switched off most of the time. Actually the device itself does not have a power switch.

When simply unmounting the USB disk it stays still on power, so it's turning an the LED is still on.

When I choose "Safely remove disk" in Nautilus the disk is powered off (not turning, no LED light).

My question:
How can I reactivate the disk when I want to use it again. There must be a better solution than is connecting the USB or power cable and reconnecting so that the external disk is recognized again. Can anybody help me an give me the command I am looking for - the opposite of "Safely remove disk"?

---

### Post by meoow on 2010-05-11
File Managers like Thunar,Dolphin don't have "Safly Remove Drive" option,so I think you click "Unmount" would just OK.

---

### Post by Sven6210 on 2010-05-12
It seems you misunderstood me or I did not express myself clearly. The 'Safely remove disk' is exactly the right function as it sends my USB disk to sleep (it switches fully off).

I am looking for a way to wake up the sleeping USB disk. So far I need to unplug the power or USB cable and replug it in order to wake up the USB disk. I am looking for a command in Ubuntu that allows me to wake it up without un- and replugging one of the cables. Technically it is possible - I used a tool under Windows XP which worked very well. But I did not find any suitable solution/command in Ubuntu yet.

---

### Post by frostschutz on 2010-05-12
I don't have any such drive, so it's hard to reproduce.

Can you show what's in dmesg or lsusb after the drive is supposedly turned off? Also, after the device shut itself off, and you checked dmesg, can you unplug it and see if the unplugging alone (not replugging) produces additional messages in dmesg?

Just wondering whether the drive is really gone for good or if it could quite simply be remounted. If the drive is really gone completely, you'd have to reset the USB bus to get it back, not exactly a nice thing to do... I'd rather get an USB cable with an onoff button then ;)

---

### Post by Sven6210 on 2010-05-12
Can you tell me how to reset the USB bus? I would not mind giving it a try. I grew up with windows - I am used to resets ;)

---

### Post by Sven6210 on 2010-05-17
After I have send the USB disk with "Safely remove disk" into the sleeping mode (LED is off and no spinning) I still can see it with "lsusb"

The result of "lsusb"

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c71f Logitech, Inc. 
Bus 002 Device 003: ID 046d:c71e Logitech, Inc. 
Bus 002 Device 002: ID 046d:0b07 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So the Western Digital disk is still there and can be seen. I get the same result for "lsusb" when the Western Digital USB disk is running. And with Windows XP and a special tool I was able to wake it up without unplugging the cable. So it must be possible, I just do not know how.

I tried:
Mount - this only works if the disk is still running but not mounted. After a "Safely remove disk" I can not mount any more

scsi-spin - I tried this tool which apparently helped other users whose USB disk went into sleeping mode, but it did not work for me.

Does anybody has another idea?

Best regards

Sven

---

### Post by frostschutz on 2010-05-17
Found these with Google, dunno if they'll help you... couldn't find a ready to use utility :(

[http://marc.info/?l=linux-usb-users&m=116827193506484&w=2](http://marc.info/?l=linux-usb-users&m=116827193506484&w=2)
[http://forums.x-plane.org/index.php?app=downloads&showfile=9485](http://forums.x-plane.org/index.php?app=downloads&showfile=9485)

---

### Post by 3rdalbum on 2010-05-17
Go to System > Administration > Disk Utility. Select your disk and click Mount. It then tells Gnome to mount the disk in the same way it usually would.

EDIT: If it doesn't list the disk, then it's too far gone; you should just unmount it rather than "safely remove", because the latter puts the USB device into a deeper sleep or "charging-only mode".

---

### Post by Zintha on 2010-05-17
Why would you need to "Safely remove drive" if you're not removing it?
I'm just curious?

---

### Post by andreselsuave on 2010-05-18
Have you tried ...
```
sudo mount -a
```
 it mounts all the stuff back

---

### Post by Grenage on 2010-05-19
> **andreselsuave said:**
> Have you tried ...
```
sudo mount -a
```
 it mounts all the stuff back

If it's listed in fstab, yes.

OP: I don't think that can be done, but I'd love to be proved wrong.

---

### Post by John Bean on 2010-05-19
> **Sven6210 said:**
> When I choose "Safely remove disk" in Nautilus the disk is powered off (not turning, no LED light).

I guess you're using the right-click menu that offers "safely remove" but no "unmount". This is irritating when using USB disks that are more or less permanently attached but you can easily work around it without resorting to the terminal or utility programs. Instead of using the right-click menu just click on the triangular "mounted" icon shown next to the drive in the "Places" panel of Nautilus; this will silently unmount the drive, and clicking on the drive will mount it again. Simple :-)

---

### Post by Sven6210 on 2010-05-19
Dear all,

Thank you very much for your help - I appreciate the community here to be so helpful. Unfortunately I did not find any solution yet.

To summarise:
I use "Safely remove disk" in order to send the USB disk into a sleeping mode where it completely stops. As it is a backup disk it only runs few hours a week and I want to keep it this way (saving energy, protecting the environment and avoiding unnecessary wear and tear of a backup-disk).

When I unmount the USB disk it will remain switched on, so keep turning. In this case I can easily remount it, but this is actually not what I am looking for.

I am really looking for a solution to reactivate the USB disk after it went sleeping. How to do it: unplug and replug the USB or power cable. This works, but it is not very elegant. And I have to twist my arm to do so (the Computer and the USB disk are in a cupboard in the living room).

Under Windows XP I used a tool that allowed me to reactivate the USB disk from the sleeping mode. So technically it is definitely possible - however I do not yet know how.

From all the advises I have received I think a reset of the USB bus sounds the most promising. If anybody knows a command to do so in Ubuntu 10.04 I would be happy if you could post it here.

[frostschutz]("http://ubuntuforums.org/member.php?u=1072388") recommended two websites out of which one sounds promising. However I did not yet have the time to try it. It will take some time for me as I first need to compile some C code. I will try that on the weekend.

Best regards

Sven

---

### Post by John Bean on 2010-05-20
I'm sorry, I had misread your original requirement. There is a solution which worked perfectly for my Maxtor USB drive, and that is to use hdparm to turn off the drive's power management. Have a look at the manpage for details.

Note that it will only work with USB drives that implement passthrough of ATA/SCSI commands but it worked fine with mine. You can easily (and safely) test if it will work by attempting to read back the current drive settings before trying to change them. If it can read them then it can change them :-)

---

### Post by Sven6210 on 2010-05-24
Dear all,

I was still not successful. What I tried on the weekend:

**1. Compiling usbreset**

I compiled the C program from:

[http://marc.info/?l=linux-usb-users&m=116827193506484&w=2](http://marc.info/?l=linux-usb-users&m=116827193506484&w=2)

The compiling went well, but I can actually not run the program. The computer says the file name is invalid.

Question: after having compiled a c program with "gcc" to I need to make any adjustments to the output file? The file looks like an executable for me (file name has the same colour when running "ls" than other executables) or are there any restrictions with executables in the user directory? When I try to run the program I am in the same directory as the compiled program and I can see it when entering "ls", but I can not run it.

**2. Trying hdperm**
Dear "John Bean" could you give me the syntax you used for "hdperm" to switch the device off and on?

I tried "hdparm -Y /dev/sdc" and "hdparm -Y /dev/sdc1". With "sudo fdisk -l" I verified that sdc1 is the right partition, so that can not be the mistake.

Thank you for your help

Sven

---

### Post by John Bean on 2010-05-24
> **Sven6210 said:**
> I tried "hdperm -Y /dev/sdc" and "hdperm -Y /dev/sdc1". With "sudo fdisk -l" I verified that sdc1 is the right partition, so that can not be the mistake

It was a while back, I'm afraid I can't remember the exact command I used and I n o longer have the drive I was using at the time. However it certainly wasn't -Y which forces the drive to spin down. I think I used -B128 to disable spindown without disabling other power management, but I can't be sure. Afterwards the drive stayed online forever when connected rather than spinning down if not used for xxx minutes.

Note that you'll need to use sudo with hdparm.

---

### Post by cryptotheslow on 2010-05-24
> **Sven6210 said:**
> Dear all,

I was still not successful. What I tried on the weekend:

**1. Compiling usbreset**

I compiled the C program from:

[http://marc.info/?l=linux-usb-users&m=116827193506484&w=2](http://marc.info/?l=linux-usb-users&m=116827193506484&w=2)

The compiling went well, but I can actually not run the program. The computer says the file name is invalid.

Question: after having compiled a c program with "gcc" to I need to make any adjustments to the output file? The file looks like an executable for me (file name has the same colour when running "ls" than other executables) or are there any restrictions with executables in the user directory? When I try to run the program I am in the same directory as the compiled program and I can see it when entering "ls", but I can not run it.

Sven

If you are in Terminal and in the same directory as your executable file then try prefixing the file name with  ./   e.g. if the file is called   usbreset   you would enter ./usbreset

You could also use the ls -l  command to verify that the correct executable permissions are set. If not, use   chmod +x ./usbreset    to set the executable permissions.

---

### Post by Sven6210 on 2010-05-24
Today I have the pleasure to update the status of this thread to "solved" and I would like to thank the community for the help provided. Even though you did not have the final solution you showed me the way to go and with the help of "ixquick" (I'm not using Google directly any more) and Werner from OpenMoko I found the solution.

The best way to reactivate the USB disk after I have used "Safely remove" and the disk is completely off (no spinning, no LED) is just to reset the USB bus.

At [http://svn.openmoko.org/trunk/src/host/usbreset/usbreset.c](http://svn.openmoko.org/trunk/src/host/usbreset/usbreset.c) you can find the C code for a program that resets the USB bus.

The detailed steps:

**1. Install libusb-dev**

sudo apt-get install libusb-dev

This is needed as the C program will include a file called "usb.h" which is provided with this package. At least I got an error message until I installed this package.

**2. Save the C program**
Copy the following text (code from At [http://svn.openmoko.org/trunk/src/host/usbreset/usbreset.c](http://svn.openmoko.org/trunk/src/host/usbreset/usbreset.c)) into the file 'usbreset.c' in your home directory:

I suggest to use the code from the above link, however in case the above link is deactivated in the near future I pasted the code below.

===start here===
/*
 * usbreset.c - Reset one or all USB devices
 *
 * (C) 2007 by OpenMoko, Inc.
 * Written by Werner Almesberger <werner@openmoko.org>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
 */


#include <stdlib.h>
#include <stdio.h>
#include <errno.h>
#include <usb.h>


static void usage(const char *name)
{
    fprintf(stderr, "usage: %s [bus/device]\n", name);
    exit(1);
}


int main(int argc, const char **argv)
{
    struct usb_bus *usb_bus;
    struct usb_device *dev;
    int all = 0;
    int bus_num, dev_num;

    switch (argc) {
        case 1:
            all = 1;
            break;
        case 2:
            if (sscanf(argv[1], "%d/%d", &bus_num, &dev_num) != 2)
                usage(*argv);
            break;
        case 3:
            usage(*argv);
    }

    usb_init();
    usb_find_busses();
    usb_find_devices();
        for (usb_bus = usb_get_busses(); usb_bus; usb_bus = usb_bus->next)
        for (dev = usb_bus->devices; dev; dev = dev->next) {
            struct usb_dev_handle *handle;

            if (!all &&
                (atoi(usb_bus->dirname) != bus_num ||
                dev->devnum != dev_num))
                continue;

            handle = usb_open(dev);
            if (!handle) {
                fprintf(stderr, "usb_open: %s\n",
                    usb_strerror());
                continue;
            }
            if (usb_reset(handle) < 0 && 
                (dev->descriptor.bDeviceClass != USB_CLASS_HUB ||
                errno != EISDIR)) {
                fprintf(stderr, "usb_reset: %s\n",
                    usb_strerror());
                continue;
            }

            if (!all)
                return 0;

            fprintf(stderr,"reset %s/%s\n",
                usb_bus->dirname, dev->filename);
        }

    if (!all) {
        fprintf(stderr, "no device %d/%d found\n", bus_num, dev_num);
        return 1;
    }

    return 0;
}

===end here===

**3. Compile the C program**

3.1 open a terminal window
3.2 make sure you are in the same directory where you have the file "usbreset.c" that you just saved
3.3 run: gcc -o usbreset usbreset.c -lusb

The result is the compiled program called "usbreset" in the current directory.

**4. Run "usbreset**"
In the same terminal window you still have from the previous step run:

sudo ./usbreset

With this command you will initiate a reset of all USB devices - it is like disconnecting and reconnecting all USB cables. Therefore you should be careful using this command when using USB devices such a USB disks or cameras while files being transferred between the USB device and the computer. I recommend only to use the command when you have no activity with any of the connected USB devices.

**Summary**
This program fully solves my issue. I can send the backup USB disk to sleep 90 % of the week and can easily reactivate it without unplugging the USB cable by just running "sudo ./usbreset"

---

### Post by Gamzarme on 2011-02-04
Thanks for all the great research, Sven! The program definitely works, but doesn't exactly solve my problem. That's okay, though. See, I have a 3.5" USB card reader unit that plugs into my board in two places. One lead handles the four card slots and another USB line supports a USB plug next to the card slots.

The program correctly reconnects the USB slot, but the card slots (which show up as four different drives in Computer) do not reset. Oh well, time to restart my machine. =P

---

### Post by malmjako on 2011-02-13
> **Sven6210 said:**
> When I choose "Safely remove disk" in Nautilus the disk is powered off (not turning, no LED light).

Is it possible to do this from the command line? The reason for asking is that I make a backup each time the computer is started, after which I unmount the backup disk. It would be nice to also have it spin down at this point, and I'm not succeeding with either of hdparm, sg_start, and sdparm:

```
> sudo hdparm -Y /dev/sdf # Nothing happens

/dev/sdf:
 issuing sleep command
 HDIO_DRIVE_CMD(sleep) failed: Invalid exchange

> sudo sdparm --flexible --command=stop /dev/sdf # The disk "clicks" but continues to spin
    /dev/sdf: SEAGATE   ST3250823A        3.03

> sudo sg_start --stop /dev/sdf # The disk "clicks" but continues to spin. No output

```

---

### Post by Sven6210 on 2011-02-13
> **malmjako said:**
> Is it possible to do this from the command line? The reason for asking is that I make a backup each time the computer is started, after which I unmount the backup disk. It would be nice to also have it spin down at this point, and I'm not succeeding with either of hdparm, sg_start, and sdparm:

```
> sudo hdparm -Y /dev/sdf # Nothing happens

/dev/sdf:
 issuing sleep command
 HDIO_DRIVE_CMD(sleep) failed: Invalid exchange

> sudo sdparm --flexible --command=stop /dev/sdf # The disk "clicks" but continues to spin
    /dev/sdf: SEAGATE   ST3250823A        3.03

> sudo sg_start --stop /dev/sdf # The disk "clicks" but continues to spin. No output

```


Well, I never tried to make a "safely remove" in the command line but I am sure it is possible. Unfortunately I am very busy these days and I am not sure when I might have the time to give it a try. I will keep you posted here.

If you find the solution before me please post it here.

---

### Post by malmjako on 2011-02-19
> **Sven6210 said:**
> If you find the solution before me please post it here.

Will do...

---

### Post by warsev on 2011-02-23
I also have this exact same problem. I use multiple external USB hard drives and sometimes flash drives. Every time I use 'safely remove drive' that port remains powered off until I eventually reboot. Surely there is a better way; there must be some way to restore power. I have searched all over the internet and have not yet found a solution. I will be watching this thread, hoping that someone learns how to do this. IMHO the [SOLVED] indicator should be removed from this thread.

---

### Post by Sven6210 on 2011-02-24
> **warsev said:**
> I also have this exact same problem. I use multiple external USB hard drives and sometimes flash drives. Every time I use 'safely remove drive' that port remains powered off until I eventually reboot. Surely there is a better way; there must be some way to restore power. I have searched all over the internet and have not yet found a solution. I will be watching this thread, hoping that someone learns how to do this. IMHO the [SOLVED] indicator should be removed from this thread.

Actually this threat is solved. Please see my post dated May 24th, 2010 on the second page. I made a whole description how to reset the USB bus with a C program. The manual is made in a way that even a beginner should be able to do it. Please give it a try, it works perfectly for me.

Good luck

---

