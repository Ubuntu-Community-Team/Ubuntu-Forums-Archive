---
title: "All Icons in Nautilus are the same; Icons in taskbar/drawer/menu are missing"
date: 2005-10-14
forum: Desktop Environments
---

### Post by hanzj on 2005-10-14
I just upgraded to breezy.

In Nautilus, folders and files look like the same thing. They all have the icon of an unwritten text document.

[[IMG]http://img436.imageshack.us/img436/4776/screenshot46ii.jpg[/IMG]](http://imageshack.us)







In the taskbar, the "Show Desktop", "Trash," and stuff in the Main Menu and Drawer are Missing. 
[IMG]http://img427.imageshack.us/img427/2878/screenshot112nm.png[/IMG]





I couldn't get a screenshot of my main menu, but the "System" and "Places" have an "X" as their icons.

Could you please tell me how to fix this?




I wonder if it's got anything to do with an error message I got when I ran "sudo apt-get dist-upgrade". 

> 
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by manicka on 2005-10-14
Just go into System-->Preferences-->Themes and change the icon theme by clicking on 'Theme Details' then choosing a different icon theme at the icons tab.

I'd try reinstalling the packages that had errors as well.

---

### Post by hanzj on 2005-10-14
Your solution works!!!

Stay smart... for dummies like me.

---

