---
title: "How to change terminal inicial path?"
date: 2008-12-18
forum: General Help
---

### Post by XFrame on 2008-12-18
Hi. I was wondering if it is possible to change the location that i enter, every time i open the terminal in ubuntu.

For example, i always get to my home path when i open the terminal, like this: diogo@XFrame-Laptop:~$. 

Is is possible for it to open automatically on the desktop folder, for example?

Thanks in advance, XFrame

---

### Post by taurus on 2008-12-18
Open a terminal.  Then right click the button and pick Profiles > Profile Preferences -> Title and Command.  Put a check mark on Ru_n_ a custom command instead of my shell and enter **cd ~/Desktop** in the Custom co_m_mand:.  And in the When command _e_xits:, pick Hold the terminal open.  Click Close and close down the terminal.  Now, see if it works if you open it again from the menu, Applications -> Accessories -> Terminal.

---

### Post by kanikilu on 2008-12-18
You could also put ```
cd Desktop
``` into your ~/.bashrc file.

---

### Post by XFrame on 2008-12-18
Hi taurus, im very thankful for your quick and good reply.

However, every time i check the box "Run a custom command instead of my shell" and write a command in the text box, even if the command is cd .. , when i close and open again the terminal, it gives me the error message: "An error occured when creating the child process for this shell" (i'm translating, maybe the error message isnt exactly like this in english).

I have to uncheck the box, to be able to open the terminal... it seems that it can't fork or something, because this error appears before he even runs the command, because it doesn't matter what i write in the box... 

Any ideia why this happens?

Thanks in advance, XFrame

---

### Post by kanikilu on 2008-12-18
Just do *gedit ~/.bashrc*. Scroll to the bottom of the file and put the following as the last line: *cd ~/Desktop*. I use this method - it works.

---

### Post by stchman on 2008-12-18
> **XFrame said:**
> Hi. I was wondering if it is possible to change the location that i enter, every time i open the terminal in ubuntu.

For example, i always get to my home path when i open the terminal, like this: diogo@XFrame-Laptop:~$. 

Is is possible for it to open automatically on the desktop folder, for example?

Thanks in advance, XFrame

You need to install a package called nautilus-open-terminal.

```
sudo apt-get install nautilus-open-terminal
```

You can then navigate Nautilus to any location, right mouse click and open a terminal.  This will open a terminal in the folder in which Nautilus is currently in.  This package should be installed by default.

---

### Post by kanikilu on 2008-12-18
> **stchman said:**
> You need to install a package called nautilus-open-terminal.

That's certainly an alternative, but if he adds it to .bashrc as I suggested, it will work regardless of where or how the terminal is launched or even which terminal you use (e.g. rxvt, konsole, etc. versus gnome-terminal).

---

### Post by stchman on 2008-12-18
> **kanikilu said:**
> That's certainly an alternative, but if he adds it to .bashrc as I suggested, it will work regardless of where or how the terminal is launched or even which terminal you use (e.g. rxvt, konsole, etc. versus gnome-terminal).

Yes, but all terminal will open to the Desktop.  If he wishes to open a terminal on the Desktop install nautilus-open-terminal and right mouse click on the Desktop.  A terminal will open with ~/Desktop as it path.  Also if you select Terminal from the Applications menu it will default to your Home ~/ folder.  A great package.

---

### Post by kanikilu on 2008-12-18
> **stchman said:**
> Yes, but all terminal will open to the Desktop.

Yeah...I'm pretty sure that's what he was after:

> I was wondering if it is possible to change the location that i enter, **every time i open the terminal in ubuntu**.

Anyways...it's always good to have options ;)

---

