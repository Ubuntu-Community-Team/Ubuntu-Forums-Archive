---
title: "DELL LINUX Wireless!!!! please help!!"
date: 2010-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by msaied86 on 2010-05-28
Dear all!

i will organize my issue because i dont understand anything from the dissordinated posts i found and hence no solution i can found

-i have vostroo 1400 with dell wireless card (1395) and i have installed the linux Ubuntu 10.04 LTS "Lucid Lynx" - Release i386.

- all works except the wireless cad it seems that the linux are not detecting it

-i went to hardware device i founded 2 drive (1 sta and 1 broad) i try to activate them and no way , both gives me error

-i installed ndiswrraper package (.deb) and it i check with ndiswrapper l  and it gives me that device still disconnected

- i went to the [www.dell.com]("http://www.dell.com") to get the drive but it is in .exe sot it is not workong

-i tryied to install the windows driver file bcmw5.inf from the drive , it gives me installed but when i make check it gives me error with the file , but the same file works my wifi with windows.

- the las solution i tried to do is install the wine package (.deb) becauuse i am offline.
the installation runs and gives me (finished) but it seem no program installed .

i tried to install it with the command way sudo....., but it gives me error that the flex package is to old  and try the version 2.4.33 or higher.

-i got a higher version of flex (2.5.33) and it gives me the same error that the flex is old..



i am really so tried of this operating system but i believe that every problem have a solution, can anybody give me his experience about these problems?


thanks in advance,

---

### Post by rivali on 2010-05-29
I have the same laptop and the problem is  that to configure the wireless driver you must be connected to the Web and  you have not already, so  internet connection is by ethernet wire, wich connector  is in  the back, next to the battery and which automatically detects Ubuntu. 

Once connected go  to System - Administration - Hardware Drivers and check Broadcom B43  Wireless driver. Wait until Ubuntu download the appropriate driver from the web  and install it. Restart the laptop and  voila....  :popcorn:

Excuse  my English. I speak Spanish and  translated this response through the Google translator, but I hope you  understand :)

---

### Post by ugm6hr on 2010-05-29
I suspect this is a very easy solution (as given above) - but it is worthwhile confirming your wifi chipset with:

```
lshw -class network
```

Also... Have a look at the wifi help link below and post details in full here.

The main problem is now going to be undoing the changes you have made with ndiswrapper etc, which is likely to interefere with the actual driver needed.

---

