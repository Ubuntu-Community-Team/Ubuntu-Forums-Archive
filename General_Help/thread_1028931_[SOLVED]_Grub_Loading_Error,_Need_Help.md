---
title: "[SOLVED] Grub Loading Error, Need Help"
date: 2009-01-02
forum: General Help
---

### Post by Sunspore on 2009-01-02
HI, I encounter similar problem now when I use LVM to transfer my linux. My Grub loader still display the old HDA directory although my linux in is HDA7 now.

I am using the live cd but when I tried to change the root to root=/dev/hda7

I cannot save, I was prompt that I do not have permission necessary to change the file. How do I do it.

Thanks

---

### Post by caljohnsmith on 2009-01-02
Sunspore, first you would want to mount the partition that has your Grub's menu.lst, which I assume is on your new hda7 partition:
```
sudo mount /dev/hda7 /mnt
```
And then you can edit the menu.lst by opening it as the root user:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
Let me know if that helps or if you run into problems.

---

### Post by Sunspore on 2009-01-02
Dear All,
         I transfer my linux to a new partition using LVM now I am unable to boot into linux. I think I would need to change the boot location to the new one with is /dev/sda7.

I am now running on the live disc, can anyone guide me on changing the boot details in the menu.lst . I tried to display and save but was unable to do it. Guess I need to type the commands in the terminal.

Can someone pls help me, thanks.

Below is the details.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       13038    84244860    f  W95 Ext'd (LBA)
/dev/sda3           13039       14593    12490537+  12  Compaq diagnostics
/dev/sda5            2551        9157    53070696    7  HPFS/NTFS
/dev/sda6            9158        9304     1180746   82  Linux swap / Solaris
/dev/sda7            9305       13038    29993323+  83  Linux

---

### Post by nemilar on 2009-01-02
try:



mount the boot partition so you can access the grub files:
```

sudo su
mkdir sda1 && mount /dev/sda1 sda1

```

Edit the menu.lst file:
```

vi sda1/grub/menu.lst

```


This part will depend upon your setup.  It might be best to post the output of the following before you proceed:

```
cat sda1/grub/menu.lst
```


But what you are going to want to do is find the boot item you've been using, which should be the default.  Find the line labled 'default':

```
default 0
```

Scroll down and find the clusters of lines starting with "title" and count to your default (counting from 0, so if your default is set to 0, it is the first one).  In mine I have:

```

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=6935698d-b65d-4eea-82bb-6d1a5f88aa82 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet


```


Look at the line labeled 'kernel'; for me my root partition is selected by UUID (root=UUID=6935698d-b65d-4eea-82bb-6d1a5f88aa82)  This is the info you want to change.

If you are using UUIDs, the easiest way to find the UUID you want is:

```
tune2fs -l /dev/sda7
```

if you have something marked LABEL there, you can use this:

```
e2label /dev/sda7
```

Which, to my knowledge, is the same as "volume name" printed by tune2fs.

Set the line in menu.lst with the new UUID or label, save, and reboot.

---

### Post by Sunspore on 2009-01-02
Hi, this is my details. I cannot seems to mount when I am running the live cd.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       13038    84244860    f  W95 Ext'd (LBA)
/dev/sda3           13039       14593    12490537+  12  Compaq diagnostics
/dev/sda5            2551        9157    53070696    7  HPFS/NTFS
/dev/sda6            9158        9304     1180746   82  Linux swap / Solaris
/dev/sda7            9305       13038    29993323+  83  Linux
ubuntu@ubuntu:~$

---

### Post by Sunspore on 2009-01-02
Hi when I type "vi sda1/grub/menu.lst" in the terminal I encounter blank with blue colour ~ at the side and nothing else

when I close the terminal and open again I got the below msg, how can I continue?

E325: ATTENTION
Found a swap file by the name "/var/tmp/menu.lst.swp"
          owned by: root   dated: Sat Jan  3 11:57:33 2009
         file name: sda1/grub/menu.lst
          modified: YES
         user name: root   host name: ubuntu
        process ID: 8321
While opening file "sda1/grub/menu.lst"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r sda1/grub/menu.lst"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/menu.lst.swp"
    to avoid this message.

"sda1/grub/menu.lst" [New DIRECTORY]
Press ENTER or type command to continue

---

### Post by Sunspore on 2009-01-02
and my sda1 is windows vista, I unable to find the root folder when I open the directory.

---

### Post by nemilar on 2009-01-02
Press enter and wait a couple of seconds, and it should show your menu.lst.

Optionally, delete the file /var/tmp/menu.lst.swp

---

### Post by nemilar on 2009-01-02
Ah, you are correct - I did not notice that the filesystem was ntfs.

Try perhaps mounting /dev/sda7 instead, and looking for boot/grub/menu.lst on there.

---

### Post by nemilar on 2009-01-02
Can you also please expand, "can't boot into linux?"  Do you still get Grub?


Assuming you still get the grub screen, once you find the menu.lst file, please post its contents

---

### Post by Sunspore on 2009-01-02
Hi I still got grub screen when I do a normal boot, however all the locations are now different as I have transfer the linux to a new partition, previous it resides in vista in wubi.

---

### Post by overdrank on 2009-01-02
Post merged :)

---

### Post by Sunspore on 2009-01-02
Hi, so what should I do next, I cannot seems to get anything out of this command "cat sda1/grub/menu.lst"

Thanks

---

### Post by Sunspore on 2009-01-02
I type 
sudo su
mkdir sda1 && mount /dev/sda7 sda1

am I correct

---

### Post by Noel96 on 2009-01-02
Here's a little program that I have found very useful for re-creating boot-ups. If you burn the CDROM iso image to disk, you can boot your system from it. Don't use the CD burning program that is default in Vista as it will burn the iso image as a file and not as an image. When you've burnt the image, restart your computer and boot from the CD with SuperGrub on it. The prompts explain step by step. 

Here's the homepage...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Here's a mirror for the iso file (0.9774 is the latest version)...

[http://forjamari.linex.org/frs/?group_id=61&release_id=664#664](http://forjamari.linex.org/frs/?group_id=61&release_id=664#664)

---

