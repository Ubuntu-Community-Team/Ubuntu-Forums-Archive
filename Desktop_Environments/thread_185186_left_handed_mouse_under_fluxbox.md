---
title: "left handed mouse under fluxbox"
date: 2006-05-31
forum: Desktop Environments
---

### Post by starpause on 2006-05-31
the title says it all ... under gnome and xfce i was able to use graphical utilities to get my mouse behaving as lefthanded (swap the buttons) but wanted to switch to an even lighter enviornment/window manager.

so here i am, happy with the snappy fluxbox, but can't figure out how to swap my mouse buttons ](*,) 

any advice appreciated ... and if the solution is something i can run from the cli even better, then i could make an icon on the desktop to swap mouse buttons (for when friends get on the machine).

thanks in advance! :KS

---

### Post by conro on 2006-05-31
i used xmodmap to swap my mouse buttons in fluxbox, and i think this strategy should switch them for any WM.. 

from: [http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons#Xmodmap_Button_Remapping](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons#Xmodmap_Button_Remapping)
------
Xmodmap Button Remapping

When using the correct configuration in xorg.conf does not produce the desired results, you may have to manually remap the mouse buttons to the correct function. The Xmodmap program will do this for you. The syntax is
```

#xmodmap -e "pointer = (remapping of mouse buttons)"

```
For instance, if you want to remap button 2 to button 3 and you have a 12 button mouse, simply
```

#xmodmap -e "pointer = 1 3 2 4 5 6 7 8 9 10 11 12"

```
You can test the results of your remapping by running the program xev and pressing the button in question while keeping the cursor inside the black box in the window. It will give you a lot of information you don't need, but it will tell you which button X thinks it is once it's remapped. By default, X does sees all buttons as a 1-to-1 physical mapping with what the mouse driver tells it.

To have X load your mapping each time it's started, simply place it inside the /etc/X11/xinit/.Xmodmap file. For user-based mappings, you can use ~.Xmodmap as such:


File: ~.Xmodmap
```

pointer = 1 3 2 4 5 6 7 8 9 10 11 12

```
-------

---

### Post by xuhainanjing on 2006-12-15
thank u very much, it works
I have searched some time for this issue, your solution is magic, thank you very much:)

---

