---
title: "ubuntu wont restart properly after install! please help."
date: 2014-07-13
forum: Desktop Environments
---

### Post by andrew134 on 2014-07-13
hi, I installed ubuntu from bootable usb and the install process works and finishes, i get to the point to where it says in order to start using ubuntu  I must restart my computer. then i click restart and boom, black  screen no start up no grub menu, nothing. now I did think it might be the usb, so I donwloaded it again on a different usb (both i tried were 4gb, more than enough for ubuntu, and right format). i also tried to get boot repair while in "try ubuntu" mode but couldnt because it said it couldnt find the file or something. so please help me, my computer is wiped it has no os, the windows it had is wiped and so was the back up to restore it. how can i fix this, and i dont have another pc to re download ubuntu again, when i did i had to go to a friends house, but their away now. and i dont think its the usb or download, i think its the graphics settings on the laptop perhaps??? im using ubuntu lts.

btw ive installed ubuntu on this laptop before and had no problems at all, now i cant. ALSO i'm a big noob with computer things, but If you guys have a solution, i'm good with following well instructed directions. Please please help!!!! 

also im new too the forums, I dont know if i posted it in the right sections i even had to look up on how to start a new forum :/. and yes i did look if there was a solution to my problem already but didnt find any that worked, but if indeed there is and i missed, do link in to this thread.

---

### Post by andrew134 on 2014-07-13
bump

---

### Post by jp734 on 2014-07-13
It will be helpful for anyone who's going to try to help you to know the info about your laptop. Brand, Model, graphics card, etc....

Also, can you still boot the laptop with the live USB? What version of ubuntu?

---

### Post by andrew134 on 2014-07-13
ubuntu 12.04 lts its an acer aspire 5517, it has an amd graphics card and yes i can still boot with live usb, only way i can acess the forums right now

---

### Post by jp734 on 2014-07-13
I would think this is graphics issue. PC has a HD3200. Check your **/var/log/Xorg.0.log** on your hard drive and look for some clue what's going on with the graphic card driver. You can use PCManFM file manager

---

### Post by yancek on 2014-07-13
> my computer is wiped it has no os, the windows it had is wiped and so was the back up to restore it. 

I assume that was by choice as there certainly was an option to install to separate partitions without overwriting windows.  Have you verified this for example by running:  sudo fdisk -l(Lower case Letter L in the command) from the flash drive?  This will show if your windows partitions still exist.

In order to see the grub menu, try booting the installed system and immediately after the BIOS screen, hold down the shift key to see if you get a menu.  The default with only one operating system is NOT to show the menu.  When you see the menu, make sure the Ubuntu entry is highlighted and hit the 'e' key.  You should see the menuentry for Ubuntu.  There will be a line beginning with the word linux, use the arrow key on your keyboard to go to the end of the line, make sure there is a space after the last word and then type nomodeset, all lower case letters.  You should see options at the bottom telling you which key to press to continue booting.

---

### Post by andrew134 on 2014-07-13
yes, im positive the windows back up is comepletely wiped, no it wasnt by choice, i accidently deleted the partition holding the widnows back up. but yes I did do what you said to check if i still had it, but I dont. 
 
as for the second part, that didnt help. so far ive been trying to reinstall and delete again, i did boot repair (now the process did work) what happening now is that the ubuntu grub shows up, i select ubuntu, it shows ubuntu logo... few seconds later i get a white screen. computer restarts. 

im now wondering if theres a way that if in live mode i can download a different os and put it on another bootable usb? because when i try to download something it says ran out of memory, im guessing because its trying to download it directly to the usb

---

### Post by jp734 on 2014-07-14
You can definitely download another OS using live USB and save it on your hard drive so you don't run out of memory.

Have you looked at your log files? I always look at these as it will help you determine what the issue is and how to solve it.

---

