---
title: "make .py files open up in Python"
date: 2011-08-30
forum: Desktop Environments
---

### Post by Cranky_Frankie on 2011-08-30
How in Ubuntu can I make clicking on .py files open in Python? I don't see Python listed in the right-click open with dialog. I know it needs a custom script, but I don't know how to do that. I think clicking on a .py file should bring up Python IDE IDLE.

---

### Post by xdominex on 2011-08-30
Well, you don't need to write a script of anything, actually. Find any python file in nautilus, right-click it, and click properties. In the "Properties" window, go to the "Open With" tab and click the "Add" button at the bottom. At the bottom of the "Add Application" window, there is an arrow next to where is says "Use a custom command." Click that arrow and type in either "idle" to run the python 2 version of IDLE, or type in "idle3" to run the python 3 version of IDLE. Make sure that whichever version of IDLE that you want to use is already installed. Anyway, after you type the appropriate command in the box, click the "Add" button. Verify that "idle" or "idle3" is selected in the "Open With" tab of the "Properties" window, and close the window. You should be good to go at this point; try double-clicking a python file to see if it worked.

Hope I've been helpful!

---

### Post by jfed on 2011-08-31
IDLE is different than Python. Do you want it to open in IDLE, or in a terminal, having it run the python script?

Also why is this in the Desktop Environments section?

---

### Post by xdominex on 2011-08-31
> IDLE is different than Python. Do you want it to open in IDLE, or in a terminal, having it run the python script?
I was wondering that myself, but I responded based upon his last sentence about what he "thinks should happen when you click on a .py file."


> Also why is this in the Desktop Environments section? 	
The desktop environment governs the results of clicking on various files. IMHO, this fits into "desktop environments" for that reason.

---

### Post by 3Miro on 2011-08-31
Windows works with .something. Linux (the desktop environment specifically) reads part of the file to determine the type of the file, whether the file ends with .py or .sh or .anything is irrelevant.

If your Python file starts with 
```
#!/usr/bin/python
```
then all that you need to do it enable the executable bit (right-click -> properties -> permissions allow to execute). Then if you click on the file, it will run.

---

