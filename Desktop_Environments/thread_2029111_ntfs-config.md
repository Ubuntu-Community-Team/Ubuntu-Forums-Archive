---
title: "ntfs-config"
date: 2012-07-19
forum: Desktop Environments
---

### Post by Philip Gray on 2012-07-19
Good evening

I auto boot my Windows partitions using NTFS-CONFIG in 12.04. My issue is that when I try an unmount one of the drives in 12.04 I get an error message that only root can unmount it. Why is this happening? In my 10.04 this does not happen.

Regards
Philip

---

### Post by coffeecat on 2012-07-19
> **Philip Gray said:**
> NTFS-CONFIG

Not a good idea at all. That's an unmaintained and unreliable 3rd party app. I suggest you uninstall it.

What it will have done is to create an entry in /etc/fstab with certain mount options. You can fine tune these options manually to obtain what you need, but it's best to ask yourself why you need an entry in /etc/fstab at all. You can use the GUI to mount your NTFS partitions on an as-needed basis and then use the GUI to unmount them, which is possibly what is happening in 10.04. But if you do need to have a NTFS partition mounted during bootup - which is what an entry in /etc/fstab is for - post the output of:

```
cat /etc/fstab
```

And then someone can help you with the mount options. Post it anyway if you would prefer to use the GUI and someone can tell you which line to remove.

---

### Post by rukiaEnix on 2012-07-19
Yep, post it please. Why you need a third app when Ubuntu can do it.

---

### Post by Philip Gray on 2012-07-20
Hi coffeecat

In 10.04 my Windows partitions mount automatically on boot. I just prefer it that way. I find it suits my working environment. I would prefer to use the GUI. Forgive my ignorance by what does /etc/fstab do exactly? I will send off the cat /etc/fstab entry and post the response.

Regards
Philip

---

### Post by Philip Gray on 2012-07-23
Hi coffeecat

Here is the response from the cat /etc/fstab entry:

philip@philip-MS-7529:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda6 :
UUID=b76af271-0e61-46c3-bd8a-59a4e6ad0f0b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=7600EDC400ED8C05    /media/Music0    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sdb5 :
UUID=1ACC0295CC026AF9    /media/Music1    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sdb6 :
UUID=266805A7680576B9    /media/Music2    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sdb7 :
UUID=D6F408B5F4089A3F    /media/Music3    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=5E1897A0189775AD    /media/four    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda1 :
UUID=B8D63427D633E3F2    /media/one    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda3 :
UUID=44CC761BCC760786    /media/three    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda2 :
UUID=0402544E025446B8    /media/two    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda7 :
UUID=1812d18f-aca5-4f00-8b4c-8ce5fce89160    none    swap    sw    0    0


philip@philip-MS-7529:~$ 

Regards
Philip

---

### Post by Morbius1 on 2012-07-23
You may have missed the nuance of what coffeecat was trying to explain.

It comes down to this:
> In 10.04 my Windows partitions mount automatically on boot. I just prefer it that way.Then why are you trying to unmount it after it boots?

If you want the ability to mount and unmount as desired then don't use ntfs-3g and don't put anything in fstab. Mount it through Nautilus and unmount it through Nautilus.

---

### Post by coffeecat on 2012-07-23
> **Philip Gray said:**
> what does /etc/fstab do exactly?

fstab stands for filesystem table. It contains the information needed for the system to mount filesystems during the boot process.

There's nothing intrinsically wrong with the /etc/fstab lines for your ntfs partitions that I can see except, as you have discovered, you need to invoke root privileges to umount them. I have a similar situation with my Windows 7 and Ubuntu dual-booting laptop where I have a single NTFS data partition, not the large number that you have. I have a line in /etc/fstab which mounts this, but in the rare event of needing to unmount it, I simply open a terminal and use umount prefixed with sudo.

I agree with Morbius1. If you want those partitions mounted on bootup, why do you need to unmount them? Why not just rely on mounting and unmounting using Nautilus? If you do want to use fstab and then unmount, then open a terminal and:

```
sudo umount /dev/sdb5
```

...or...

```
sudo umount /media/Music1
```

... for sdb5 which is mounted on /media/Music1. You can use either the device or mountpoint with umount. Simply substitute the relevant details for other partitions.

If you want to get rid of your /etc/fstab entries and rely on Nautilus and don't know how to do this, post back and someone can take you through this.
 
The situation is no different for this from 10.04, so if you are finding a difference in 12.04 we'd need to know more about your 10.04 setup to explain this.

---

### Post by Philip Gray on 2012-07-24
Hi Morbius 1 and coffeecat

I have an issue with documents and spreadsheets that I have worked on at the office and then carry on working on at home. I do computer scripting for a program that is used in our call centre. I usually create a manual document, with screenshots, describing what I have done which I then distribute to our training section and the call centre senior supervisor. I have found that sometimes if I copy the documents from my usb stick to one of my windows partions and to my 12.04 installation, 12.04 will not let me modify them, I get an error message advising that  I need route privileges especially if I am trying to move the screenshots around. I thought that if I unmounted the partition and remounted it the issue may be solved. This does not happen in 10.04. My pc at the office is Windows XP SP3 and I have full admin rights on it.

I auto mounted my Windows partitions in 10.04 because I added bookmark links in Nautilus to various Windows folders that I use often like:- My Documents, my various mp3 folders, my flv and mp4 folders. I was hoping to do the same in 12.04. 

I have three hard drives in my system a 512GB, a 1TB and a 2TB. The 521GB one has my 9.04, 10.04 and Windows XP installation on it. It does not have any space on it for 12.04. So I purchased the 2TB which I partitioned into 5 partitions, one for 12.04 and the other 4 as backup for my 512GB and 1TB drives. The 1TB contains a copy of my 'My Documents' folders and the other folders I referred to. With two dvd writers and the two older drives I do not have any spare power sockets so I have to unplug the 512GB so I can plug in the 2TB. So if I am using the 12.04 drive I do not have the option to boot into 10.04 or XP.  It is becoming a bit of a nuisance unplugging drives all the time.

This is rather perplexing.

Regards
Philip

---

### Post by coffeecat on 2012-07-24
> **Philip Gray said:**
>  I have found that sometimes if I copy the documents from my usb stick to one of my windows partions and to my 12.04 installation, 12.04 will not let me modify them, I get an error message advising that  I need route privileges especially if I am trying to move the screenshots around.

This simply should not happen if you are mounting NTFS and FAT32 filesystems with Nautilus.

Except... you mention a USB stick. This would probably be formatted FAT32. You haven't installed the package usbmount by any chance, have you? If you have - uninstall it now. It is not designed for GUI systems and interferes with automounting by Nautilus and if you are relying on usbmount, that would certainly require root privileges.

The only other time I can think that you would get an error message saying that you need to be root after mounting a filesystem with Nautilus is if the filesystem is a Linux one.

@Morbius1, any other thoughts?

---

### Post by Morbius1 on 2012-07-24
> **coffeecat said:**
> @Morbius1, any other thoughts?
To be honest I'm still trying to figure out that last paragraph. It appears that he's unplugging physical hard drives on a running system in order to connect new ones. So he needs to unmount them to remove them and replace them. That's just a guess.

---

### Post by Philip Gray on 2012-08-12
Hi Coffeecat and Morbius1

Sorry for only responding now. I have been ill with flu and then bronchitis. I have not installed usbmount. My usb stick mounts automatically, in 12.04 and 10.04, when I insert it.

To clarify my comment about disconnecting hard drives. I have installed 10.04 and 12.04 on two different drives. My 10.04 is installed on my 512GB drive which also has Windows XP installed on it. My 12.04 is installed on my new 2TB drive which, currently, does not have anything else on it. My 1TB drive is readable and assessable to both 10.04 and 12.04. I do not have all three drives mounted and working at the same time.

I have a 450W power supply so I cannot run all three hard drives plus my two DVD writers at the same time. So I have to swop the one power cable between the two bootable hard drives. I only do this with my switched off. I do not do this while my PC is on. I am looking for a bigger power supply which should solve this.

Regards
Philip

---

