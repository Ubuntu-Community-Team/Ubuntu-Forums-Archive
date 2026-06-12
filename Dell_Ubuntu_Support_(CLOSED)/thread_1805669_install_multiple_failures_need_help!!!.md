---
title: "install multiple failures need help!!!"
date: 2011-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kronos943 on 2011-07-16
i have been trying to load ubuntu 11.04 on my dell inspiorn 1545 but i came across a problem when i restarted. it gave me an error 

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _

and when i try to load windows i cant get the boot loader all i get is

"Error: unknown filesystem
grub rescue>"

i can load the cd but when i tried to find the partitions in the terminal i couldnt please help!!!!

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

