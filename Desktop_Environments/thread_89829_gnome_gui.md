---
title: "gnome gui"
date: 2005-11-13
forum: Desktop Environments
---

### Post by balasatya on 2005-11-13
Hi,
 I have installed grub in my primary partition and reinstall win-2000 (BCZ I failed to install grub in my linux root). now I can log in to my user account.How can I activate my desktop? Should I need to install Gnome desktop?
I am new to linux and want to be free from windows. Please help me.
thank you.
 
    :smile:

---

### Post by foolsh on 2005-11-13
yes you need to install the "DESKTOP"

"startx" should start the gui but if the install is broken then try reinstalling it 
you will need to have installed the desktop  "by just hitting enter at the installations first screen"
or if you installed the "server" version then type "sudo apt-get install ubuntu-desktop"
and reboot

if you want dual boot windows and ubuntu you will need to install windows first then ubuntu
dividing your hard drive up in to seperate partitions will be part of the process
im assuming you have wiped your harddrive clean and are starting over from scratch
I give each operating system 10GB and leave the rest as fat32 partition so I can access it from both OS'es without read write permision troubles.
depending on how big "or small" your harddrive it is the is up to you but you will need atleast 2GB for windows and linux each.
during the windows installation when it asks where to install "again assuming your wiping your harddrive cleean" choose to delete all partitions and create a new partition atleast 2GB but i suggest about 10GB.
leave the rest of the disk blank for now
after windows finishes and reboots for the first time you can install ubuntu
now during the ubuntu instalation when it asks you where to install at
choose edit partition manually
then create a new partition 
type ext3
mount point /
atleast 2GB but again i would make it 10GB if i could 
then make another partion about 500MB 
type swap space
then make the final partition useing all the rest of the space 
type fat32
for the mount point you can enter manually and it will create a folder in the root directory linking to your fat32 partition "mount point /whateveryouwantittobe"

then when ubuntu ask if you want to install grub to the master boot record choose yes dont worry its safe unless your installing ubuntu to a second harddrive "i have not gotten this to work on a second harddrive"

then after its all said and done when you start your computer your should be given the choice to boot ubuntu or windows

---

### Post by balasatya on 2005-11-14
thanks. But i installed ubuntu on the second hard drive. ](*,)

---

