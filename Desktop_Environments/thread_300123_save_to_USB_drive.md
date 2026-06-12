---
title: "save to USB drive?"
date: 2006-11-15
forum: Desktop Environments
---

### Post by ja2z on 2006-11-15
When I try to "save as" to external hard drive I get the message" file does not exist".
Even when document has come from the external disk I can't save back to it.
Help please.
Ubuntu newbie ja2z

---

### Post by jd65pl on 2006-11-15
Assuming that the usb stick is mounted to media do:

```
ls -l /media
```

Check the permissions on the output of the command. if you are unsure about the permissions please do:

```
cd ~
ls -l /media > usbPerm.txt
```
This command will save the output to a file in your home folder called usbPerm.txt, post this file on the forum and I'll explain the permissions to you.

J

---

### Post by ja2z on 2006-11-15
> **jd65pl said:**
> Assuming that the usb stick is mounted to media do:

```
ls -l /media
```

Check the permissions on the output of the command. if you are unsure about the permissions please do:

```
cd ~
ls -l /media > usbPerm.txt
```
This command will save the output to a file in your home folder called usbPerm.txt, post this file on the forum and I'll explain the permissions to you.

J

Many thanks for your speedy reply.
Well I managed to create the usbPerm.txt file (there's a first time for everything they say, even Linux!!) Now I hope I've uploaded it OK.
As an intermediate Windows user this is really intriguing it's already a million times better experience than XP. I can't wait to ditch it completely.

---

### Post by jd65pl on 2006-11-15
Do this is the terminal:

```
chmod 777 '/media/Seagate 160'
```

This will enable you to write to the drive. I'm not sure if it will be persitant though, i.e. will remain in effect after a reboot or unplug of the drive.

---

### Post by ja2z on 2006-11-15
> **jd65pl said:**
> Do this is the terminal:

```
chmod 777 '/media/Seagate 160'
```

This will enable you to write to the drive. I'm not sure if it will be persitant though, i.e. will remain in effect after a reboot or unplug of the drive.

Well did that  got "changing permissions of '/media/Seagate 160': Read-only file system ja2z@jh-laptop:~$" Waited 10 minutes, closed terminal. Tried adding a tick to the "write" box in Seagate 160 properties/permissions but still got "couldn't change permissions ...because read-only" tried drag and drop and "save as" but no joy I'm afraid.
Sorry to be a pain.

---

### Post by jd65pl on 2006-11-16
Do you know if it is formatted to ntfs? Try doing

```
sudo chmod 777 '/media/Seagate 160'
```

---

### Post by ja2z on 2006-11-19
> **jd65pl said:**
> Do you know if it is formatted to ntfs? Try doing

```
sudo chmod 777 '/media/Seagate 160'
```

Yes, that was the problem. I had previously formatted the drive as NTFS and I saw somewhere a mention of linux needing the FAT32 format.
I have managed to partion the disk using Windows disk manager but now it has a primary FAT32 partition of 30GB and 130GB NFTS. It appears Windows won't make bigger partitions. Obviously it can be done as my other external drive is 250GB FAT32.

(The reason for not using this one is that it uses a PC HDD and needs an external power supply whereas the one I'm trying to reformat uses a  laptop Disk which takes it's power from the USB on my laptop which has Ubuntu on and makes the whole lot easily portable.)

So the next question is "How do you partition/format a disk using Linux?"
If you can help with this one I'd appreciate it but if not let me know and I'll go back to the forums.
Many thanks for you help and peseverance.

---

