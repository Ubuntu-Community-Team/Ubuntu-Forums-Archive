---
title: "Operating System Not Found"
date: 2009-03-20
forum: General Help
---

### Post by mylifedrive on 2009-03-20
I have been running Ubuntu 7.04 off a 16 GB Transcend Flash drive for about a month now. I have some important documents on it, and I don't want to lose them.

I use a Toshiba Satellite Laptop.

Recently I have noticed that when I go to the computer after being away for an hour or so, there is just a black screen and I have to restart the computer, or all the Icons turn into little pixelly note images and I have to do the same. Sometimes blank error messages would pop up, and then also I would have to restart.

Well this time, When I restarted, It wouldn't boot up. I get the normal Boot window, and a black screen, (With some of my technical info at top) and then these messages:

PXE-E61: Media test failure, check cable
PXE-MOF Exiting PXE ROM
Operating system not found


I get the same thing every time. Please help!

---

### Post by fieroboom on 2009-03-20
> **mylifedrive said:**
> I have been running Ubuntu 7.04 off a 16 GB Transcend Flash drive for about a month now. I have some important documents on it, and I don't want to lose them.

I use a Toshiba Satellite Laptop.

Recently I have noticed that when I go to the computer after being away for an hour or so, there is just a black screen and I have to restart the computer, or all the Icons turn into little pixelly note images and I have to do the same. Sometimes blank error messages would pop up, and then also I would have to restart.

Well this time, When I restarted, It wouldn't boot up. I get the normal Boot window, and a black screen, (With some of my technical info at top) and then these messages:

PXE-E61: Media test failure, check cable
PXE-MOF Exiting PXE ROM
Operating system not found


I get the same thing every time. Please help!

This thread would be better suited in the [Hardware & Laptops Forum](http://ubuntuforums.org/forumdisplay.php?f=332).
How is your flash drive connected?
:D
-Paul

---

### Post by prshah on 2009-03-20
> **mylifedrive said:**
> 
PXE-E61: Media test failure, check cable
PXE-MOF Exiting PXE ROM
Operating system not found

The PXE (Portable eXecution Environment) messages are normal; they are for booting off LAN, and that most likely does not apply to you.

Clearly, the flash disk / drive / stick is not seen at all. Have you tried unplugging and replugging it?

If it's a stick, can you check it in another computer? Is it readable?

---

### Post by mylifedrive on 2009-03-20
> **fieroboom said:**
> This thread would be better suited in the [Hardware & Laptops Forum](http://ubuntuforums.org/forumdisplay.php?f=332).
How is your flash drive connected?
:D
-Paul

USB. Directly plugged into a port of the laptop


> **prshah said:**
> The PXE (Portable eXecution Environment) messages are normal; they are for booting off LAN, and that most likely does not apply to you.

Clearly, the flash disk / drive / stick is not seen at all. Have you tried unplugging and replugging it?

If it's a stick, can you check it in another computer? Is it readable?

Plugged into Vista, it recognizes it, but asks to reformat. Plugged into the same laptop when running ubuntu off another flash drive, it acts like it doesn't exist.

---

### Post by mylifedrive on 2009-03-20
If there is a way to rescue my documents on the desktop of the drive, I would be grateful. 

Also, when I have the drive plugged in, It does show up in the BIOS options of the laptop.

---

### Post by prshah on 2009-03-21
> **mylifedrive said:**
> 
Plugged into Vista, it recognizes it, but asks to reformat. Plugged into the same laptop when running ubuntu off another flash drive, it acts like it doesn't exist.

Can you:

a) plug it in, then open the terminal (Applications-Accessories-Terminal) and post the output of ```
dmesg | tail
```

b) Install [ext2/3 IFS drivers]("www.fs-driver.org/") in Windows (which will allow you access to linux partitions in Windows; be sure to enable "read-only" mode) and then try plugging in the usb drive to check if the files are accessible?

---

### Post by mylifedrive on 2009-03-21
> **prshah said:**
> Can you:

a) plug it in, then open the terminal (Applications-Accessories-Terminal) and post the output of ```
dmesg | tail
```

[   63.996000] Bluetooth: L2CAP ver 2.8
[   63.996000] Bluetooth: L2CAP socket layer initialized
[   64.144000] Bluetooth: RFCOMM socket layer initialized
[   64.144000] Bluetooth: RFCOMM TTY layer initialized
[   64.144000] Bluetooth: RFCOMM ver 1.8
[  114.016000] NET: Registered protocol family 10
[  114.016000] lo: Disabled Privacy Extensions
[  114.016000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  124.588000] ath0: no IPv6 routers present
[  177.680000] ath0: no IPv6 routers present
joshua@joshua-laptop:~$ 


b) Install [ext2/3 IFS drivers]("www.fs-driver.org/") in Windows (which will allow you access to linux partitions in Windows; be sure to enable "read-only" mode) and then try plugging in the usb drive to check if the files are accessible?

Still asks to reformat.

---

### Post by linuxisevolution on 2009-03-21
Boot an Ubuntu livecd and run fsck on each of the flash drive partitions, like this:

sudo fsck /dev/sdc1


replace the sdc1 part with the dev of your flash drive, find it by typing:

sudo fdisk -l

In terminal.


That should repair the flash drive. Next you will need to fix the boot loader.


type sudo grub in terminal

type find /boot/grub/stage1

it will output a number

type root (XXX,X)

Replace the x's with what the find command said.

type setup (hdX)

remove the second part of what the find command said and put it in the (hd0) format, replacing X with 0 or whatever number find said.

Good luck :)

---

### Post by mylifedrive on 2009-03-21
> **linuxisevolution said:**
> Boot an Ubuntu livecd and run fsck on each of the flash drive partitions, like this:

sudo fsck /dev/sdc1


replace the sdc1 part with the dev of your flash drive, find it by typing:

sudo fdisk -l

In terminal.


That should repair the flash drive. Next you will need to fix the boot loader.


type sudo grub in terminal

type find /boot/grub/stage1

it will output a number

type root (XXX,X)

Replace the x's with what the find command said.

type setup (hdX)

remove the second part of what the find command said and put it in the (hd0) format, replacing X with 0 or whatever number find said.

Good luck :)

sudo fdisk -l gives me this:

```
Disk /dev/sda: 16.0 GB, 16064184320 bytes
64 heads, 32 sectors/track, 15320 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xffffffff

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

```

---

### Post by prshah on 2009-03-21
> **mylifedrive said:**
> 
Disk /dev/sda doesn't contain a valid partition table
[/CODE]

Ouch! 

Boot off your other flash disk into Ubuntu; then download and install testdisk (it's in the repos); then use that to check your drive. testdisk comes with another program called photorec; that can be used to recover your files.

---

### Post by mylifedrive on 2009-03-21
Could you tell me what to do in testdisk?

---

### Post by mylifedrive on 2009-03-21
What information do you want me to give you?

---

### Post by mylifedrive on 2009-03-22
bump? :KS

---

### Post by mylifedrive on 2009-03-25
BuMp :(

---

### Post by mylifedrive on 2009-03-26
Bump. $5 By PayPal to whoever can get my flash drive operating again. If this is not allowed, please just say so, don't lock the topic. I just really need help.

---

### Post by Fludge on 2009-03-26
I've never used this program but i'll try to help (for free, of course ;) )

First open terminal and run ```
sudo testdisk
```
If it says your terminal window is too small, resize it (mine was 24 lines, the program requires 25)
Select [Create]
Select your flash drive and then [proceed]
Select [Intel ] (I think this is ok for most people)
and then [Analyse ]. It lists all your partitions on that disk.
If it doesn't find your partitions, try [Quick search], it hopefully finds your broken partition.  
If not, press enter and select [Deeper Search] . This seems to take very long (I'm testing this program now), but hopefully earlier steps get your problem fixed. The program may also give you some error messages about your disk.
Post any info which the program gives, and hope someone who really knows this program comes to your aid :P

---

### Post by mylifedrive on 2009-03-27
Thanks for helping.

**After analyze:**

```
Disk /dev/sdb - 16 GB / 14 GiB - CHS 15320 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors


Partition sector doesn't have the endmark 0xAA55

```

**After Quick Search:**

```
Disk /dev/sdb - 16 GB / 14 GiB - CHS 15320 64 32
     Partition               Start        End    Size in sectors










Structure: Ok.

```

**After Deeper Search:**
```
Disk /dev/sdb - 16 GB / 14 GiB - CHS 15320 64 32
     Partition               Start        End    Size in sectors













Structure: Ok.

```

Augh! My partitions just vanished!

---

### Post by Fludge on 2009-03-27
So it doesn't find your partitions?
Sounds bad, but you can try another program which comes with testdisk, write ```
sudo photorec
```
in terminal (again you may need to resize your terminal)
Select your flash drive and [proceed], then choose [Intel ]

I think you'll now get option to search "no partition"
Select the "no partition" line, then [search ] (search whole disk instead of partitions if you get that option)
Now the program asks about filesystem, choose [other ] unless you know that you had ext2/3 on your flashdrive.
Then just choose which directory you want the files to be placed (defaults to /home/<username>, the program creates a directory "recup_dir.1" there)
After you've selected folder, press Y, and the program starts to search files.
Now just wait until the program finishes, it shows you statistics about files found while it's running. You can also check the folder "recup_dir.1" while it's still running.

Hopefully this program gets your files out, at leasts it finds my files which I've deleted a couple months ago :P

---

### Post by mylifedrive on 2009-03-27
> **Fludge said:**
> So it doesn't find your partitions?
Sounds bad, but you can try another program which comes with testdisk, write ```
sudo photorec
```
in terminal (again you may need to resize your terminal)
Select your flash drive and [proceed], then choose [Intel ]

I think you'll now get option to search "no partition"
Select the "no partition" line, then [search ] (search whole disk instead of partitions if you get that option)
Now the program asks about filesystem, choose [other ] unless you know that you had ext2/3 on your flashdrive.
Then just choose which directory you want the files to be placed (defaults to /home/<username>, the program creates a directory "recup_dir.1" there)
After you've selected folder, press Y, and the program starts to search files.
Now just wait until the program finishes, it shows you statistics about files found while it's running. You can also check the folder "recup_dir.1" while it's still running.

Hopefully this program gets your files out, at leasts it finds my files which I've deleted a couple months ago :P

It did get out some files, but I don't have a hard drive, so I'm putting them on a 4 GB flash drive. However, The files don't all fit, so...

But this has promise, is there any chance I could restore my whole install?

---

### Post by Fludge on 2009-03-27
I don't think that's possible since your partition is badly broken.
Of course you can try *fsck*, but I'd strongly recommend backing up all your files before doing that since it may make your files completely unrecoverable.
Could you try dumping your recovered data on your laptop's hard drive? It shouldn't matter that it's ntfs-formatted, Ubuntu live cds are able to handle them.

---

### Post by mylifedrive on 2009-03-27
> **Fludge said:**
> I don't think that's possible since your partition is badly broken.
Of course you can try *fsck*, but I'd strongly recommend backing up all your files before doing that since it may make your files completely unrecoverable.
Could you try dumping your recovered data on your laptop's hard drive? It shouldn't matter that it's ntfs-formatted, Ubuntu live cds are able to handle them.

Thats the prob- I don't have a hard drive. That's why I have been doing it this way. I ended up with over 40,000 useless text files and temporary JPG's- So if the fsck thing does not risk making my drive completely unusable (like, can't be reformatted) I would try it out.

---

### Post by Fludge on 2009-03-27
Did you try opening any of the files? It seems photorec can't restore your filenames, so check the content of the files before giving up.
You can also choose which filetypes you want photorec to find. To do this, choose in partition selecting screen [File opt], and toggle using right and left keys which filetypes you want to find.

About fsck, it won't make your disk unformattable. It does roughly same as ScanDisk or chkdsk on Windows, it tries to fix the filesystem. The chance to get your filesystem fixed is a very small though because it's so badly broken.

---

### Post by mylifedrive on 2009-03-27
> **Fludge said:**
> Did you try opening any of the files? It seems photorec can't restore your filenames, so check the content of the files before giving up.
You can also choose which filetypes you want photorec to find. To do this, choose in partition selecting screen [File opt], and toggle using right and left keys which filetypes you want to find.

About fsck, it won't make your disk unformattable. It does roughly same as ScanDisk or chkdsk on Windows, it tries to fix the filesystem. The chance to get your filesystem fixed is a very small though because it's so badly broken.

There are just too many. And I didn't even get half of them restored before I ran out of space. It didn't stop with recup_dir.01- every 500 files it went to a new directory all the way up to recup_dir.66

---

### Post by Fludge on 2009-03-27
Yeah but did the files you checked contain just random data or data which you wanted?
If you're sure you don't need text files, set photorec not to search them.

---

### Post by mylifedrive on 2009-03-27
> **Fludge said:**
> Yeah but did the files you checked contain just random data or data which you wanted?
If you're sure you don't need text files, set photorec not to search them.

random data. I suppose maybe twenty of them were what I wanted, but I'm not going to try to sift through everything. I am setting it to search excluding txt now. We'll see what I get.

---

### Post by mylifedrive on 2009-03-28
> **mylifedrive said:**
> random data. I suppose maybe twenty of them were what I wanted, but I'm not going to try to sift through everything. I am setting it to search excluding txt now. We'll see what I get.

I didn't end up with anything good, so I'm willing to take the "next step" ;)

---

### Post by mylifedrive on 2009-03-31
):P Bump ):P

---

### Post by mylifedrive on 2009-04-02
BUMP :guitar:

---

### Post by mylifedrive on 2009-04-04
*** bump ***

---

### Post by mylifedrive on 2009-04-14
*** BuMp ***

:guitar:

---

