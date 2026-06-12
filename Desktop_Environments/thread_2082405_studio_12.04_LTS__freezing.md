---
title: "studio 12.04 LTS  freezing"
date: 2012-11-09
forum: Desktop Environments
---

### Post by Flaggmann on 2012-11-09
Is there anyone aware of any identified problems with ubuntu studio 12.04 LTS freezing randomly on mouse relocation moves such that one is not even able to CTRL-ALT-F3 to login to a command line console to do a sudo init 6 to force an orderly restart. It requires a full hard PWR DWN to clear. It has happened on two separate boxes and continues to. One box has ASUS UEFI with16 GB RAM the other slightly older ASUS MB (still has PCIe capability) but with only 4GB RAM.  

Initially thought installing and running Apache2, PHP5, andf mysql was reason, but uninstalling them did not cure the problem.

Fortunately have not had any video edit projects or databse projects open at the time the failures occurred so haven't lost any serious data as result yet.

Thanks for any help.


Further info; no indications of anything in /var/logs  but I can duplicate the problem by loading GIMP and opening a jpeg to edit, then zoom to 200 or 400% or higher a doing a scroll right or left; it begins the horiz scoll then freezes.  It does so reliably almost every time using gimp. Other programs it is less predictable but always related to horizontal movements of open windows apparently. other boxes with 32 bit ubuntustudio 12.04 LTS work fine just the 64 bit version exibits the problem. I have resource monitor on a panel and cpu and memory not topping out at all

First started to show for me around the time mozilla FF went to vers 13.0 update and has existed ever since. Three other older boxes have same vers studio installed but 32 bit and do not exibit the freezing seen on this 64 bit version.

---

### Post by ibjsb4 on 2012-11-09
Something to try.

Open a terminal and enter:

top

This will allow you to monitor ram/cpu just to see if it being eaten up by a process.

---

### Post by Flaggmann on 2012-11-10
> **ibjsb4 said:**
> Something to try.

Open a terminal and enter:

top

This will allow you to monitor ram/cpu just to see if it being eaten up by a process.

Tried it as suggested but nothing showed out of ordinary. Xorg was top of list resources not high, it just froze as well No processing whatsoever allowed; unable to CTRL-ALT-Fx to sudo init 6 and force orderly shutdown same in both machines and GIMP horiz scroll will cause fail every time

---

### Post by ibjsb4 on 2012-11-10
I understand that this is happening on two 64 bit boxes, but I still wonder if there may be a better video driver for you to be using.

---

### Post by Flaggmann on 2012-11-10
> **ibjsb4 said:**
> I understand that this is happening on two 64 bit boxes, but I still wonder if there may be a better video driver for you to be using.
Both are ASUS MB's with genuine intel sets. 

1st using Intel Corporation Ivy Bridge Graphics Controller (rev 09) onboard (P8Z77-V MB  16GB RAM)

2nd using ATI Radeon x600 add on vid adapter (P5QL Pro MB 2GB RAM)

Was a clean install of 12.04LTS on P8Z77-V machine, then cloned HD and installed same base updated install
in P5QL Pro box and let it auto config from there.

If it was only the one with the ATI vid card acting up I could maybe see an OEM ATI driver problem; since
two different boxes, diff MB's and vid adapters hard to fathom vid drivers although not impossible.

was leaning towards a common X-org lib file somewhere that is common to all windows especially with scrolling; maybe
a glitch in an update somewhere as the 64 bit boxes initially were OK but there have been a lot of updates of late, which
is why I wondered if anyone was aware of anything like this.

---

### Post by ibjsb4 on 2012-11-10
Yep, that kills the driver idea.  Ill do some more looking around, but out of ideas for the moment.

---

### Post by ibjsb4 on 2012-11-10
The kernel or xorg?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=studio+12.04+freezing&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=studio+12.04+freezing&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Flaggmann on 2012-11-12
> **ibjsb4 said:**
> The kernel or xorg?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=studio+12.04+freezing&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=studio+12.04+freezing&as_qdr=all&sa=Google+Search&lang=en")


Thanks for the tip and link; it appears much more common than I thought and much wider problem than just a driver somewhere it wud appear. compiz or kernel maybe . 

I will try the CTRL-ALT-F1 temp workaround given in the link text u gave me and see if I can add any new log info here. 

Oddly enough back in early 11  vers series I often thought there seems to be a lot of code effort in the appearance facade bells and whistles and not as much emphasis on the bllod & guts behind the scenes that need to work flawlessly to make the facade a success; kind of like politicians lol


UPDATE  Unable to CTRL-ALT-F1 access any error info just frozen solid even to that access as well

I am able to log onto both 64 bit machines using ssh -a -X userID@hostname  and run both GIMP and firefox  and am unable to cause either system to duplicate freeze using same horiz mouse movements. For what this might be worth to anybody assigned to look into the problem.

UPDATE Nov 17,2012 1546 utc   discovered only happened to pc's installed from studio 12.04 64 bit ISO burnt to dvd; ONLINE UPGRADES were fine. SOLVED for me wiped HD's and went to different 64 bit distro ISO DVD I have that works properly. Data cap costs too high to download a new copy of 12.04-64 especially after replacing a lot of hardware becuz the freezing looked like h/w at first. Better luck to others with the same problem

---

