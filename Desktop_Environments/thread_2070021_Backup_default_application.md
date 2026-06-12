---
title: "Backup default application"
date: 2012-10-11
forum: Desktop Environments
---

### Post by muzycales on 2012-10-11
I have a quick question about the "BackUp" application that comes with Ubuntu 12.04.

I managed to set up my computer the way I like it. Now, I'd like to create a backup of my file system partition. I've research a few backup options (such as fsarchiver, partimage), but if I'm not mistaken, in order to be able to use fsarchiver I have to run it from a live cd. Therefore, I was wondering if I can use the Backup program instead. Maybe I could select the "/" and take the files and save them to usb flash drive. Would that work? 
Thanks much.

---

### Post by jerrrys on 2012-10-11
Hi muzycales, welcome to the forums  :)

A mounted partition will have processes in use and will not give you a good clone.  So you are going to need someway to clone "/" while unmounted.

I use [clonezilla]("http://clonezilla.org/"), but there are [other ways]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=system+backup&as_qdr=all&sa=Google+Search&lang=en").

---

