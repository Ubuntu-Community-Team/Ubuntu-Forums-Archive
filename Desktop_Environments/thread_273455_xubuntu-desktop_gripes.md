---
title: "xubuntu-desktop gripes"
date: 2006-10-08
forum: Desktop Environments
---

### Post by mahy on 2006-10-08
Hi folks, 

just today i installed Xfce (sudo apt-get install xubuntu-desktop) on 
my Kubuntu Dapper machine, Fujitsu-Siemens Amilo Pro V2045 laptop. 
The results are lamentable. It starts ok, and i can start all foreign 
(non-xfce) apps, but only some xfce apps. Thunar, Terminal, Mousepad 
etc, they all work fine. On the other hand, Settings Manager and 
everything related to it doesn't start at all and displays this on 
stdout: 

```

janci@darkstar:~$ X Error: BadDevice, invalid or uninitialized input 
device 168 
  Major opcode:  148 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 168 
  Major opcode:  148 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 

```

(Actually when i try to start settings manager for the first time, Orage is started instead.)

xfce4-menueditor displays the same errors, but it does start in the 
end. Moreover, the small window that appears when i click logout button 
looks seriously crippled. Logout itself doesn't work either, it ends up 
in a computer freeze. N.B. My graphics card is ATI Mobility Radeon 
X300, using the proprietary drivers from Ubuntu's repositories 
(xorg-driver-fglrx). It works flawlessly (incl. 3D acceleration, of 
course) in KDE; and it has also worked in Xubuntu Breezy. I even tried to comment out the Wacom devices in my xorg.conf and did a dpkg-reconfigure xserver-xorg, but nothing helped...

I found nothing by googling, hope i'll be more fortunate here. TIA for 
your help 

Mahy

---

