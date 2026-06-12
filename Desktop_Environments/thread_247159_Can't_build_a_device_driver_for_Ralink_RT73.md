---
title: "Can't build a device driver for Ralink RT73"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Woozey on 2006-08-30
Hi.
I have Ubuntu 6.06 on my laptop. And i'm tring to get work USB W-Lan adapter DWL-G122 ver.C1
So I've downloaded Ralink RT73 driver from Ralink Website.
Follow the README instructions:
"Build Instructions:  
====================
1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware
 
6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up"
But i've got an error at point 2 after "make config" comand
"make: ***No rule to make target config'. Stop."
Please tell me, what should I do with that.

---

### Post by Woozey on 2006-09-01
Please, somebody

---

### Post by morbid88 on 2006-09-09
Hi.
If you're not using kernel version 2.4 then there's no need to do make config.

If you're using a new version of linux, you're likely running the 2.6 kernel. in which case just go straight to the next stpe, and run make.



BTW, there's some problems with the Ralink RT73 drivers, they seem to freeze up the system in some cases. I still haven't found someone to help me with that, but if that happens to you just come back to the forums and look it up.

JB.

---

