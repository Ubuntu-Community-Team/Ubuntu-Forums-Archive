---
title: "Use an Icon to launch a script which will in turn launch an application"
date: 2009-05-03
forum: General Help
---

### Post by paydaydaddy on 2009-05-03
Is it possible to set a desktop icon to launch a script which will in turn launch an application? Here are some specifics of what I am trying to do. I have installed puppy linux on an old laptop. I have updated the SeaMonkey browser which includes SeaMonkey Mail. I can start the mail client by navigating to the Seamonkey directory and then running the command ./seamonkey -mail. I can also open the browser and click Window then choose Mail & News. I would like to have an icon on the desktop that would launch the mail client in one click. Any suggestions?

---

### Post by mb_webguy on 2009-05-03
Sure.  Just enter the path to the script in the Command box when you create the launcher.

---

### Post by DeMus on 2009-05-03
> **paydaydaddy said:**
> Is it possible to set a desktop icon to launch a script which will in turn launch an application? Here are some specifics of what I am trying to do. I have installed puppy linux on an old laptop. I have updated the SeaMonkey browser which includes SeaMonkey Mail. I can start the mail client by navigating to the Seamonkey directory and then running the command ./seamonkey -mail. I can also open the browser and click Window then choose Mail & News. I would like to have an icon on the desktop that would launch the mail client in one click. Any suggestions?

Right-click on your desktop and choose Create launcher
In the name field type in E-mail (or whatever name you want to give the launcher)
In the command field you type in: /path to seamonkey/seamonkey -mail
In the comment field you can type something if you like.
Now click Ok and a new launcher will appear on the desktop. Click it and Seamonkey will start.
Replace path to seamonkey by the actual path.

---

### Post by paydaydaddy on 2009-05-04
Because I am trying to do this in Puppy Linux this is a little more complicated. I have an Icon with editable properties. The fields are:
1. clicking the Icon opens (path)
2. Arguments to pass (for executables)

I can set the path easy enough, but I am not sure what else to do. My thoughts are that I could create and save a bash script that I could link to and clinking the icon would launch it. Part of the problem is that this is a very abstract idea in my head and if it can be done I need some kind soul to lead me through it. Do I open a terminal and type in the desired commands and then save it? If so, how do I make it executable? Is this an I D 10 T problem? Please help if you can.

---

### Post by mb_webguy on 2009-05-04
> **paydaydaddy said:**
> Because I am trying to do this in Puppy Linux this is a little more complicated. I have an Icon with editable properties. The fields are:
1. clicking the Icon opens (path)
2. Arguments to pass (for executables)

I can set the path easy enough, but I am not sure what else to do. My thoughts are that I could create and save a bash script that I could link to and clinking the icon would launch it. Part of the problem is that this is a very abstract idea in my head and if it can be done I need some kind soul to lead me through it. Do I open a terminal and type in the desired commands and then save it? If so, how do I make it executable? Is this an I D 10 T problem? Please help if you can.

Put the path to seamonkey in the path line, and "-mail" in the arguments line.

---

### Post by paydaydaddy on 2009-05-04
> **mb_webguy said:**
> Put the path to seamonkey in the path line, and "-mail" in the arguments line.

Thanks. That did it. I had tried every combination that I could think of but somehow did not hit on that one. I guess it was an ID 10 T problem.

---

