---
title: "Change Ubuntu Login Background"
date: 2019-03-30
forum: Desktop Environments
---

### Post by nanasei on 2019-03-30
Hello,
    I am new to Ubuntu but have been using Ubuntu 18.10 for almost 3 months and having a wonderful experience I am glued to my terminal and enjoying the Linux experience, I have been able to customize a whole lot of things the only thing that bugs me is the login screen with its purple background. I really really want to change it and have a beautiful picture there to greet me each time upon startup, I would really appreciate the help if anyone can direct me as to how to resolve these issues, also I want to add that I tried a few things online and lost my login screen totally I was only seeing some background activity on a black screen with OK in green text and some startup activity in white text I had to use my bootable to correct this by deleting my root and having it installed again, that put me through the hustle of reconfiguring things from scratch I don't want to go through that again.

---

### Post by Frogs Hair on 2019-03-30
Moved to its own thread.

---

### Post by deadflowr on 2019-03-31
Typically you change the background by editing the file /etc/alternatives/gdm3.css.
This file is actually a symlink to another file
In Ubuntu 18.04 it's linked to the file /usr/share/gnome-shell/theme/ubuntu.css
In Ubuntu 18.10 it might be symlinked to /usr/share/gnome-shell/theme/Yaru/gnome-shell.css.
Use
```
ls -l /etc/alternatives/gdm3.css
```
to find out what file it really is in case.

To add or change a picture you need to make the section marked as #lockDialogGroup reads as
```
#lockDialogGroup  {
background: url(file:///path/to/file);
background-repeat: no-repeat;
}
```
Replace path/to/file with the path to the file you want to use.

Make sure it reads background and not background-color, as that throws a wrench onto the works.

Edit: I think the easiest and safest way to edit it is to first copy the file into your home folder then make a quick backup copy there, then make the edits and copy the edited file back into the system location
like
```
cp /usr/share/gnome-shell/theme/Yaru/gnome-shell.css ~/Documents
cp ~/Documents/gnome-shell.css ~/Documents/gnome-shell.css.bak
Make edits then
sudp cp ~/Documents/gnome/shell /usr/share/gnome-shell/theme/Yaru/gnome-shell.css
```
That way you only need to run as root once, to copy the file back.
With an original backed up in your documents folder for safekeeping.

---

