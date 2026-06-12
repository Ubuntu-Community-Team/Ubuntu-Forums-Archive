---
title: "help me i do not know how to reboot to windows"
date: 2009-03-22
forum: General Help
---

### Post by floatingab on 2009-03-22
i have finished install ubuntu,but i do not know how to retoot to windows,when i restart it ,it is automatically log in to the ubutu,help me

---

### Post by Aizawa on 2009-03-22
If you did everything with default settings, you should have installed the GRUB boot manager (I think that's the name - Can't be bothered looking it up).

When you start up the computer, GRUB is going to give you a list of options; you simply press your keyboards arrow keys to select an OS and the enter key to boot that OS!

I hope that helped!

---

### Post by floatingab on 2009-03-22
but there is no list of options
when i press esc then have a list but do not have vista system, just three ubuntu choices, my operation system is vista, how can i do that

---

### Post by howefield on 2009-03-22
What is the output from the command

```
sudo fdisk -l
```

---

### Post by Aizawa on 2009-03-22
Are you sure you didn't use your whole hard drive for your Ubuntu partition?

---

### Post by floatingab on 2009-03-22
when i press the esc
the list is like this
ubuntu
ubuntu recovery
ubuntu something like this i can not remember
otherwise it will restart to ubuntu not reboot into windows
please help me !!!!!!!!

---

### Post by floatingab on 2009-03-22
i am not sure, how can i know it whether i use the whole hard disk

---

### Post by floatingab on 2009-03-22
so terrible what can i do!!!

---

### Post by howefield on 2009-03-22
Post the output from the command I gave you so we know if you still have a windows partition or not.

---

### Post by floatingab on 2009-03-22
i think i use the whole hard disk to install it, because when i open the compuer there is just cdrw/dvd rw, and system file
so i can not describe how i feel now
if i have a recovery cd, how can i restore my previous system

---

### Post by floatingab on 2009-03-22
i do not know how can i check it
i am so disappointment now

---

### Post by mlentink on 2009-03-22
boot into ubuntu
Click your 'Applications'  tab just next to the ubuntu logo
Move to 'Accessories' and within that to 'Terminal' And select the latter

A window will open up with a prompt like 'you@yourmachine:~$'
at the blinking cursor type 
```
sudo fdisk -l
```Please note that the last character is a lowercase 'L', not a 1!

copy the results and paste them here, so we have some more info to help you

---

### Post by Jimmyfj on 2009-03-22
> **floatingab said:**
> so terrible what can i do!!!

If you have an old Win98 disk, either on Cd or floppy you can boot up the computer on this. On Cd you chose to boot the system with CD-ROM-support.
When booted, you type in this command:

```
fdisk /fixmbr
```

This should fix your Master Boot Record, Track 0,0 on your hard drive. 

But before attempting that you could boot up the system in Ubuntu. Once inside Ubuntu you go to Places>Home Folder. From here you should be able to see yuor Vista partition. If you can't se it, you most likely deleted it during install.

---

### Post by floatingab on 2009-03-22
please help me
so disppointed, what can i do
can i recovery my previous setting

---

### Post by LiamWilson on 2009-03-22
> **floatingab said:**
> 
If I have a recovery cd, how can I restore my previous system?

the same way you installed Ubuntu, put the CD in, and Restart. But this will erase your Ubuntu install.

---

### Post by floatingab on 2009-03-22
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bf30b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by mlentink on 2009-03-22
I am very, very sorry.
Most likely you used the 'use entire disk'option during the installation of Ubuntu. Your windows partition is gone, and you can only make you machine boot up windows again by reinstalling it. If you have a original Windows disk or recovery disk insert it in you cd-drive and follow the instructions.

---

### Post by nothingspecial on 2009-03-22
I`m sorry but it looks like windows and all your data are gone.

---

### Post by floatingab on 2009-03-22
i can see it, does that mean, i am not deleted ?

---

### Post by floatingab on 2009-03-22
so disappointed!!! crying!!!!!

---

### Post by floatingab on 2009-03-22
no other solutions

---

### Post by LiamWilson on 2009-03-22
Oh my, I'm sorry to hear that. Have you a System Recovery CD?

---

### Post by nothingspecial on 2009-03-22
You have reformatted your hard drive and installed Ubuntu where windows once was. Without some very expensive forensic software it is unlikely you will be able to recover any data.

So you have a decision. Do you want to wipe Ubuntu and reinstall windows or do you want to start using ubuntu?

---

### Post by mlentink on 2009-03-22
> **floatingab said:**
> no other solutions
I am afraid not.  If you had some very very valuable data perhaps a data-forensics expert may be able to recover bits and pieces, but I sincerely doubt it, since during the installation your disk was repartitioned and formatted.
Windows will do the same when you reinstall it. 

So again, I'&#7743; really sorry, but I hope you have a fairly recent backup, otherwise...

---

