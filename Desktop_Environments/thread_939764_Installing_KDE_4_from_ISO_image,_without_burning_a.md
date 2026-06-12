---
title: "Installing KDE 4 from ISO image, without burning a disc... Please help!"
date: 2008-10-06
forum: Desktop Environments
---

### Post by 3rag0n on 2008-10-06
I'm using ubuntu HH ultimate with KDE *3-point-latest* and GNOME, and I desperately want KDE 4.1.1...
I have the ISO image of Kubuntu with KDE 4.0, and i understand that i must first install this kde 4.0 and then update online to 4.1.1.
And i'm currently in an area where there are no blank cd's for sale in a 5 km radius. 

I was wondering if there was any way of installing KDE 4.0 from the iso to my existing HH installation, without burning to a disc. 

I tried the following things :
1. Extracted the files of ISO to a folder using *rt-click + extract here* , and then tried to make sense of the stuff contained within... no success. In suse, i could install the packages manually from the install disk but here i fail to understand the structure and the way the packages are organised. Since i already have an existing installation, i only want to install the kde 4 related packages and not the other stuff. I dont want to install a separate ubuntu with kde 4.

2. I tried to paste the extracted files in to a pendrive, and then boot. I also modified the bios settings to boot from my pendrive first, but nothing happened. grub started instead of the "try ubuntu" screen

3. Tried to locate an option in synaptic where there would be a facility of mounting an ISO instead of a CD-ROM. Found nothing of the sort.

I do not wish to install KDE from online sources, because of the lousy connection speed.

Please help, someone !!!:confused::(:confused:

---

### Post by 3rag0n on 2008-10-06
pleeez..... help...:confused:

---

### Post by Ed1000 on 2008-10-06
Well, I am not sure but I may know a workaround for the slow speed. How about putting your iso in a tar or deb form on a local web?

---

### Post by 3rag0n on 2008-10-06
> **Ed1000 said:**
> Well, I am not sure but I may know a workaround for the slow speed. How about putting your iso in a tar or deb form on a local web?

How exactly ....? I dont know how ... :(

---

### Post by maybeway36 on 2008-10-06
Unetbootin might be able to help you. [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by 3rag0n on 2008-10-07
> **maybeway36 said:**
> Unetbootin might be able to help you. [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Nice tool, but...
I dont wish to install kubuntu itself... only KDE 4 within my existing ubuntu partition...

Oh, by the way, IF i burn this kubuntu iso to a CD, will it give me an option of installing KDE 4 inside my existing ubuntu?
Something like... *update existing installation* ?

---

### Post by 3rag0n on 2008-10-07
Bump.

---

### Post by 3rag0n on 2008-10-07
b00mp

---

### Post by 3rag0n on 2008-10-07
aww.. bump. bump.

---

### Post by tacutu on 2008-10-08
i think you could mount the iso image:
```
sudo mount -o loop filename.iso /mnt/whatever
```

and then add /mnt/whatever to your repositories in /etc/apt/sources.list:

```
deb file:/mnt/whatever / hardy main restricted
```

or something along these lines. This will add the mounted iso image as a local repository. Then you can install whatever is in there.

---

### Post by Ed1000 on 2008-11-14
I see you have had some replies since I replied. Do you still need help?

---

### Post by chrestomanci on 2008-11-14
The process of creating a bootable USB drive is a bit more complex than just copying the files. You need to setup the boot block of the USB key correctly as well.

If you head over to [PenDriveLinux.com](http://www.pendrivelinux.com/) you should find all the instructions you need.

If you want to fool synaptic into thinking your ISO image is a real CD, then using the mount command as root should do the trick. Something like:
```

sudo mount ~/kubuntu-8.10-desktop-i386.iso /media/cdrom0 -t iso9660 -o loop

```

---

