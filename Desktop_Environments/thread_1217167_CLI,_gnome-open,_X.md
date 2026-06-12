---
title: "CLI, gnome-open, X"
date: 2009-07-19
forum: Desktop Environments
---

### Post by podianu on 2009-07-19
Dear all;
 I would like to optimise my processor use and so I have switched to CLI in Ubuntu Hardy by disabling gdm and then using the startx command. I face a few issues
 (a) I am able to shut down using the halt command as the superuser using sudo halt. Other users are not able to do so after logging out of the GUI menu. How do I enable them to shut down the machine without having to log on as the superuser everytime.
 (b) In a further attempt to start specific programs only I would like to use the gnome-open command to start a program to which I get the response cannot find display as the X server has not been initiated with startx. Is there any way to use the GUI, specific to the program requiring it,  started directly and exclusively from the command line. I hope I am making myself clear. The aim is to open a document like an open org spreadsheet only directly using the CLI with gnome-open and X specifically without startx.
        Thanks
               Podi

---

### Post by Keith Hedger on 2009-07-19
Is this the sort of thing you want?
Press Ctrl-Alt-F2 (to get to a cli if you are in a graphical enviroment), login and type```
sudo  xinit gedit -- :2
```
This will start a new x session and run gedit on display 2

---

### Post by podianu on 2009-07-19
> **Keith Hedger said:**
> Is this the sort of thing you want?
Press Ctrl-Alt-F2 (to get to a cli if you are in a graphical enviroment), login and type```
sudo  xinit gedit -- :2
```
This will start a new x session and run gedit on display 2

Tried that and got
 Server already active for display 0
         Thanks though

---

