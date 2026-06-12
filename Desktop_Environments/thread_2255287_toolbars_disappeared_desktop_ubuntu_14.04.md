---
title: "toolbars disappeared desktop ubuntu 14.04"
date: 2014-12-03
forum: Desktop Environments
---

### Post by Bigmon on 2014-12-03
Hi !
Wonder if anyone can help. Something has happened (or I have done something) and now when I am in the desktop mode I cannot see any menu options at all. All I can see are the desktop files. There are no options to access dash, wireless, shutdown etc. I cannot do anything. They are there, however, in guest mode. I have tried restarting gnome and unity which are suggestions from previous threads but this has not worked. All was working fine until I was in k3b copying a disk when it went pearshaped.

Any ideas ?

---

### Post by veddox on 2014-12-04
Sounds like you somehow managed to screw your Unity... The desktop files are handled by Nautilus, that's why you don't have any problems there. I would probably try to reinstall Unity.

---

### Post by Bigmon on 2014-12-04
I have tried with reinstalling unity from the command line but did not work.

---

### Post by veddox on 2014-12-04
Did you make sure you purged you're old installation before reinstalling?
```
sudo apt-get purge unity
sudo apt-get install unity
```

---

### Post by Bigmon on 2014-12-04
No, I am afraid that did not work either.

---

### Post by ibjsb4 on 2014-12-04
I do not run Unity, but I do know that there are reset commands for both unity and compiz.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+unity&sa=Search&cof=FORID:9)

---

### Post by Bigmon on 2014-12-04
I have tried the suggestions from the above link, but when attempting to run the code where it asks to "gedit compiz etc", the computer tells me it cannot open display.

---

### Post by CantankRus on 2014-12-04
Log in normally.
ctrl+alt+t to open a terminal
**[SIZE=3]or[/SIZE]**
Right click on the desktop and create new folder.
Open the new folder and navigate to **/usr/share/applications **
Copy and paste the "Terminal" file to your desktop.

Open the terminal and run...
```
dconf reset -f /org/compiz/
```

Then logout...
```
kill -9 -1
```
Log in.

---

### Post by ibjsb4 on 2014-12-04
For the reset option, I followed this link.

[https://answers.launchpad.net/ubuntu/+source/unity/+question/211866](https://answers.launchpad.net/ubuntu/+source/unity/+question/211866)

More detail can be found at the 'webupd8.org' link.

---

### Post by Bigmon on 2014-12-05
When I arrive at /usr/share/applications there is no terminal option. Just nerolinux.desktop options. Which I cannot open because it says that it is an untrusted launcher. I cannot open a terminal with ctrl/alt/t, nothing happens. If I open a command line with ctrl/alt/f1 ( not sure if this does the same job) and put code dconf reset -f/org/compiz/ I get cannot autolaunch d-bus without x11 $display. (My apologies for the code but I am trying to write this from a kindle and I cannot seem to copy and paste anything)

---

### Post by CantankRus on 2014-12-05
> **Bigmon said:**
> When I arrive at /usr/share/applications there is no terminal option. Just nerolinux.desktop options. Which I cannot open because it says that it is an untrusted launcher. I cannot open a terminal with ctrl/alt/t, nothing happens. If I open a command line with ctrl/alt/f1 ( not sure if this does the same job) and put code dconf reset -f/org/compiz/ I get cannot autolaunch d-bus without x11 $display. (My apologies for the code but I am trying to write this from a kindle and I cannot seem to copy and paste anything)

Login normally then switch to tty1 with ctrl+alt+F1 (or switch at the greeter if shortcuts not working)
Login to tty1 and run....
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
```

Make the desktop file executable...
```
chmod +x ~/Desktop/gnome-terminal.desktop
```
logout.


Switch to tty7 with ctrl+alt+F7
Click on gnome-terminal on your desktop and run...
```
dconf reset -f /org/compiz/ && setsid unity
```

Sometimes (after waiting about 30 secs) you may need to reload unity again...
```
setsid unity
```

Still no luck, try logging out...
```
kill -9 -1
```
and log back in.

---

### Post by vasa1 on 2014-12-05
> **Bigmon said:**
> When I arrive at /usr/share/applications there is no terminal option. Just nerolinux.desktop options. ...
There seem to be two sets of names for .desktop files: the names seen when you use `ls` in a terminal and the names you see when you navigate to /usr/share/applications in a file manager. So, in a file manager, you'll see **Terminal** or **Terminal Emulator** whereas the terminal will show the same file as **gnome-terminal.desktop**.

And
Text Editor will be gedit.desktop
Document Viewer will be evince.desktop
Network Connections will be nm-connection-editor.desktop
etc

That you see only nerolinux.desktop is scary.

---

### Post by Bigmon on 2014-12-05
Thankyou very much CantankRus, that has solved the problem. I now have my taskbars back !!!

---

### Post by CantankRus on 2014-12-05
> **Bigmon said:**
> Thankyou very much CantankRus, that has solved the problem. I now have my taskbars back !!!
No problem.
You might want to install **gnome-session-flashback**
This will give 2 extra sessions at the greeter.
[LIST]
[*]Gnome Flashback Compiz
[*]Gnome Flashback Metacity
[/LIST]

You can just log in to the **Gnome Flashback Metacity** session should you have problems with the ubuntu/unity session
and run recovery commands from there.

> ...cannot autolaunch d-bus without x11 $display
To run the dconf command from a tty you need to be logged into an Xsession because dconf uses d-bus to write to the dconf database.
So from a tty you would specify the display to use...
```
DISPLAY=":0" dconf reset -f /org/compiz/ && setsid unity
```

---

