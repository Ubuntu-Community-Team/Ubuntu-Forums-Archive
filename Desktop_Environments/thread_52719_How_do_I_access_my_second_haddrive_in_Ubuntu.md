---
title: "How do I access my second haddrive in Ubuntu?"
date: 2005-07-28
forum: Desktop Environments
---

### Post by bruin03 on 2005-07-28
Hi all,
I'm a recent user who decided to switch from win xp to Ubuntu for my regular desktoping. I had a second haddrive in windows with a lot of data, but I'm unable to see it in Ubuntu under the menu titled "Computer"

How do I access my second harddrive?

---

### Post by Sam on 2005-07-28
[UbuntuGuide - Windows](http://ubuntuguide.org/#windows)

---

### Post by bruin03 on 2005-07-28
[QUOTE=Sam][UbuntuGuide - Windows](http://ubuntuguide.org/#windows)[/QUOTE]

Hi, forgive my greenness, but I'm completely new to this Operating System and unix, and I don't quit understand the terminology. Could you please break it down for the layman? :)

---

### Post by thechitowncubs on 2005-07-28
[QUOTE=bruin03]Hi, forgive my greenness, but I'm completely new to this Operating System and unix, and I don't quit understand the terminology. Could you please break it down for the layman? :)[/QUOTE]
 Hyperlink:a hypertext link; a graphic or text string which, when clicked, opens a new web page or jumps to a new location in the current page.

---

### Post by bruin03 on 2005-07-28
[QUOTE=thechitowncubs]Hyperlink:a hypertext link; a graphic or text string which, when clicked, opens a new web page or jumps to a new location in the current page.[/QUOTE]
Very funny. Why must some of you linux guys be so smug?  8-[

---

### Post by bruin03 on 2005-07-28
I tried the following and these are the results:
[qoute]myusrnom@ubuntu:~$ sudo mkdir /media/windows
Password:
myusrnom@ubuntu:~$ sudo mount /dev/hda2 /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

myusrnom@ubuntu:~$

[/quote]what did I do wrong?  :-?

---

### Post by Sam on 2005-07-28
[QUOTE=bruin03]Very funny. Why must some of you linux guys be so smug?  8-[[/QUOTE]
Forgive him.

I'll try to explain.

First, find the Windows partition. Open a terminal and type (without the dollar sign, this means to type the command in a terminal)
```
$ sudo fdisk -l
```
The Windows partition is the one with 'HPFS/NTFS' in the System column. Note the corresponding device (e.g: /dev/hda1)

Then you need a mount point for this partition. This will create a new directory.
```
$ sudo mkdir /media/windows
```

Edit your fstab file, this contains every mounts to do on system startup.
```
$ sudo cp /etc/fstab /etc/fstab_backup
$ sudo gedit /etc/fstab
```

Add the following line at the end (/!\ replace '/dev/hda1' with the device found in the first step):
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

This is done, now remount every mount points:
```
$ sudo mount -a
```

You now have your Windows data under /media/windows.


Ask if you don't understand something. Or [RTFM](http://dictionary.reference.com/search?q=rtfm) :wink:

---

### Post by bruin03 on 2005-07-28
I got it. The trick was the $ sudo fdisk -l to find the name of the second disk. Thanks Sam.

---

### Post by Sam on 2005-07-28
[QUOTE=bruin03]I got it. The trick was the $ sudo fdisk -l to find the name of the second disk. Thanks Sam.[/QUOTE]
You're welcome! Enjoy Ubuntu Linux :wink:

---

### Post by cs378 on 2005-07-29
[QUOTE=Sam]Forgive him.

I'll try to explain.

First, find the Windows partition. Open a terminal and type (without the dollar sign, this means to type the command in a terminal)
```
$ sudo fdisk -l
```
The Windows partition is the one with 'HPFS/NTFS' in the System column. Note the corresponding device (e.g: /dev/hda1)

Then you need a mount point for this partition. This will create a new directory.
```
$ sudo mkdir /media/windows
```

Edit your fstab file, this contains every mounts to do on system startup.
```
$ sudo cp /etc/fstab /etc/fstab_backup
$ sudo gedit /etc/fstab
```

Add the following line at the end (/!\ replace '/dev/hda1' with the device found in the first step):
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

This is done, now remount every mount points:
```
$ sudo mount -a
```

You now have your Windows data under /media/windows.


Ask if you don't understand something. Or [RTFM](http://dictionary.reference.com/search?q=rtfm) :wink:[/QUOTE]

Yes i did this right, the windows ntfs drive is in the /media/windows/

but u know how to set a drive into the Places --> Computer?  ](*,)  ](*,) 


i have done the same thing in KUbuntu and works very well, but Ubuntu don't seem to do that


thx for helping big newbie  \\:D/  \\:D/

---

### Post by Sam on 2005-07-29
[QUOTE=cs378]Yes i did this right, the windows ntfs drive is in the /media/windows/

but u know how to set a drive into the Places --> Computer?  ](*,)  ](*,) 


i have done the same thing in KUbuntu and works very well, but Ubuntu don't seem to do that


thx for helping big newbie  \\:D/  \\:D/[/QUOTE]
I don't know how to add items in 'computer', but to add something in the 'Places' menu, open any open dialog (e.g. with gedit), then choose on the right any folder then clic 'Add'.

---

### Post by titus1950 on 2005-07-29
[QUOTE=cs378]Yes i did this right, the windows ntfs drive is in the /media/windows/

but u know how to set a drive into the Places --> Computer?  ](*,)  ](*,) 


i have done the same thing in KUbuntu and works very well, but Ubuntu don't seem to do that


thx for helping big newbie  \\:D/  \\:D/[/QUOTE]



 Erase the line in front of : ( works with vfat,don't know about ntfs I guess is the same)
 dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Save ....Reboot....,
Now windows will show on desktop,places and computer

Could you let me know if it works with ntfs,please.

---

