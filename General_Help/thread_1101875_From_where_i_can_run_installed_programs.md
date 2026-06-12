---
title: "From where i can run installed programs?"
date: 2009-03-20
forum: General Help
---

### Post by smarty7 on 2009-03-20
I recently installed realplayer from a .bin file, now if i want to run realplayer i have to go to the installed location then click realplayer and then it asks me whether to run it in terminal, run and two more options.
Isn't there a way from which i can run realplayer like the diffrent installed  applications that we can run directly from the above menu bar.
I have Ubuntu 7.10 gusty Gibbon

---

### Post by cholericfun on 2009-03-20
Not sure bout the problem but maybe give this a try:
right click Applications -> Edit Menus -> New Menu
and then fill out the form there... adding the whole path (i think) like 
/where/your/realplayer/is

actually, before doing that you may want to check if the program is listed but not ticked to display for some reason...

good luck

---

### Post by Shazaam on 2009-03-20
1. Right-click the panel, choose "Add to panel" and see if it is there in the list (probably not). If it's not there search for it ("find an item to add to the panel" at the top).
2. Go to System>Preferences>Main Menu. The app might be listed there but unchecked. Check it. If it isn't there, on the right hand side click "New Item" and put it where you want. After you do that it is a simple matter to right-click the new menu item and choose "Add to panel".
3. Right-click the desktop, choose "Create Launcher". Just like making a desktop shortcut in Windows.
To accomplish #2 and #3 you will need to know what the command is to launch your app. You can find it by going to the executable you have been clicking to run it. Right-click it, choose "Properties" and look under "Location". As an example, if you put...
```
/usr/lib/firefox-3.0.7/firefox
```
in the command box Firefox would start up when the menu item/launcher is clicked.
4. Add the Medibuntu repository to Synaptic and install RealPlayer 10. it should automatically add a menu item.

Add repos--
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Add Medibuntu repo--
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by lunatico on 2009-03-21
> **smarty7 said:**
> I recently installed realplayer from a .bin file

That usually created a link at Applications -> Sound and Video -> RealPlayer

Not sure I understand your problem...

---

### Post by smarty7 on 2009-03-21
> **Shazaam said:**
> 1. Right-click the panel, choose "Add to panel" and see if it is there in the list (probably not). If it's not there search for it ("find an item to add to the panel" at the top).
2. Go to System>Preferences>Main Menu. The app might be listed there but unchecked. Check it. If it isn't there, on the right hand side click "New Item" and put it where you want. After you do that it is a simple matter to right-click the new menu item and choose "Add to panel".
3. Right-click the desktop, choose "Create Launcher". Just like making a desktop shortcut in Windows.
To accomplish #2 and #3 you will need to know what the command is to launch your app. You can find it by going to the executable you have been clicking to run it. Right-click it, choose "Properties" and look under "Location". As an example, if you put...
```
/usr/lib/firefox-3.0.7/firefox
```
in the command box Firefox would start up when the menu item/launcher is clicked.
4. Add the Medibuntu repository to Synaptic and install RealPlayer 10. it should automatically add a menu item.

Add repos--
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Add Medibuntu repo--
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Thanks shazaam it helped!

---

