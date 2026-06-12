---
title: "Naming custom open commands"
date: 2009-05-08
forum: General Help
---

### Post by rasmus_ on 2009-05-08
If I want to open a file-type with a custom command I use:

Right-click file -> Properties -> Open With -> Add -> Use custom command

This works great, but if I use a command such as

env "/home/rasmus/.wine2" wine "C:\Program Files\App\App.exe"

it will be named 'env'. It works but the name isn't very descriptive. Especially if I got 10 different applications named 'env'. Which one is which? :confused:

**My question is:**

How can I give a custom application command a custom name such as "My application"?

Btw, I'm using Ubuntu Intrepid.

---

### Post by spiderbatdad on 2009-05-08
```
man bash
```

---

### Post by geirha on 2009-05-08
Look in ~/.config/share/applications/ . The entry you created is likely called env-usercreated.desktop, but running the following should identify it ```
grep 'Name=env' ~/.config/share/applications/*
``` 

Edit it in a text-editor and change the line "Name=env" to "Name=My Application" or whatever you prefer.

---

### Post by rasmus_ on 2009-05-10
Thanks but my "~/.config/share" doesn’t contain a folder named "applications". I did however find a similar folder "/usr/share/applications" but none of them matched the name env. I even tried
```
grep -r "Name=env" *
```
in both my home directory and in "/usr/share" without any luck.

---

### Post by spiderbatdad on 2009-05-10
can you not use a custom command like ```
bash -c '/home/rasmus/.wine2 && wine C:\Program Files\App\App.exe'
```

---

### Post by rasmus_ on 2009-05-10
spiderbatdad:

I think you misunderstood me; the problem is not executing the command. That already works. The problem is that GNOME displays the command using only its first word (when right-clicking a file and selecting the application to open it). Using my command it will be called "env" and using your command it will be called "bash". I want a more descriptive name such as "My Application".

---

### Post by spiderbatdad on 2009-05-10
I see. These are know application types used for opening files. I dont see how you can change the names of the systems applications. For example if file open with Text Editor I can't change that to My Text Editor...since I havent written a text editor app and somehow hard coded it into gdm.
If you run ps -ef you will find your processes properly identified.

EDIT: I take that back...I have some .sh scripts in a directory called /home/user/bin. bin is in my executable path. I can set custom open commands the way you desrcibe simply by entering the script name. So perhaps the issue is creating $PATH to your scripts in .bashrc?
screenshot as example:

For example I have this added to .bashrc
```
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin 
```I'm not sure this is necessary...I can't seem to find a file in the system where I believe configuration exists so that if bin is created in the user's home directory, it is added to $PATH.

---

### Post by geirha on 2009-05-10
Sorry. ~/.local/share/applications, not ~/.config/share/applications

---

### Post by mc4man on 2009-05-10
All r.click -> open with -> use a custom command become a userapp.desktop in ~/.local/share/applications and get an appropriate entry in ~/.local/share/applications/mimeapps.list

The naming format is userapp-name-xxxxxx.desktop where xxxxxx is some numbers and letters and name is the first word of the command

To give a display name and an icon if desired there are 3 ways

From the command line open the .desktop in a text editor - requires you know the exact name of the .desktop which is not displayed (can been found on the line in mimeapps.list

If you have a nautilus action "open in text editor" you can right click on and open.

The simplest is navigate to ~/.local/share/applications and r. click -> properties on the blue icon with name of command

 The display name can be changed, the actual name can never  be (what's used in mimeapps.


Ex. in screen

Edit: initially the display name for this .desktop would of been mplayer with a blue diamond icon

---

### Post by rasmus_ on 2009-05-11
It worked perfectly! :) Thanks guys. I went with the solution provided by geirha and mc4man. spiderbatdad's solution is second best; it would have given me a way to distinguish the applications but it would give me less freedom in naming them.

---

