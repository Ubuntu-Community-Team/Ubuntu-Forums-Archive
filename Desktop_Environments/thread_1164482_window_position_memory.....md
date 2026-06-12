---
title: "window position memory...."
date: 2009-05-19
forum: Desktop Environments
---

### Post by zero7404 on 2009-05-19
i want ubuntu to remember the window locations i set with specific applications. namely, firefox, thunderbird. every time i start up a new window it keeps snapping to a panel (even after i turned off the snapping window feature in compiz fusion). i also don't like how the windows are sticky to the panels, but since snapping hasn't disabled, i have to hold down the shift key before i move a window to get it exactly where i want it....

any ideas on how to get ubuntu to remember window locations ? would it be an option within gconf-editor ?

---

### Post by hictio on 2009-05-19
You have to use the argument "--geometry" on the launcher.
Take a look at this thread [gnome-terminal windows size on open](http://ubuntuforums.org/showthread.php?t=991037)

---

### Post by zero7404 on 2009-05-19
> **hictio said:**
> You have to use the argument "--geometry" on the launcher.
Take a look at this thread [gnome-terminal windows size on open](http://ubuntuforums.org/showthread.php?t=991037)

thanks....i looked over the thread. but i'm not sure where to start since i'm not familiar with launcher....or the files/config utilities that are used to control window positions....

simply want to size up my windows on the desktop, then make ubuntu remember that until i move it again....

i looked into 'place windows' option which is set to enabled, but the fields are blank.

---

### Post by hictio on 2009-05-19
Launcher is the icon on the Gnome Panel that when clicked starts the given program
What you might want to do is adding the "--geometry" parameter to the command, so that program will always open on the same place on your desktop.
To open a launcher and edit its configuration, do a right click on it, and select propreties.

Take a look at the screenshot, I have enlarged the Launcher window a bit so you can see the whole thing, I have added what is shown as highlighted text, so, all the Terminal program that I open using that launcher will have that size, and use that space on the desktop.
You can add the same for other launchers that start other programs, play a bit with the sizes to get them the way you want them to be.

Maybe there is an option do this using the CompizConfig Settings Manager, but I don't know about it :)

[URL=http://img93.imageshack.us/img93/1381/geometry.png]
[IMG]http://img93.imageshack.us/img93/1381/geometry.th.png[/IMG]
[/URL]

---

### Post by zero7404 on 2009-05-19
thanks hictio, much appreciated....

however it does work with the terminal (which i have on the desktop), but it does not work with firefox, which i have an icon in the top panel. i will move a few icons to the desktop and see if the window sizes and locations take....

update:
it doesn't work with firefox or thunderbird, regardless of whether the icon is in the panel or on the desktop.....not sure y, at least the size of the window is the same each time i start it

---

### Post by uschxc on 2009-09-02
i have this need too.  all my windows open in the top left corner and its just annoying to always have to move the windows.

i wanna say there is a compiz setting at least to make them open in the center always, even that would be better than no memory.  thats kind of a feature that i would expect easily change if not defult by now.

---

