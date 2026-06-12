---
title: "wifi driver menace"
date: 2011-07-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the_executioner on 2011-07-23
hey everyone i am new to ubuntu and here is what the problem is

after installing natty besides win 7 on my m101z, the first few times the wifi driver just works fine is able to detect wifi networks and everything but stops later after a couple of reboots
i have a bcm4313 broadcom card, any help at all would be greatly appreciated folks especially as i've been trying to figure it out since 3 days without a break

---

### Post by the_executioner on 2011-07-23
awrigh ---------------------update-----------------------------------------
hopefully this helps some newbie and they dont have to go through the same level of frustration that i did

lil background on the driver and what happened in this case
                 it seems that the card BCM4313 runs like the wind on the driver called brcm80211, incidentally this driver and its subsidary modules (cfg80211 and mac80211) are included in the kernel of Natty, but wen things get complicated is that ther are various other sources which offer drivers for BCM43** cards, which after updating to my wifi had gone kaput. but it turned out that once i reinstalled natty the driver would stop detecting networks even if i din update the drivers, 

after a lil digging i found out that 
dmesg   
in the terminal returns one of these sentences
 brcm80211: module is from the staging directory, the quality is unknown, you have been warned.
so according to linux the module wasnt fully developed 
anyway i'll leave this here 

so what i did was this
 i knew that i knew that the first run after a reinstall everything (my wifi i mean) was working tip top, so i copied the results of these commands (during the first run) into a text file 
sudo lshw -c network                                % to see my hardware state 
lsmod                                                          % to check which modules are loaded
iwconfig                                                      % to check the state of network 

at the next reboot the drivers failed 

and when i checked the output of

sudo lshw -c network 

i found that the wlan card was disabled to enable it i ran this command

sudo ifconfig wlan0 up 

after this i checked iwconfig i found that sure enough the essid was not set
so i manually set the essid of the card to that of my wireless router using this commad

sudo iwconfig wlan0 essid <'essid val'>

and sure enough the connection was through 
 
for this solution u need to know the essid of the wireless router u'll be using
otherwise this solution doesnt work 
besides i gotta do this everytime i reboot 
but if anybody got a more permanent fix to this please contribute 
------------------------------------------------------------------
and to newbies dont giveup , thers light at the end of every tunnel 
linux might seem unfriendly at the begining wen things arent working out for u 
but after that it keeps on gettin better and better
and man natty is slick i love it

---

