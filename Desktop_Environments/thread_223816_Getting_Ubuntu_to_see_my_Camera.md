---
title: "Getting Ubuntu to see my Camera"
date: 2006-07-27
forum: Desktop Environments
---

### Post by NZ-Wanderer on 2006-07-27
Hi there...
Was wondering if someone could possibly help me...

I have a Megxon Model SX301A digital camera, and no matter what I do I can't seem to get it to be read by Ubuntu..
I have gthumb installed but it doesn't know the camera is there
I have also installed digikam, but that doesn't find my camera either..

I contacted tech support, and all they said was:

> This camera support 2 function mode when connect to PC :
1. Mass Storage Device which is same as a card reader.  This driver was built-in Linux new version (sorry I forget which version).  So we don't need to install any driver for it.
2. Web Camera, this driver only support Windows O.S. And we have not for Linux.

Sooo I think I might be missing something..

If I click on "computer" in "places" and then plug my camera in I get an icon with the word "drive" under it and a usb icon above it appear, however when I click on the icon it says:

> Opening drive, you can stop this operation by pressing cancel.

then after a minute or so it pops up a message:

> Unable to mount the selected volume.

Show more details says:
> mount: special device /dev/sda does not exist
mount: special device /dev/sda does not exist
error: could not execute pmount

Any ideas anyone??

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

---

### Post by simonn on 2006-07-27
Open up Device Manager (it is a menu option - just cannot remember where).

Now unplug your camera from the USB port, wait a bit and plug it in again. Are any devices added?

---

### Post by NZ-Wanderer on 2006-07-27
Thanks for the reply, Did that :D  - first picture is without the camera plugged in, second picture is WITH the camera plugged in...

[[IMG]http://img220.imageshack.us/img220/9269/screenshotik6.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotik6.png)............[[IMG]http://img220.imageshack.us/img220/3651/screenshot1eq6.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshot1eq6.png)

I took the pictures cause even tho I know it changed, I wouldn't have a clue what it means or what I am supposed to do...

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

> **simonn said:**
> Open up Device Manager (it is a menu option - just cannot remember where).
Now unplug your camera from the USB port, wait a bit and plug it in again. Are any devices added?

---

### Post by simonn on 2006-07-27
Could you remove your camera and from a terminal do:

```

$ lsusb > camera-unplugged

```

Then plug it in, and after a minute or so:

```

$ lsusb > camera-plugged

```

And then attach the camera-* files created to this thread.

Probably easier than working with screenshots.

FWIW, it looks like the volume (i.e. partition) on the cameras flash memory is not being picked up correctly - but that is just a guess from the screen shot.

---

### Post by NZ-Wanderer on 2006-07-27
Hokay, I tried that...

However I do not understand what you said about

> And then attach the camera-* files created to this thread.

Attach what files? and where are they??

---

### Post by simonn on 2006-07-27
The > in the commands above essentially means, run the command (lsusb in this case) and instead of displaying the output on the screen create a file and write the output to it. In this case the  files are camera-unplugged and camera-plugged.

Try running just:

```

lsusb

```

And comparing it to the contents of the camera-* files you created - open them in a text editor.

The * is a wild card. For instance:

```

$ ls a* 

```

would list any file in the current directory which begins with 'a'.

In this case camera-* would match camera-plugged and camera-unbplugged.

The files will be located in the directory you were in when you ran the commands.

---

### Post by NZ-Wanderer on 2006-07-27
Ahhh now I get you, thank you...

Hokay, contents of Camera-Unplugged and Camera-plugged are the same

Bus 002 Device 004: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0458:0019 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 003: ID 06a3:0255 Saitek PLC 
Bus 001 Device 001: ID 0000:0000

---

### Post by simonn on 2006-07-27
Doh! Sorry... it's friday...

use lshal, not lsusb.

---

### Post by NZ-Wanderer on 2006-07-27
Ahhh that a big difference thank you :D :D 

Here are the files you requested, I had to ZIP them so I could attach them..

---

### Post by simonn on 2006-07-28
Ok. The camera is being assigned to /dev/sda. There is a possibility that when you plug the camera in again this will change, so after the next time you plug it in, do the following:

```

$ dir /dev/sd*

```

The camera should be assigned to one of the returned files, so use that in place of /dev/sda below.

Can you try the following:

```

$ sudo mkdir /mnt/temp
$ sudo mount /dev/sda /mnt/temp

```

If this does not succeed, please post the output from the commands.

If it does, browse to /mnt/temp and check to see if you can browse the camera's file system.

---

### Post by NZ-Wanderer on 2006-07-28
Thanks again for the help...

This is the result

john@ubuntu:~$ sudo mkdir /mnt/temp
Password:
john@ubuntu:~$ sudo mount /dev/sda /mnt/temp
mount: you must specify the filesystem type
john@ubuntu:~$

---

### Post by simonn on 2006-07-28
Ok. It is not using /dev/sda as the only partition. Normally /dev/sd? (where ? is a letter) will refer to the drive and /dev/sd?x (where x is a number) refer to the actual volumes (i.e. partitions). However, it is possible to use the device name as a volume as well (e.g. a cd in a cd drive is just one volume and is refered to as the device e.g. /dev/hdc). I thought this may have been confusion HAL, but it looks as if this is not the case.

Unplug the camera.

Wait a short while.

```

$ dmesg > dmesg-unplugged

```

Plug the camera in.

```

$ dmesg > dmesg-plugged

```

Attach dmesg-* to the thread.

This should show some errors.

---

### Post by NZ-Wanderer on 2006-07-28
Here ya go :)

---

### Post by simonn on 2006-07-28
Try mounting /dev/sda1 like we tried with /dev/sda before.

---

### Post by NZ-Wanderer on 2006-07-28
Hehehe tried that with a few of them...

john@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
mount: you must specify the filesystem type
john@ubuntu:~$ sudo mount /dev/sda0 /mnt/temp
mount: you must specify the filesystem type
john@ubuntu:~$ sudo mount /dev/sda2 /mnt/temp
mount: you must specify the filesystem type
john@ubuntu:~$

---

### Post by simonn on 2006-07-28
????

Sorry, I am completely stumped.

What do you do in windows?

---

### Post by NZ-Wanderer on 2006-07-28
In windows all I did was put the driver CD into the drive and install the drivers.

Ohwell, thanks for all the help...:D

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

---

### Post by NZ-Wanderer on 2006-07-28
I have contact the cameras tech support people again and have pointed them at this thread, maybe they might have some idea??

> **simonn said:**
> ????
Sorry, I am completely stumped.
What do you do in windows?

---

### Post by Txukie on 2006-08-08
try using

sudo mount -t vfat /dev/sda1 /mnt/temp

---

### Post by NZ-Wanderer on 2006-08-08
Thanks for the message, however I get this:

john@ubuntu:~$ sudo mount -t vfat /dev/sda1 /mnt/temp
mount: mount point /mnt/temp does not exist

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

> **Txukie said:**
> try using
sudo mount -t vfat /dev/sda1 /mnt/temp

---

### Post by cwaldbieser on 2006-08-09
> **NZ-Wanderer said:**
> Thanks for the message, however I get this:

john@ubuntu:~$ sudo mount -t vfat /dev/sda1 /mnt/temp
mount: mount point /mnt/temp does not exist

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

You need to create the folder you want to mount the camera on.  Try:
```

$ sudo mkdir /mnt/tmp

```
first.  That will make the folder.  Then run the previous command to mount it.

---

### Post by NZ-Wanderer on 2006-08-09
Did:

john@ubuntu:~$ sudo mkdir /mnt/tmp
Password:

Then tried first without the camera plugged in, and then with it plugged in, both times I got the following:

john@ubuntu:~$ sudo mount -t vfat /dev/sda1 /mnt/tmp
mount: special device /dev/sda1 does not exist

Also tried that line with sda0, and sda2

> **cwaldbieser said:**
> You need to create the folder you want to mount the camera on.  Try:
```

$ sudo mkdir /mnt/tmp

```
first.  That will make the folder.  Then run the previous command to mount it.

---

### Post by cwaldbieser on 2006-08-10
> **NZ-Wanderer said:**
> Did:

john@ubuntu:~$ sudo mkdir /mnt/tmp
Password:

Then tried first without the camera plugged in, and then with it plugged in, both times I got the following:

john@ubuntu:~$ sudo mount -t vfat /dev/sda1 /mnt/tmp
mount: special device /dev/sda1 does not exist

Also tried that line with sda0, and sda2

Well, you have to use the "dmesg" command that someone posted earlier to figure out what device file the computer creates when you plug your camera in.  It is a little difficult to explain the full process, but basically:

1) $ dmesg
Scan output for something like "created device node sdb1".  In that case /dev/sdb1 is the device.
2) mount the device to an existing directory
$ sudo mount -t vfat <device file> <folder>

If your camera looks like a mass storage drive to the computer, this should work.

If it is a hassle for you, it might be easier just to get a cheap card reader (SanDisk makes some that look almost like thumb drives).  Just pop your camera card in the reader and plug the reader into the USB drive.

If you have a thumb drive or other USB device, you may want to see if you can get those working first to make sure there isn't any problem with your USB drivers.

---

### Post by NZ-Wanderer on 2006-08-10
Thanks for the message...
I have just got myself one of these little things

[http://www.geeks.com/details.asp?InvtId=UCR54IN1B&cpc=RECOM](http://www.geeks.com/details.asp?InvtId=UCR54IN1B&cpc=RECOM)

Haven't put it in yet, so hope it works...:D 

> **cwaldbieser said:**
> If it is a hassle for you, it might be easier just to get a cheap card reader (SanDisk makes some that look almost like thumb drives).  Just pop your camera card in the reader and plug the reader into the USB drive.

---

### Post by NZ-Wanderer on 2006-08-11
Yup, putting that card reader/writer into my computer made Ubuntu sit up and start reading things, it now reads my Camera memory stick perfectly.. :)
Many thanks to everyone for their help...

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

---

