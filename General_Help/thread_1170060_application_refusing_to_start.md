---
title: "application refusing to start"
date: 2009-05-25
forum: General Help
---

### Post by chippanfat on 2009-05-25
[SIZE=2]Hi all. I'm very inexperienced with linux, and i've recently installed xubuntu on a spare computer to use as an ftp server. 

The software that had been using was installed through the terminal:
sudo apt-get install [/SIZE][SIZE=2]proftpd gproftpd
and in the application's menu it was called gadmin ftp 

but I couldn't remove a directory for user, So what I did made the application close, and when I go to re-start the app it refuses.


I tried using the purge command to uninstall it, and i've also tried removing the app in synaptic and searching for all the individual files and removing them. I can uninstall it the application but theres all these other files left, so when i go into the folders to remove them manualy, the delete button dosent work and i cant "right click and move to trash"

I'm not to hot with the command line. i though by typing sudo apt-get install proftpd gproftpd it might re-install everything but it dosent

Is there anything I can do to compleatly remove it? or reinstall everything to the default settings


Cheers. 
[/SIZE]

---

### Post by geraldvillorente on 2009-05-25
In commandline just type this command...
```

sudo rm -rf <dir_to_delete>

```

PS. Be careful of using that command as it may wipe out your entire docs and directory. Be specific to the directory that you want to delete to.

---

### Post by chippanfat on 2009-05-25
> **geraldvillorente said:**
> In commandline just type this command...
```

sudo rm -rf <dir_to_delete>

```PS. Be careful of using that command as it may wipe out your entire docs and directory. Be specific to the directory that you want to delete to.


in the synaptic manager, i clicked on properties to find out where all the files for app were, and there basicaly scatterd around the place.

So where would i find the primary folder? if there is one of course.

---

### Post by geraldvillorente on 2009-05-25
You mean ftp user's folder?

use this command to view the package directories..
```

sudo dpkg -L proftpd

```

---

### Post by chippanfat on 2009-05-25
> **geraldvillorente said:**
> You mean ftp user's folder?

sorry, i mean the ftp application folder. If I've explained that right?

I was in an irc room trying to find a solution, and they said that the application files are probably scattered about all over the place

---

### Post by geraldvillorente on 2009-05-25
use this command
```

sudo apt-get remove proftpd 

```

---

### Post by chippanfat on 2009-05-25
> **geraldvillorente said:**
> use this command
```

sudo apt-get remove proftpd 

```


I tried that:(
and i tried 
```

sudo apt-get remove --purge proftpd gproftpd

```I think that's the right code, off the top of my head

---

### Post by geraldvillorente on 2009-05-25
then what is the error?

---

### Post by chippanfat on 2009-05-25
It executed the command and it run perfectly. But it did't un-install  the whole application. Because then I re-installed it using 
```

sudo apt-get install

```

but when I've run the application from app menu its just done the same thing when it hasn't opened.

---

### Post by geraldvillorente on 2009-05-25
di you try?
```

sudo apt-get install --fix-missing

```

---

### Post by chippanfat on 2009-05-26
the only thing i can really think of to solve this is go use it through the terminal.
The tutorial that i used had two ways.
1. the beginner way with a gui
2. for more experienced users through the terminal

[http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd](http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd)

what command would i use to start the application? and are there any resources that lists nearly, or all of the command used in ubuntu?

---

