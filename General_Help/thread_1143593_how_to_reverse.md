---
title: "how to reverse"
date: 2009-04-30
forum: General Help
---

### Post by aquanim on 2009-04-30
How can i reverse the changes i have made follwoing the instructions from this link 

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Mesa_drivers)

or should I make a totally new installation?
which would you recommend??

10x for the help

i have used the back up copy of my xorg.conf but no success

---

### Post by blazemore on 2009-04-30
The easiest thing would be to install the drivers using the standard Ubuntu tool. It should overwrite any other drives you have installed.

---

### Post by aquanim on 2009-04-30
can you give me a hint how to do that because right now i gotta do everything from the console 
my ubuntu is totally busted right now i cannot log in at all my screen is all scrambled :)

---

### Post by blazemore on 2009-05-01
Try
```
sudo dpkg --reconfigure -phigh xserver-xorg
```

---

### Post by aquanim on 2009-05-01
already did more than 10 time :) with all types of variations of the command but no avail the only thing i can configure is the keyboard and the mouse 

i have gone through the forums and there are people with similar problems but with no solution regarding the sudo dpkg --reconfigure -phigh xserver-xorg command

---

### Post by blazemore on 2009-05-01
Personally I would back up all your files to an external hard disk, then reinstall Jaunty.

---

### Post by aquanim on 2009-05-01
hm....... :) strange i am downloading it at the moment i had enough of this and decided to do the same :D:D:D

---

### Post by blazemore on 2009-05-01
Make sure you format as ext4 to get the uber-fast boot speeds!

---

### Post by aquanim on 2009-05-01
DONE

complete and total re install :) now configure time and next time be more careful :)

---

