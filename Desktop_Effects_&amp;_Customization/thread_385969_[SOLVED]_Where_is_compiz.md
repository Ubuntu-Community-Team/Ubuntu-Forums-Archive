---
title: "[SOLVED] Where is compiz?"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by gettinoriginal on 2007-03-16
I just installed compiz via the synaptic package manager, but all I can find in my files is 3 icons which dont do anything.  Where is Compiz ??

---

### Post by HugoPalma on 2007-03-16
Try running:

compiz-tray-icon

---

### Post by gettinoriginal on 2007-03-16
I would if I had one  LOL,   doing a file search, I have 3 .png files, and they are only the graphical icons (background.png, freedesktop.png, and icon.png), and all they do when I click them is show the icon.  Doing a system search shows all other compiz files are lockled in root.

---

### Post by ZERO_SHIFT on 2007-03-17
You might want to try Beryl.

---

### Post by gettinoriginal on 2007-03-17
already tried to install that, but it just filled my terminal with error messages !!!!

---

### Post by digital_sabotage on 2007-03-18
Do you have Xgl running?  Go to System menu ...Administration ...Login Window ...Security tab ...select Configure X-Server.  You should be running on Xgl.

If you aren't...
In terminal type 'sudo nautilus'
This will allow you to edit as root..

Edit the /etc/X11/gdm/gdm.conf file. Modify it like this:

[servers]
0=Xgl
#0=Standard (comment out this line)

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


Now log out and log back in ...in 'Configure X Server' you should now see Xgl.

You should now be able to run compiz from terminal with 'compiz --replace gconf'

if window decorations are missing, title bar, close, minimize etc in terminal type 'gnome-window-decorator --replace'

worked for me... good luck

---

### Post by gettinoriginal on 2007-03-19
Well, I followed your advice, I am now running in Xgl.   But when I put your commands in the terminal, I get a totally blue screen with no toolbar, and if I run 'gnome-window-decorator --replace', I get an error message saying 'bash: gnome-window-decorator: command not found.

---

### Post by digital_sabotage on 2007-03-26
Sorry I wasn't much help GettinOriginal.  However, I just got rid of compiz due to poor performance and followed these instructions to install beryl... 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

It works great.  I think it actually makes my system faster than a regular gnome session.    
Using more video card instead of processor or something *not sure*

---

