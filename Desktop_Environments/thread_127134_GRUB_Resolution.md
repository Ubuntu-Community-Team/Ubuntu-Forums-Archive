---
title: "GRUB Resolution"
date: 2006-02-08
forum: Desktop Environments
---

### Post by shawnzyoo on 2006-02-08
I recently bought a new 19inch Flat Panel
and I have fixed the resolution in ubuntu (1200X1024)
but Grub is still at the wrong resolution
i am not sure where i can change this
does anyone have any suggestions?
Thanks

---

### Post by ESPOiG on 2006-02-08
i always thought u culdnt change the grub reso... it is default at 640x480 and wen u make splash images for it u always make them 640x480

i sumhow think (may not be right) that maybe just maybe u cant change the reso of grub... cuz i have a 17" and my grub is still 640x480 it aint like it chnages automatically

it isnt really a techincal peice of software that i wuld imagine wuld incorporate a thing like reso

wat i thought anyway :P

---

### Post by frodon on 2006-02-08
This should work : [http://www.ubuntuforums.org/showpost.php?p=670508&postcount=2](http://www.ubuntuforums.org/showpost.php?p=670508&postcount=2)

---

### Post by shawnzyoo on 2006-02-09
so i tried that and when it boots ubuntu it changed the resolution
useful but not what i was trying to change
when computer first boots and i have my 
OS options listed
that is the menu i want to change the resolution of 
cause i can only see a little bit of my OS options 
thanks

---

### Post by rado_london on 2006-02-09
I was trying to find a solution for the same problem. BUt finally I realized that there isnt solution. The reason is simple- GRUB has been made to be small because it is located in the MBR (Even Windows has small resolution on boot).
Thats what I think:D

---

### Post by Brynster on 2006-02-09
To the best of my knowledge it cannot be done

Simply put its uses VGA as ther isn't a monitor out ther that cannot acheive basic VGA resolution. It uses VGA  because most video device support VGA without a driver. As posted above it has to fit into a tiny MBR sector on your HDD with simply doen't have enough space for a 30meg Nvidia driver or ATi driver.


But hey as ever I will be happily proved incorrect at any moment....

---

### Post by shawnzyoo on 2006-02-09
all interesting thanks for the info/thoughts
this is discouraging to hear though
since i can only see parts of the main grub screen
oh well
i assume there are other boot loaders out there
does anyone know if these other boot loaders can change the screen resolution?
thanks

---

### Post by rado_london on 2006-02-09
I only know LILO as good boot loader but it still supports up to 640x480

---

### Post by alfonz on 2006-02-09
[QUOTE=Brynster]To the best of my knowledge it cannot be done

Simply put its uses VGA as ther isn't a monitor out ther that cannot acheive basic VGA resolution. It uses VGA  because most video device support VGA without a driver. As posted above it has to fit into a tiny MBR sector on your HDD with simply doen't have enough space for a 30meg Nvidia driver or ATi driver.


But hey as ever I will be happily proved incorrect at any moment....[/QUOTE]

You got it ... ISO standard for VGA resolution is 640x480. When you first boot a system all instruction sets come from BIOS which load all standard resolutions etc etc such as the VGA standard for Video Display. So when BIOS tells the system to boot from the MBR it loads GRUB. Till this point Grub has nothing to do with changing resolutions therefore you get 640x480 when the OS choice screen starts. Anything after that is a different ball game.

If you want a higher resolution for Grub's OS menu then you need to hack your CMOS table in the BIOS....err good luck

If I am wrong, please feel free to correct me, anyone. ;)


Cheers!

---

