---
title: "XGL installed, but super/winkey has lost all function."
date: 2006-06-29
forum: Desktop Environments
---

### Post by Sanjay on 2006-06-29
Just managed to get XGL/Compiz to install and run. However now my Super/Win key is non functional.
I cannot use the zoom/water effects without reconfiguring keys, and they hotkey assignment puzzles me somewhat. 
Its not only that the Super shortcuts for compiz don't work, but across everything the key has no function, For example none of my amarok global hotkeys that use Super now function. 
I remember reading somewhere on a Kororaa wiki that there was a known issue with XGL & Super?.
But i'm stumped, and i really want my Super Key back! :confused: 

Cheers, Sanjay.

---

### Post by funnyguyfunnyguy on 2006-07-02
I am having the same problem. Anyone have any ideas?

---

### Post by jms830 on 2006-07-08
go to System>Preferences>Keyboard
then click on the Layout Options tab
and change the Alt/Win Key Behavior to "Meta is mapped to the Win-keys"

then to use winkeys for shortcuts with XGL/Compiz they are  <Meta>
you will also probably have to re-set your custom amarok global shortcuts

---

### Post by MystaMax on 2006-08-10
I tried to set "Meta is mapped to the Win-Keys" and then go into keyboard shortcuts and set my 'Lock Screen' shortcut to my windows key+L but no luck. The shortcut sets to **<Mod4>l**, but it doesnt work. I also would like my windows key to show the main panel, but it wont set either. If i click the shortcut textbox to replace the shortcut for "Show the panel menu" and try and set my windows-key, it wont respond to anything. I do not have this problem when i'm not running compiz/xgl.

Any ideas/suggestions?

---

### Post by Epimetheus on 2006-08-28
```
& xmodmap -e "clear Mod4" & xmodmap -e "add Mod4 = Super_L"
```

add this after Exec=/home/toby/.compiz.sh in /usr/share/xsessions/compiz.desktop

It worked for me, hope it helps someone else atleast.

---

### Post by iceman504 on 2006-09-05
i'm having the same problem also but when i click on the keyboard layout options tab all i get is a grayed out box with nothing in it. Anybody know how to fix this?

---

### Post by Rashid584 on 2006-09-22
> **Epimetheus said:**
> ```
& xmodmap -e "clear Mod4" & xmodmap -e "add Mod4 = Super_L"
```

add this after Exec=/home/toby/.compiz.sh in /usr/share/xsessions/compiz.desktop

It worked for me, hope it helps someone else atleast.

Cheers dude. The command worked for me :D :D

I don't really understand what you meant with your second bit though.

I'm almost content typing it each time though... (or using the drop down menu of remembered commands with ALT+F2...)

-Rashid

---

