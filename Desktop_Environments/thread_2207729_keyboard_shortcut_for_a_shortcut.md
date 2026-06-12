---
title: "keyboard shortcut for a shortcut"
date: 2014-02-24
forum: Desktop Environments
---

### Post by roiikkata on 2014-02-24
hey,


   i have a program/app that is run from itself. its one of those ones that you click on and it just runs. im wondering how i can create a keyboard shortcut to it so i can just press the combination and it opens (a hotkey combination like ctrl+o )

i can create a .desktop shortcut for it too.

just looking for what to put into the shortcut "command" in the custom shortcuts of the keyboard settings

i tried googling it but im pretty sure that it confuses the search engine to search for "keyboard shortcut for a shortcut ubuntu" and such ..
i tried just typing in the path of it with the name of the program at the end into the command part of the custom hotkey window but when i set it it does nothing, but, if i put the path into the terminal the same way surrounded by  '  and  '  then it opens ..


a little confused here ..

its for ubuntu 13.10

thanks ..

---

### Post by tfrue on 2014-02-25
Search for the "Keyboard" application in the Unity Search bar, and you select custom Keyboard Shortcuts from the menu and define your own Name for the shortcut and the command to execute the program. 

Good luck,
Chris

---

### Post by roiikkata on 2014-02-27
true
but how do i add a hotkey to launch a .desktop file?
like, what code do you put in to it?

---

### Post by roiikkata on 2014-04-08
into the "command" part of it, i mean .. ive searched everywhere for it. . . **sigh**

---

### Post by mc4man on 2014-04-08
> **roiikkata said:**
> true
but how do i add a hotkey to launch a .desktop file?
like, what code do you put in to it?
You have 2 threads about this though this one *may* be different if you are specifically asking how to launch a **.desktop** via a custom shortcut binding
(your other thread seems to be about just setting a custom shortcut for a command (binary

So to answer specifically, using vlc.desktop as an example - 
The command for the custom shortcut would be - 
```
gtk-launch vlc
```
This launches via vlc.desktop where just "vlc" launches the binary (/usr/bin/vlc

---

### Post by roiikkata on 2014-04-08
oh, sorry, no, my fault.
i was asking about a .desktop file that was a "shortcut" for a program that runs out of a folder, not installed through the software center ..
i put the folder in my "documents" folder i guess, and put a shortcut to it on the desktop, which i would like to run from a hotkey
what command do i put into the shortcut editor under custom shortcuts .. ? am i getting it right i just have to restart my laptop .. ?

---

### Post by roiikkata on 2014-04-08
to be more clear it was not vlc it was called yoono (i think), a facebook/twitter, etc. client ..

---

### Post by mc4man on 2014-04-08
I believe in this case you would need to use gtk-launch, but it probably only works on .desktops that are in an applications folder.
(I could test out but not till later...
You could try opening the desktop launcher in a text editor & using what's on the Exec= line as a command for binding, if it doesn't work then use gtk-launch as described.

To see -** copy** your desktop launcher to ~/.local/share/applications

Get the exact name of the .desktop file (if not sure after copying open a terminal & run this, find the name..
```
 ls .local/share/applications
```
Edit: note that the display name of a .desktop is not always the actual name of the .desktop file

Then set your custom binding command to that name **without the .desktop part** (so for whatever.desktop use whatever, ie. 
gtk-launch whatever
Then log out/in & test

---

### Post by roiikkata on 2014-04-09
ok i'll try it. this could take a while. the program im trying to launch now isnt working now for some reason ..

---

### Post by roiikkata on 2014-04-09
ok so i got another desktop file
it works from the terminal but not from the command of the shortcut interface
it says this under file type of the file:

desktop configuration file (application/x-desktop)

i tried it first after i logged back in, then after i restarted .. no launch

double checked and triple checked from the terminal and it launches every time

---

### Post by roiikkata on 2014-04-10
is there a setting i need to enable somewhere to get it to launch from shortcuts like it does from the terminal .. ?
im not finding anything anywhere
perhaps a direct search for the issue of that ..

---

### Post by roiikkata on 2014-04-10
got it.
the directory was /usr/share/applications to copy it to and to do so i had to open it as root (using my password)
log out, log in
now it works fine
also, some shortcuts are already taken (there are lots of them)
i set it to ctrl+` instead of not using ctrl key

---

