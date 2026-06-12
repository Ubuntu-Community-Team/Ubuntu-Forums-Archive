---
title: "Sony Ericsson K550i not detected"
date: 2009-06-19
forum: General Help
---

### Post by 0v3rth3d4wn on 2009-06-19
[FONT=Lucida Console][FONT=Lucida Console][SIZE=2]Hello! I'm using Kubuntu Jaunty (9.04) and have the following problem: I plug my Sony Ericsson K550i into the USB but it seems not to be detected. Any suggestions? I did not find any software that could help me and I searched a lot of places and tried anything and still not resovling this issue. I really want to get this working so if you have come accross such problem or you know what could be wrong please reply. Thank you![/SIZE][/FONT]
[/FONT]

---

### Post by m4tic on 2009-06-19
I use a W880i and works fine, the question is wat do u want your pc to do with your phone?

---

### Post by 0v3rth3d4wn on 2009-06-19
Well I need to transfer some files from the computer to the phone but the phone is not detected at all when is plugged into an USB port. When I type lsubs it is also now shown there so it is really not detecting anything at all but the phone let me chose File Transfer and it seems to work but not detecting as removable device or usb device.

---

### Post by m4tic on 2009-06-19
common prob in windows but its not the OS fault, its your usb cable, try cleaning the phone with something, and to be sure your phone is detected, first connect it in phone mode. if ubuntu identifies the modem of your phone you can go on your phone to settings, connectins and usb-file trsnsfer.

tell me if it works coz thats what normally happens

---

### Post by 0v3rth3d4wn on 2009-06-19
I did all of this right now. I chose Phone Mode and also did not has any detection. From there File Transfer mode and again the same - nothing. On windows is working but I need it here on ubuntu.

---

### Post by m4tic on 2009-06-19
i need to know if it connects in phone mode or wat

---

### Post by 0v3rth3d4wn on 2009-06-19
Well, I chose Phone Mode, I can use all the phone features, the ubuntu is not detecting that there is something plugged, then I go to connectivity-> USB -> USB connection, waited a few seconds, the phone shows the screen which tells you that your phone is plugged and not to remove it without safety remove. Still the system is doing again the same. It does not detect it.

---

### Post by m4tic on 2009-06-19
to fix this you need to make a mount point.

You have to look what the device name is. To do this:

Code:
sudo fdisk -l
than you see all of your connected Drives (HDD,usb etc)


Code:
sudo mkdir /media/phone

sudo mount /dev/sdh1 /media/phone

---

### Post by m4tic on 2009-06-19
i dnt knw if that code will work, i use ubuntu

---

### Post by rahulmehtaraj on 2009-11-17
Hello I tried connecting USB using phone.it seems to be working perfectly for that mode.However I am not able to transfer files from my mobile phone to my Kubuntu laptop.
I am having Sony Erikkson W760a

---

### Post by rahulmehtaraj on 2009-11-17
> to fix this you need to make a mount point.

You have to look what the device name is. To do this:

Code:
sudo fdisk -l
than you see all of your connected Drives (HDD,usb etc)


Code:
sudo mkdir /media/phone

sudo mount /dev/sdh1 /media/phone

I did sudo fdisk -l
It is showing
/dev/sda1               1         972     7801856   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         972       13849   103439212+   7  HPFS/NTFS
/dev/sda3           13850       30401   132953940    f  W95 Ext'd (LBA)
/dev/sda5           13850       17889    32449219   83  Linux
/dev/sda6           22752       30401    61440000    7  HPFS/NTFS
/dev/sda7           17890       22751    39053983+  82  Linux swap / Solaris
I dont know what the first part of unknown is.When I did sudo mount /dev/sdh1 /media/phone after doing sudo mkdir /media/phone it shows -"[I][B]sudo mount /dev/sdh1 /media/phone
mount: special device /dev/sdh1 does not exist[/B][/I]"

---

### Post by StuartN on 2010-02-25
Sony-Ericson memory is full?

I just had this problem, although the phone had connected in the past. dmesg showed a string of USB error -62 messages.  It seems that there must be 2 MB or more of free memory on the phone in order to connect.

I deleted some images and the phone then connected fine.

---

