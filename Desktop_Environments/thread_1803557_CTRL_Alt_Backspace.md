---
title: "CTRL Alt Backspace"
date: 2011-07-13
forum: Desktop Environments
---

### Post by charliewhizbeez on 2011-07-13
How can I enable it?

I know to go to keyboard shortcuts, but I don't know the command.

---

### Post by akand074 on 2011-07-13
You are using Natty as I can tell. Open up the dash (super or click the button at the top left) and type "keyboard" (or as much as you need to type) and open that application. Go to Layouts tab and click the "Options" button. Find "Key sequence to kill the X server" option and enable it.

EDIT: NVM Just noticed you are using XUbuntu, go through the menu to preferences and find "Keyboard" assuming xubuntu has it.

---

### Post by Toz on 2011-07-13
Have a look at: [https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap]("https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap"). For Xubuntu, you will need to follow the instructions in the "Using the command line" section.

---

### Post by charliewhizbeez on 2011-07-13
where is ~/.xinitrc?
if type it into a terminal it says no file or directory.

---

### Post by Toz on 2011-07-13
If it doesn't exist, you will need to create it. It's a hidden file called **.xinitrc** in your home directory. ```
mousepad ~/.xinitrc
```Make sure you give it executable permissions ```
chmod +x ~/.xinitrc
``` when you are finished creating it.

---

### Post by charliewhizbeez on 2011-07-14
Is there anything else I need to do after making it executable?

---

### Post by akand074 on 2011-07-14
Is there no keyboard layout settings in Xubuntu? :S There should be, or you should be able to just install the settings manager. Just simpler.

---

