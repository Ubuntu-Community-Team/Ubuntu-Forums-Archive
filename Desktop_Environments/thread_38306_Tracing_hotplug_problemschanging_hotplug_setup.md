---
title: "Tracing hotplug problems/changing hotplug setup"
date: 2005-05-30
forum: Desktop Environments
---

### Post by cleary on 2005-05-30
This one is a bit of a doozy, and I may need to actually post this in the Livecd section, but I'll see how we go here anyway -

In short:
**[size=4]Can anybody give me any hints or tips on how I might go about making Kubuntu use the standard hotplug scripts instead of what appears to be a "customized initrd (hotplug) configuration"?[/size]**

I'm in the process of building a hybrid LiveCD based on the Kubuntu LiveCD Mainmodule, and the Morphix0.5pre5 basemodule. (To save the question being asked the reasons behind doing this are outlined [here](http://www.ubuntuforums.org/showpost.php?p=193386&postcount=2))

**MY RESEARCH SO FAR:**

In order to get it to work, all I've really had to do is extract the Mainmodule off the Kubuntu 5.04 Livecd, recompress it in the fs Morphix uses for it's mainmodules and tada! It works, almost ;)

Where I'm having issues is with the Hotplug system being
a) Unreliable
b) Not running the scripts to set up icons on the desktop

I'm not new to building LiveCDs, but most (if not all) of my experience has been gained by modifying existing setups for my own needs. Which means that I haven't had a lot of experience getting into the nitty gritty of the boot process, and various setups available. Now, what I've found is:

From the Hotplug manpages:
*The  hotplug  program  path name is registered in /proc/sys/kernel/hotplug, and normally holds the value /sbin/hotplug.  Except for  specialized configurations such as initrd(4) configurations...*

The value contained in my /proc/.../hotplug file is 
/sbin/udevsend 
**not** /sbin/hotplug as suggested by the manpages. 
I am guessing from this that it is a specialized initrd configuration. On this initrd topic, if I 
```
ls -l /
...
lrwxrwxrwx    1 root  root     28 May 19 21:15 [color=red]initrd.img[/color] -> boot/initrd.img-2.6.10-5-386
...
lrwxrwxrwx    1 root  root     12 May 19 21:22 [color=blue]vmlinuz[/color] -> boot/vmlinuz
```
The vmlinuz link is valid, contents of /boot :
```
lrwxrwxrwx  1 root root      14 Apr  1 18:00 [color=blue]vmlinuz[/color] -> vmlinuz-2.6.11
-rw-r--r--  1 root root 1576242 Mar 15 17:07 vmlinuz-2.6.11
```
But there is no initrd-xxxx.img in /boot - comparing the root filesystem with a mainmodule developed specifically for morphix shows that /initrd.img link doesn't exist in the Morphix configuration. 
From the initrd manpages, initrd is a tiny block device created on a ramdisk, and linked to in /dev/initrd. This does not exist in /dev of my Morphix build.

What I've concluded from this (based on my very limited understanding of the whole situation) is that Kubuntu uses a "specialized initrd configuration". 
I'm also assuming due to the lack of initrd stuff where it should be, that Morphix doesn't use a "specialized initrd configuration".

In order to keep my mainmodule compatible with the Morphix basemodule, I reckon I need to make the mainmodule use the standard hotplug setup - unfortunately, it doesn't seem to be as simple as changing the entry in /proc/sys/kernel/hotplug because it won't let me edit it.

I hope this makes sense - I'll probably make a few changes as I reread it. The areas I'm working in are unfamiliar to me, so apologies for any errors  :neutral:

---

### Post by cleary on 2005-05-30
**_Reasons behind the Kubuntu/Morphix hybrid LiveCD:_**
**Background:**
I'm building this LiveCD for use in a production environment. We've been using an early version of Morphix (0.41d basemodule 2.4.x kernel) with a customised Gnome 2.4 Mainmodule. This hybrid project is an upgrade to this current environment.
Some advantages to using PCs booting LiveCDs:
Stable – a hang of any kind can be resolved with a reboot
Speed – We have the machines loading the iso into ram and running out of a ramdisk
Support – any hardware failure can be resolved by removing the usb pendrive (for persistent storage), the CD, replacing the offending item, and reinserting the cd, and pendrive.
There are other reasons behind the move but think about how they can be of use to your specific environment, and I think you'll find them an attractive proposition. 
We run them on 3GHz/1024MB/15”LCD Dell Optiplex GX270s, soon to be replaced with A64 3400+/2GB/19” LCD beasties.

**Why Morphix + Kubuntu?**
Each project has it's advantages which I want to take advantage of:
**Kubuntu** – great support network, new packages available, consistent interface if we want to roll out machines with Kubuntu on a hdd install.
**Morphix** – Modular design, updates to the BaseModule can be easily integrated with the mainmodule without any (major) changes to the Mainmodule.

At this stage, the project's success isn't guaranteed, this is basically a feasibility test to see if I can get the thing going, and going well. So far it's looking really promising :)

---

### Post by cleary on 2005-05-31
bump

---

### Post by cwaldbieser on 2005-05-31
Well, I am not a Morphix expert, so I can't help you there.  However, I can explain why you can't edit /proc/sys/kernel/hotplug.  The /proc filesystem essentially is showing you running processes.  It is a reflection of what is actually running in user and kernel space, so you can't change it.

BTW, my Kubuntu responds with /sbin/hotplug when I cat that file.  It also looks like /etc/init.d contains a hotplug script which presumably starts the hotplug daemon at boot time.

---

### Post by cleary on 2005-06-01
Hi - thanks for the reply :)

It's interesting that your Kubuntu uses /sbin/hotplug when you cat /proc/sys/kernel/hotplug because I have two other machines here running Kubuntu Hoary (laptop and a desktop) and they both reference /sbin/udevsend...
I'm wondering if you (or I) may be using the Hoary preview install??? I'm definitely not using preview for the LiveCD.

Anyway, I found a resolution of sorts to the unreliability problem. It seemed that the morphix basemodule was loading and running it's own hotplug system very early in the boot process, and then I'm assuming Kubuntu was setting up for using it's custom hotplug system, without me explicitly running it (note that I didn't start the /etc/init.d/hotplug script anywhere) - hence the different /sbin/<script> references.
So I uninstalled hotplug from the Kubuntu Mainmodule, remastered and now cat /proc/sys/kernel/hotplug shows /sbin/hotplug.
The /sbin/hotplug script actually got deleted in the uninstall, so I copied it in from one of my hdd installs (but haven't bothered tracing what it does just yet).

This seems to have stabilised my usb storage devices (I would find if I rebooted with one still plugged in, it would throw errors in dmesg, and I'd have to unplug and replug it to get it work). I've just rebooted about 8 times in a row with files on the device in various states and it remounts fine :)

All I need to work out now is how to get it dropping icons on the desktop (and removing them) as I un/plug devices :)

---

### Post by cwaldbieser on 2005-06-02
I actually wrote a shell script to put the icons on the desktop-- it was pretty easy.  Removing the icons should have been easy, too, but for some reason the hotplug remove event never seemed to fire for me.

Here is a message I posted on the Kubuntu mailing list that explains what I did:
-----------------------
At the konsole:

$ lsusb

Take note of the output.  Now plug in your flash drive and issue the command 
again.  There should be an extra line that corresponds to your USB device.  
There may even be a description that identifies it.  There is an ID number 
for the device in the format ####:####.  You need to record that ID number 
for later.

Now you should have a directory called /etc/hotplug/usb.  It may or may not 
already have some stuff in there.  I needed two add two files to hook my 
drive into the hotplug system.  The first is a file that you call something 
like "flashdrive.usermap", and the second is a matching script that would 
just be called "flashdrive" (substitute "ipod", "pendrive", or whatever).

The flashdrive.usermap file should contain a line like this:

flashdrive 0x0000 0x05dc 0x0080 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 
0x00000000

The first field is the name of the other file (the script file).  The second 
field is just zeroes.  The 3rd and 4th fields match the pieces of the ID you 
copied down before.  In thi example, my usb drive had an ID 05dc:0080.  The 
"0x" prefixes on each number is notation to indicate these numbers are 
hexidecimal numbers (base 16).  The rest of the fields are just zeroes.

Now the second file is a script you write to do something when the hotplug 
system detects your device going in or out of the usb port.  I wrote the 
following little script, which creates a device icon on my desktop:

---------- start script "flashdrive" ---------------------
#!/bin/bash

#If the USB device is not plugged in (e.g. during bootup), then skip trying to 
perform an action.
if [ -z "$(lsusb | grep 05dc:0080)" ]; then #usb device ID goes here.
    exit 0
fi
if [ "$ACTION" = "add" ]; then
    #Sleep until the device becomes available.
    while [ ! -e /dev/sdb1 ]; do
        sleep 1
    done

    #Make the mount point and mount if it does not exist.
    mkdir -p /media/sdb1
    mount /dev/sdb1

    #Create the desktop icons on each user's desktop.
    for desktop in /home/*/Desktop
    do
        cat > "$desktop/USB Drive.desktop" << DRIVEFILE
[Desktop Entry]
Dev=/dev/sdb1
Encoding=UTF-8
Icon=hdd_mount
MountPoint=/media/sdb1
ReadOnly=false
Type=FSDevice
UnmountIcon=hdd_unmount
DRIVEFILE
    done
fi
---------end script "flashdrive" ------------

The 5th line in the script reads:

if [ -z "$(lsusb | grep 05dc:0080)" ]; then #usb device ID goes here.

And you need to replace the 05dc:0080 with your device ID.  This part of the 
script makes sure the device is actually plugged in before trying to do 
anything else-- the hotplug system fires it when you boot up, even though the 
drive isn't plugged in, so you need to ignore it or you could end up hanging 
for a while.

The next part of the script just makes a mount point and mounts the drive.  
You may need to tweak this if your device is not mounted on /dev/sdb1.  The 
last part of the script creates the device icon file on your desktop.

Not exactly the most elegant solution in the world, but DYI folks may want to 
give it a try.  Maybe someone will come up with something better that doesn't 
require hard coding in the specific device IDs...

---

### Post by cleary on 2005-06-07
Wow - I honestly didn't expect anyone to go to that much effort  :grin: 
Thanks a lot for the reply, while not a direct solution to what I'm after, there's certainly some useful stuff in there for me. Unfortunately, I need this build to cater to x number of different usb devices, not just my own.

I've just found some morphix specific apps for usbmounting that may do the trick, so I'll give them a go and see what happens :)

The help is greatly appreciated   =D>

---

