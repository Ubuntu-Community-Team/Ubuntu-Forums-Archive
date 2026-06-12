---
title: "Help"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ScottLH on 2005-12-01
I have a question, I am trying to acces the cdrom through the terminal

I think it is 
cd /
ls
cd rom

but this is not working can someone give me the commands to do this. Thank you.

---

### Post by RAOF on 2005-12-01
If your cdrom is mounted, you'll probably find it under /media/cdrom, so it would be ```
ls /media/cdrom
``` and ```
cd /media/cdrom
```etc.

---

### Post by cgjones on 2005-12-01
If you type mount in a terminal, it will show all currently mounted filesystems. Look for /media/cdrom. Also, if you type ls -l /dev/cdrom, you will see what device cdrom is symlinked to. Helps sort things out if you have more then one cdrom.

---

### Post by ScottLH on 2005-12-01
OK I did that and it showed me what was on the cd rom. What I am trying to do is install the Nvidia Nforce drivers from a .run file on the cd in the drive. I need to do this with root I can get to root but I don't know the the coomands to acces the cd to install the drivers.

---

### Post by RAOF on 2005-12-01
Typically, the commands you would need to run (if the nforce drivers are in the root directory of the CD) are:
```
cd /media/cdrom
sudo ./NVIDIA_nforce_driver_file_name.run.bin

```
Where NVIDIA_nforce_driver_file_name.run.bin is obviously replaced with the actual name of the file.

---

