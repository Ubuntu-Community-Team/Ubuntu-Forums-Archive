---
title: "amricas army problems"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by cus1984 on 2008-02-17
hello all, i have installed america's army, from downloading the following file 'armyops250linux.run', 

I didn't use the command line to install as i'm a new linux user and dont really know how or the reason they are used as of yet. Basically i right click the file 'armyops250linux.run' > then 'Properties' > then ticked the box 'Allow executing file as Program'. Double clicked the file and then ran it. 

When Prompted i chose to install the file in the following directory
'/usr/local/games/armyops'

There was another install section which confused me which said 'Do you want to install symbolic links to a directory in your path'. 
I selected 'YES' and the menu displayed 'please enter a path in which to create the symbolic link'.

The default was 'user/local/bin', i selected 'YES' but an error was shown saying 'no write permissions for this path'. However i selected 'OK' and i was taken back to the 'Do you want to install symbolic links to a directory in your path' option..... so this time i selected 'NO'.

The installed continued, but i cant seem to run the game, nor do i know how to run it, when i scroll to the directory where i was installed (/usr/local/games/armyops) there is a 'ArmyOps' icon and i try to run it as an executable but nothing happens. 

Also an alternative way by pressing Alt +f2 when i select Army OPs to run as application nothing happens there either???
 
can any1 help - 
has me not using the symbolic links had an effect?

---

### Post by Imnpsnm on 2009-03-10
I have the same problem, but i think it is because I didn't install it with root permissions, next time I'll install it from console.
I think that could be the problem and yours the same I think.

Did this help you?

---

### Post by JonnyM on 2009-03-10
Try using this... [http://25assist.com](http://25assist.com)

---

### Post by Polygon on 2009-03-10
you should be able to just install it to a home folder and run it from there.

then to play the game cd to the america's army directory in console and run

./armyops250linux.run

if you want to make a menu entry

go to system > prefs > main menu

and add a americas army option somewhere and for the command, make sure its the folder the america's army folder is, so like

/home/<whatever>/armyops/armyops250linux.run

and it should work, no need for external programs.

---

