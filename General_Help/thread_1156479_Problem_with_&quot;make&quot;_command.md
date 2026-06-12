---
title: "Problem with &quot;make&quot; command?"
date: 2009-05-11
forum: General Help
---

### Post by ryanlhjess on 2009-05-11
[SIZE="5"][B]The Situation 
[/B][/SIZE]

I am trying to install Linux drivers for my ASUS WL-167 Wireless USB dongle. I downloaded these drivers from the support.asus.com
website.  I have been following the instructions as listed in the README file, however I have come to a hiccup in the process, and require some assistance.

[SIZE="5"]**The Problem**[/SIZE]

I am having trouble following the following instructions.

```
Build Instructions:  
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
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
```


As soon as I get to the second part of STEP 3

*   $make config         # config build linux os version*

I get the error

*make: command not found*

the same goes for the step that follows (STEP 4)

*4> $make all            # compile driver source code*

---

### Post by albinootje on 2009-05-11
> **ryanlhjess said:**
> 
make: command not found
Please do the following :
```

sudo apt-get install build-essential

```
And try again.

---

### Post by ryanlhjess on 2009-05-11
Thanks that worked

---

