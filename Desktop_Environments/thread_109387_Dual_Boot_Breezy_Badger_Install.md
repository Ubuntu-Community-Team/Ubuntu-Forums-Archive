---
title: "Dual Boot Breezy Badger Install"
date: 2005-12-28
forum: Desktop Environments
---

### Post by ColdClone on 2005-12-28
Basic System Description:
Dell Inspiron 8000 Laptop (bought 01/2001)
PIII 800 Mhz
512MB RAM (Maxed)
60GB Seagate 5400 RPM internal IDE HDD
32MB ATI Mobility M4 Graphics Card w/ TV Out
1600 X 1200 UXGA 15.4" LCD
SONY 8X CD-RW Internal
Toshiba 8X DVD Modular Bay (removed)
3Com 10/100 & V.90 LAN Mini-PCI
Dual After Market Li-Ion Batteries
ESS Maestro 3i Sound Chipset w/ SPDIF Out
FoxConn Motherboard w/ Firewire 400
External Firewire Lacie 250GB HDD
External Firewire Lacie Double Layer DVD Burner.

Main Activities:
Gmail, Quick Multi-page Web Browsing
Digital Photo Touchups
Wordprocessor / Spreadsheet generation
Audio CD / DVD Cloning (Slysoft)
MS Streets and Trips map panning

One of my prime concerns is for my computer to be as responsive as possible when:
1. Starting Up
2. Starting apps
3. Using apps
3. Web browsing
4. Thumbnailing / opening / editing / writing jpg files

I intend to use Linux for everything I can as I have hopes for quicker reponse times in the above activities as well as better ease of use with the command line.
I know however, I will need windows for a few things in the near future (TurboTax).

Clearly, I need a dual boot system for now and I intend on:
1. Wiping the laptop by deleting all partitions
2. Creating a partition for Windows XP Pro

Questions
Q1: Do you think Breezy Badger is right for me?

Q2: Should I install Windows XP Pro on a NTFS (more features) or FAT32 file system (faster and linux write compliant)?

Q3: Can I use the same partition for a Windows Swap and a Linux Swap file?

Q4: What are optimal partitiaion sizes and file systems (ext3) for the partitions assuming I install fairly large full apps on the windows partitition like MSOffice 2003, Acrobat Writer, MS Streets and Trips, Photoshop CS2,  etc.. on my 60GB laptop disk.

Q5: What is the best linux guide to use to learn the console (shell) commands and linux in general? I don't want a reference, rather a walk through, tutorial-type, document.

I read a lot here and there with different suggestions.
Any help would be greatly appreciated !

---

### Post by icarius on 2005-12-28
I am a relatively new Linux user so I can't help you much on some of the technical aspects. However, I recently turned my machine into a dual booter and I am very happy with it. I didn't wipe my machine clean I just resized the windows NTFS partiiton with partition magic  to make it just big enough to run windows. I then created two new partitions, one for ubuntu (which I have come to love) and the other for a Fat32 partiton, which I use as my main data repository. In this way, I have a shared space for both of my os's. Mounting is farily simple 

as root in terminal (sudo -su)
gedit /etc/fstab
to the last line add /dev/hda$    /(location wher eyou want to mount, I did /home/icarius/Desktop) rw,user, uid=icarius 0 0
save and exit
as root 
mount /dev/hda$ ($=whatever partition number the drive is )

Hope that helps

---

### Post by meborc on 2005-12-28
read this... [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

it helped me to make my comp into dual boot and it is one of the best walk-throughs there is...

---

### Post by ColdClone on 2005-12-28
Thank you icarius. Do you think it is good to have a seperate partition for the swap file?

---

### Post by ColdClone on 2005-12-28
Thank you meborc. I will take a look at that walk through. The problem I had looking for manuals was that many of the linux guides were so old (talking about Red Hat 5.0 etc).

---

### Post by ColdClone on 2005-12-28
That is the best guide ever.
And it is up to date.
I will use it like a bible.
I will print it and do the dual boot install.

---

### Post by meborc on 2005-12-29
i tried to print it too, but it seems that the pictures are unprintable :D ... since your new ubuntu home is a protable one, i would suggest you run to your best friend (or simply to your workplace) and use another comp to read the manual as you go... so you could ask help as needed, if it should come to that while you are installing...

good luck :mrgreen:

---

### Post by Sef on 2005-12-29
Just use thepartitioner that comes with installlation disk.  It partitioned with no problems including shrinking my NTFS into a smaller partition.   Also I have read here that sometimes there is problems with partition magic when setting up to use linux.

---

### Post by ColdClone on 2006-01-03
Thank You again meborc. I was able to print the entire web page with images and all. It might be a setting in Firefox or dare I say it: IE. Some pictures are a toner drainer though as they are shell images (black background).

---

### Post by ColdClone on 2006-01-03
Thank you for letting me know about the possible problems with partition magic. Typically I like to do very clean installs (erasing all partitions and recreating it all). Keeps me from ever feeling like the quick fix was the reason for my computer running slow now :)

---

