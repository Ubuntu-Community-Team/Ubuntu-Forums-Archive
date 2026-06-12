---
title: "Can someone Please repackage this tar.gz file for me?"
date: 2006-10-31
forum: Desktop Environments
---

### Post by trojanlinux on 2006-10-31
i have been trying for hours, can someone please repackage this for me into a .deb .  i would really appreciate it!

[http://www.samsung.com/support/productsupport/download/FileView.aspx?cttfileid=1090950&type=Printer+and+Multifunction&typecode=&subtype=Color+Laser+Printers&subtypecode=&cmssubtypecode=&model=CLP-300&filetype=DR&language=&LSSI=/include/SSI/us_left/LMenu_PrinterandMultifunction_ColorLaserPrinters.sec&RSSI=/include/SSI/us_right/RMenu_PrinterandMultifunction.sec](http://www.samsung.com/support/productsupport/download/FileView.aspx?cttfileid=1090950&type=Printer+and+Multifunction&typecode=&subtype=Color+Laser+Printers&subtypecode=&cmssubtypecode=&model=CLP-300&filetype=DR&language=&LSSI=/include/SSI/us_left/LMenu_PrinterandMultifunction_ColorLaserPrinters.sec&RSSI=/include/SSI/us_right/RMenu_PrinterandMultifunction.sec)

---

### Post by firetux on 2006-10-31
There is nothing to package about that tar.gz, its just an ordinary archive.
Which step goes wrong?

---

### Post by trojanlinux on 2006-10-31
x@x-laptop:~$ '/home/x/Desktop/image' ./configure
bash: /home/x/Desktop/image: is a directory
x@x-laptop:~$ cd '/home/x/Desktop/image' 
x@x-laptop:~/Desktop/image$ make
make: *** No targets specified and no makefile found.  Stop.
x@x-laptop:~/Desktop/image$

---

### Post by daveisadork on 2006-10-31
> **trojanlinux said:**
> x@x-laptop:~$ '/home/x/Desktop/image' ./configure
bash: /home/x/Desktop/image: is a directory
x@x-laptop:~$ cd '/home/x/Desktop/image' 
x@x-laptop:~/Desktop/image$ make
make: *** No targets specified and no makefile found.  Stop.
x@x-laptop:~/Desktop/image$

I'm guessing you didn't actually take the time to read the directions on the page to which you linked.

> 3. Download and extract the driver
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]

4. The driver will be extracted as 'image' folder in current path.

5. Execute installation program.
[root@localhost root]#./image/setup.sh

6. When the welcome screen appears, click 'Next' and proceed installation.


---

### Post by aysiu on 2006-10-31
The instructions on the Samsung website don't say anything about *./configure* or *make*.

> 1. Make sure that you connect your machine to your computer.
Turn both the computer and the machine on.

2. When the Administrator Login window appears, type in root in the Login field
and enter the system password.

3. Download and extract the driver
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]

4. The driver will be extracted as 'image' folder in current path.
[b]
5. Execute installation program.
[root@localhost root]#./image/setup.sh[/b]

6. When the welcome screen appears, click 'Next' and proceed installation. 

---

### Post by trojanlinux on 2006-10-31
oh ok i diddnt think those instructions were for debian. the printer will be here tomommrow. so all i do is follow those instructions? I am worried about #2

2. When the Administrator Login window appears, type in root in the Login field
and enter the system password. 

where will the admin window "appear" from?

---

### Post by aysiu on 2006-10-31
Instead of this: ```
x@x-laptop:~$ '/home/x/Desktop/image' **./configure**
``` Do this: ```
x@x-laptop:~$ '/home/x/Desktop/image' **sudo ./setup.sh**
``` For more info, read this:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by trojanlinux on 2006-10-31
x@x-laptop:~/Desktop/image$ '/home/x/Desktop/image' sudo ./setup.sh
bash: /home/x/Desktop/image: is a directory

---

### Post by TheMono on 2006-10-31
As two seperate commands, first do "cd /home/x/Desktop/image"
Then do "sudo ./setup.sh"

Obviously without my speech marks...

---

### Post by aysiu on 2006-10-31
Sorry, I thought you were already in that directory. ```
cd ~/Desktop/image
sudo ./setup.sh
```

---

### Post by trojanlinux on 2006-10-31
x@x-laptop:~$ cd /home/x/Desktop/image
x@x-laptop:~/Desktop/image$ sudo ./setup.sh
/home/x/.setup7616: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by trojanlinux on 2006-11-02
i got the printer. i installed the driver through the add printer, but every time i try to print it stops the job.help please

---

### Post by trojanlinux on 2006-11-02
bump

---

### Post by trojanlinux on 2006-11-02
anyone?

---

