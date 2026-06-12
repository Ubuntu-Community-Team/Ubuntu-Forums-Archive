---
title: "Weird problem loading GUI"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Dr_Freemanstein on 2006-08-26
A weird problem has developed with X on Ubuntu 6.06 (Dapper), since I last used it!  Now, when i enter my Username/Password at the login, the GUI starts loading as normal (brown spash loading Nautilus etc.) and even plays my startup sound, but then freezes upon displaying my desktop.  It varies the freeze point aswell, sometimes the mouse is immovable and no icons display, other times, all the icons display, and I can move my cursor for a few seconds.  After being frozen for about 30 seconds, it drops me back to the login screen.  Sometimes however, my monitor displays a message asking my if the display is within limits??

I have tried *sudo dpkg-reconfigure xserver-xorg*, and run through that withh all defaults again (which all worked before) but still it freezes!?

Anyone got any ideas why, and how to fix???

_System Specs:_
<_ Processor _>       AMD Athlon(tm) XP 2400+
<_ Mainboard _>       Gigabyte Technology Co., Ltd. GA-7VA-A
<_ Memory _>          768MB DDR-SDRAM
<_ Hard Disks _>       
1:  Maxtor 6Y080L0 (76GB) [Partitioned into 66GB (NTFS), 500MB (Swap), 10GB (ext3)
                    2:  ST340810A (37GB) [One partition of 37GB (FAT32)]
<_ Optical Drives _>  
1: ATAPI CDRW 52X32 (CD 52X Rd, 52X Wr)
                    2: PIONEER DVD-RW  DVR-110D (CD 40X Rd, 40X Wr) (DVD 5X Rd, 5X Wr)
<_ Video Adapter _>   NVIDIA GeForce FX 5200
<_ Sound Card _>      Creative SB Live! series
<_ Input Devices _>   
Keyboard: Standard 101/102-Key or Microsoft Natural PS/2 Keyboard 
                    Mouse:    PS/2 Compatible Mouse 
<_ Printer _>         EPSON Stylus Photo RX420 Series
                   
<_ Operating System(s) _> 
Windows System:   Microsoft Windows XP/2002 Home 5.01.2600 (Service Pack 2)    
                        Linux System:     Ubuntu 6.06 LTS (Dapper Drake)

---

### Post by mejy on 2006-08-26
I'm not sure if this will work, but I had a very similar problem a few days back.  Here's the fix I use (I have no idea why or how it worked).

At the GDM (login screen), change the login type to Failsafe Terminal.  When the terminal opens up, first type 'gnome-terminal'.  When this loads, type 'metacity' into it.  Open a new tab (File->New Tab), and type gnome-panel.  Open up another tab, and type 'nautilus'.  Now, on the menu at the top (which should have loaded by now), go to System->Prefernces->Themes.  Assuming nothing's crashed so far, just log out and log back into Gnome as you normally would.

Worked for me.

---

### Post by Dr_Freemanstein on 2006-08-26
Thanks....that seemed to work.....for now ;) 

Weird how it did that tho eh???

Will keep a note of your soloution for future ref

Thanks again

---

