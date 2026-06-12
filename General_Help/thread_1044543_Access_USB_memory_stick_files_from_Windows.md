---
title: "Access USB memory stick files from Windows"
date: 2009-01-19
forum: General Help
---

### Post by healthstatus on 2009-01-19
I have a software application that we have installed on a Bootable Ubuntu 8.10 USB memory stick, the application creates a data file that is saved to the memory stick, the user then wants to pull the memory stick from the laptop, insert into a windows machine (XP or Vista) and retrieve the data file.  What additional steps do I need to take for this to be possible?

thanks,
Greg

---

### Post by HermanAB on 2009-01-19
You need to install an Ext3 file system handler on MS Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Cheers,

Herman

---

### Post by healthstatus on 2009-01-19
That looks like a good option, I was hoping however that my clients wouldn't have to do anything to their windows computer to read the file.  Is there a way I can modify the Ubuntu USB key to create a partition that Ubuntu can write to and windows can read from?

---

