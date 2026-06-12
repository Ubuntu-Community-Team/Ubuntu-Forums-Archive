---
title: "How to create a shortcut to my new hdd"
date: 2006-01-05
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-05
Its mounted under 
/mnt/hdb/

I really aint able to create a shortcut to have on my desctop and other places...

and another problem. I have a HP Deskjet 720 C printer.
Ive configured it troug printermanager to be the default printer (its in the list)
but still it doesnt print. Do I have to install something?

---

### Post by Stambo00 on 2006-01-05
[QUOTE=syklitengutt] I really aint able to create a shortcut to have on my desctop and other places... [/QUOTE]

You can create shortcuts to folders by right clicking them and then choosing "make link". After that you could cut and paste the link onto the desktop or anywhere else you might like.

---

### Post by syklitengutt on 2006-01-05
that folder is disabled for make link

---

### Post by Ocxic on 2006-01-05
mount your drive in /media (eg: /media/my_Harddrive) and an icon should show up on your desktop automatically.

---

### Post by magnusbb on 2006-01-05
By clicking on "Make link", Nautilus creates a symbolic link in the same directory. /mnt is not owned by you, and therefore this is no good solution.

In the directory you want a link - do a:
**ln -s /mnt/your_new_harddrive name_of_link**

Then you're of course free to copy the link to other places.

---

### Post by RedTDI on 2006-01-14
> I have a HP Deskjet 720 C printer.
Ive configured it through printermanager to be the default printer (its in the list) but still it doesnt print. Do I have to install something?


I had the same problem for a month but the solution was in the /etc/pnm2ppa.conf file.
The following text is from that file.

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command
line
# option e.g., "-v 720".

version                         **(Note:No version number is present)**
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

Just type the model in the version line of text as below.

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
# 
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command
line
# option e.g., "-v 720".

version 720                           **(This is the corrected line)**
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

What is happening is that the system configuration information is getting missed from being placed in the configuration file /etc/pnm2ppa.conf and you have to type it in manually.

All you need to do is run "Gedit" under and then type the version number of your printer "720" on the version line, like above, manually into the file and then save it.
The command would be "gedit /etc/pnm2ppa.conf " in the top line of "Run under other user". It will prompt for your rooot password before the file is displayed.
Your printer will start to work immediately but if you need to change to say gray sacle at the same time, do a reboot to set the printer correctly.

Dennis

---

