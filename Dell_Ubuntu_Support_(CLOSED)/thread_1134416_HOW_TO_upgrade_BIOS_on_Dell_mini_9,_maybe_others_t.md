---
title: "HOW TO upgrade BIOS on Dell mini 9, maybe others too"
date: 2009-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2009-04-23
I recently upgraded the BIOS on my Dell mini 9, without using Windows. Now it is version A05, released a week ago. There are several ways to do this. here is what worked for me. If your computer also has Windows, it might be easier to use Dell's Windows-platform BIOS updater.

1. You will need a USB pendrive that you are willing to over-write (lose all information). Even a very small one will do.

2. You will need a FAT partition somewhere on your "hard drive" (solid state drive, on the mini 9). Probably you already have one.

3. Go to the Dell support site, and get the DOS version of the BIOS update software. Put a copy of the file on your FAT partition, and make note of its file name. If you have more than one FAT partition, use the first one.

4. Go to the FREEDOS site, and get balder.img here:
[http://www.freedos.org/freedos/files/](http://www.freedos.org/freedos/files/)
put this file in your home directory.

5. From Ubuntu, insert the USB pendrive. When it mounts, right-click to get its properties. Determine where it has mounted (probably /dev/sdb). In what follows, I will use "sdX" to refer to the USB. For best results, do not have any other writeable device connected to your computer.

6. Unmount the USB (leave it plugged in). In Terminal:

sudo dd if=balder.img of=/dev/sdX

7. Re-boot, and press 0 at the boot screen, to get the boot menu. Select "removable media" (your computer thinks the Balder USB is a floppy disk). When it boots, you will be in DOS, and see the A:> prompt.

8. Your computer must be on AC power, not battery. Change the volume to C: (which will be the FAT partition on the main drive). Then, type the BIOS updater file name:

A:>C:
C:>YOURBIOSFILENAME

9. Let the BIOS updater work. When it is done, the computer automatically reboots.

10. Your USB is not useful for anything else, while balder is there. To make balder go away:

sudo dd if=/dev/zero of=/dev/sdX

and maybe re-format it.

---

### Post by anjilslaire on 2009-04-23
Nice. 

However, if you've got your usb booting to DOS, you can simply put your bios files on the usb flash drive as well, then you don't need a fat partition on your SSD.

Just run the bios updater from the USB, thats what I do.

---

### Post by Rallg on 2009-04-23
Not everyone has a USB that can boot to DOS. If you use balder, as I wrote, then you cannot put the BIOS updater file onto the USB. That is because balder converts your USB to a "floppy disk" of size 1.4Mb, with no space to put any other software. That's why you need a DOS partition somewhere else.

---

### Post by anjilslaire on 2009-04-23
ah, ok. Good to know. Thanks for that. So it literally treats it as a floppy. Interesting. 
One more tool for the toolbox :)

---

### Post by shiningkenmonster on 2009-05-02
> **Rallg said:**
> 

6. Unmount the USB (leave it plugged in). In Terminal:

sudo dd if=balder.img of=/dev/sdX

7. Re-boot, and press 0 at the boot screen, to get the boot menu. Select "removable media" (your computer thinks the Balder USB is a floppy disk). When it boots, you will be in DOS, and see the A:> prompt.

8. Your computer must be on AC power, not battery. Change the volume to C: (which will be the FAT partition on the main drive). Then, type the BIOS updater file name:

A:>C:
C:>YOURBIOSFILENAME


I did: Re-boot, and press 0 at the boot screen, to get the boot menu. Select "removable media" (your computer thinks the Balder USB is a floppy disk). When it boots, you will be in DOS, and see the A:> prompt.

When it boots, I tapped 0. and selected the "removable device" option. It loaded a black screen. it just loaded grub and went straight into loading the computer. I did not see the A:> prompt. 

What went wrong? need trouble shooting help here. I am still using BIOS A00

---

### Post by anjilslaire on 2009-05-02
Try booting from USB, because that's what the device really is at the hardware level, before the image on the usb is launched, essentially turning it into a floppy.

Just a suggestion. As noted, I've not used Balder.

---

### Post by shiningkenmonster on 2009-05-02
Yeah, I've ran the "USB" section too. It just loaded a black screen and it just sits there and says 'FreeDOS.' thats it. nothing else happens.

anjilslaire, instead of using balder10.img, what program did you use?

can you list your steps on here for what you did to flash your bios?

---

### Post by anjilslaire on 2009-05-03
If you're at a FreeDOS prompt, you're probably sitting at A:> and can then complete the process.

Myse;f, I used an HP USB DOS boot utility under Windows to format my usb as a true DOS-bootable disk, and placed the bios on it also. I then booted my mini from my usb flash to a c:\ prompt, then simply ran the A05 bios app.

If you have access to a Windows system, you can get the HP utility from here:
[http://www.bay-wolf.com/usbmemstick.htm](http://www.bay-wolf.com/usbmemstick.htm)
Follw the instructions to get it created. I created an A05 folder, and put the A05 bios inside it.
After booting into DOS, I simply changed into the bios directory I made:
```

cd A05

```
Then executed the A05 bios .exe right from the usb stick. Let it run, and **don't interrupt it** even if it looks like nothing is happening at first. The system will eventually reboot itself upon completion

---

### Post by sir_nasty on 2009-05-13
I was trying to use your instructions and my usb stick made me mad so I found another way.... if you have a mini 9 then dell has a dos utility partion on your laptop but it's not mounted.

open a terminal
run:
mkdir -m 777 /media/fat32

then:

gksudo gedit /etc/fstab

add this line:

/dev/sda1 /media/fat32 vfat defaults,umask=000 0 0

ruN:

mount /media/fat32

then download the dell bios update
copy the update file to the /media/fat32 folder
now:
cd /media/fat32
sudo mv ./autoexec.bat ./autoexec.old

cd /boot/grub

gksudo gedit menu.lst

add this:

title dos
root (hd0,0)
chaniloader +1

edit the line in there that says "timeout 0" to be "timeout 3"

restart the computer, press esc when the grub loader shows up, arrow down, select dos, run the command to flash the bios!

---

### Post by anjilslaire on 2009-05-13
That probably works great if you have the original Dell install & partitions. That lasted about an hour on mine ;)

---

### Post by floborg on 2009-05-13
Hey, you've all heard about the new Linux app FlashRom (maybe has another name)?  It apparently can flash the BIOS from your Linux environment.  Might still be in beta...

---

### Post by appleguru on 2009-06-02
Easy tutorial here for upgrading your bios with just ubuntu and a flash drive:

[http://ubuntuforums.org/showpost.php?p=7336044&postcount=64](http://ubuntuforums.org/showpost.php?p=7336044&postcount=64)

---

### Post by anjilslaire on 2009-06-02
> **floborg said:**
> Hey, you've all heard about the new Linux app FlashRom (maybe has another name)?  It apparently can flash the BIOS from your Linux environment.  Might still be in beta...

Never a good idea to flash a bios while inside the OS, linux or Windows. Best to boot to another environment like DOS or another linux on a stick.

---

