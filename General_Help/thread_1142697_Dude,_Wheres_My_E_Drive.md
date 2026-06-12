---
title: "Dude, Wheres My E Drive?"
date: 2009-04-29
forum: General Help
---

### Post by LazyLlama on 2009-04-29
Hey guys! I've got a small problem, which I know you can help me with. I'm fairly new with Ubuntu and I love it! You see, I installed my Ubuntu onto my E drive, whereas my C drive contains mostly windows stuff. I can very easilly access my C drive from the File Browser - but I also have stuff I want to use on my E drive - so where is it?
 
 I'd be grateful for anyone who could tell me - as basic as it is :D

Thanks very Much!
 -The Llama

---

### Post by FluffyElmo on 2009-04-29
I assume you want to access the data from Windows? You have to install a Windows driver for the Ubuntu filesystem to see the files. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by LazyLlama on 2009-04-29
Strange - I accessed my C drive well enough...
  Oh, well thank you! I'll install these drivers :D

---

### Post by elasto1mania on 2009-04-29
If you installed Ubuntu on e drive you formated e drive and the date is wiped out.

---

### Post by Grenage on 2009-04-29
How many physical disks do you have?
How are they partitioned?
Which partitions are being used for linux and windows installs?
Which partition is being used to store the data you want?

---

### Post by LazyLlama on 2009-04-29
Thanks for replying, but I'm fairly sure it didn't - I installed using Wubi and when I accessed my E drive (on windows) I found two folders, ubuntu and Program Files - so I know its not gone.

 Thanks anyway :P

---

### Post by jelle_ on 2009-04-29
ubuntu don't use drives, everything is part of /. so in your case the e-drive is /

---

### Post by max_power on 2009-04-29
LazyLlama gnu/linux doesnt use drive letters thats why you are confused.

your "E:" drive is actually the root (/) of the partition so if you want to go to E: you need to go to /

ex) in terminal type: ```
cd /
```

if you want to go to your desktop you type```
 cd /home/(your username here)/Desktop
```

---

### Post by LazyLlama on 2009-04-29
Thanks for all the replies! cd / doesn't seem to do anything :( (was it somthing I said?!)

  The E drive contains ubuntu in a folder called Ubuntu - but I want to get to a folder called "Program Files" - as I've said before.

I'm fairly sure Ubuntu thinks this Ubuntu folder is a drive. If this helps.

---

### Post by ChaiTan on 2009-04-29
If you have installed ubuntu in E drive using wubi, you can access the drive in ubuntu through /host
Open File Browser click on Filesystem and your E drive will be the directory named "host"

---

### Post by max_power on 2009-04-29
i dont understand what your trying to do. 

are you trying to access the Ubuntu file system from Ubuntu or from Windows?

---

### Post by LazyLlama on 2009-04-29
YES! Thank you very much! All my files are safe and secure - you saved my day!

---

