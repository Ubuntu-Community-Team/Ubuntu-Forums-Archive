---
title: "urgent help"
date: 2012-06-10
forum: Desktop Environments
---

### Post by manas87p on 2012-06-10
I was finding that if any way to uninstall windows program then i found a forum containing this 
cd $HOME rm -rf .wine 
rm -f $HOME/.config/menus/applications-merged/wine* rm -rf $HOME/.local/share/applications/wine rm -f $HOME/.local/share/desktop-directories/wine* rm -f $HOME/.local/share/icons/????_*.{xpm,png} rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}

then my all files in C (desktop, download, documents around 30 GB) 
was deleted or hidden. then i noticed that I don't have permission to install, download from any torrent software. when i install from terminal shown that ....permission denied... are you root.Even my desktop image not there.Please help me what to do

---

### Post by UltimateCat on 2012-06-10
Windows has a system restore point.
If you are able to set another restore point you should be ok.

This is the only way that I know to get back to safety-

```
rm

```
rm means remove....

Are you using Ubuntu or some other distribution of Linux?  If so which OS besides Windows?

---

### Post by manas87p on 2012-06-10
> **UltimateCat said:**
> Windows has a system restore point.
If you are able to set another restore point you should be ok.

This is the only way that I know to get back to safety-

```
rm

```rm means remove....

Are you using Ubuntu or some other distribution of Linux?  If so which OS besides Windows?
 I am using ubuntu 12.04. before I installed windows file(office, photoshop) with WINE. I am very new user of ubuntu. I do not understand what to do. My those file was very impotant. please help..

---

### Post by The Cog on 2012-06-10
Sorry, but it's not going to be easy. Wine has this hidden directory .wine in which it keeps everything in its emulated C drive (in directory .wine/drive_c). If you deleted the .wine folder with rm -rf then you have deleted all its C drive contents.

There is a program called photorec that can scan a disk for the remains of files. It's in the repositories. If the files are important enough to you, you could install photorec and get it to save everything it can find to a USB drive. But there's no guarantee that it will find all your files, and even if it dies, it just gives the files numbers, so you will spend hours looking through all the rescued files trying to work out what is what.

---

### Post by David Andersson on 2012-06-10
> **manas87p said:**
> I was finding that if any way to uninstall windows program then i found a forum containing this 

As others said, that seems to remove all local settings for wine and its file structures. If you want to remove a particular program installed within wine I think the menu entry "Uninstall Wine Software" should be used (same as Add/Remove program in Windows). But that is too late now.

> **The Cog said:**
> 
There is a program called photorec that can scan a disk for the remains of files. It's in the repositories. If the files are important enough to you, you could install photorec and get it to save everything it can find to a USB drive.

To recover as much as possible it is important to use the disk as little as possible in the time after the files was removed and before a file recovery program such as photorec is used. So, stop using your system and run from a liveCD or liveUSB. In the live session install *photorec*, or *foremost*, or *recoverjpeg*.

If the files you lost are just windows programs, then don't bother recovering files. Install them again when you have wine up and running again. If you have lost pictures, musik, videos or office documents the recovery program (*photorec*, *foremost*, or *recoverjpeg*) might find some or most of them, but they will find a lot of unrelated files (files that have not been deleted, in your home and in the system, and files that have been intentionally deleted, by you or by the system during e.g. updates). It will be a lot of work to sort things out afterwards. And you need free disk space, of about the size of the partition you are recovering from, to save recovered files in. A usb-thumb-memory is probably not enough.

A lot of work, and no guarantee it finds everything. But good practice.

Do you have a backup?

---

