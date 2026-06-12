---
title: "Where does the stuff I install go"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Trelo on 2006-06-13
Not everything I install goes to the menu.  How do I find them and add them to the Applications menu.

Thanks in advance :)

---

### Post by 5-HT on 2006-06-13
Easiest way of doing such would probably be to use 'which' to find the executable, and Alacarte to add a menu item for the executable in question.

1. Find the executable:
```
 which <program_name> 
``` 
e.g., to find the executable for 'vim'
```
$which vim 
/usr/bin/vim
``` 
2. Create a menu entry for the program:

i. Applications -> Accessories -> Alacarte Menu Editor
ii. Click on the the Menu category you would like to place the shortcut in (or create a new Menu: option is under the 'file' tab)
iii. From a Menu category: File -> New Entry
iii. Enter a name for the entry, and under the 'command' field enter the output of 'which'.

Hope that helps.

---

### Post by Trelo on 2006-06-13
Thanks a lot for your help, much appreciated! :)

---

