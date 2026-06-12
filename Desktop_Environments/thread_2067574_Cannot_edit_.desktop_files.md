---
title: "Cannot edit .desktop files"
date: 2012-10-07
forum: Desktop Environments
---

### Post by jbuczek on 2012-10-07
I have a week old clean install of 12.04.1.  Everything seems normal.

I want to edit some .desktop files to add keywords so dash searches turn up what I want.

I found thousands of "desktop configuration files" in /usr/share/applications and more in ~/.local/share/applications.  Mostly for stuff I'll never use.

Only a few have the ".desktop" suffix, mostly ones related to wine.  Even ones I created myself with "Main Menu" do not.

I cannot edit any of them.  If I try to open one it just starts the app.  Tried as su... no go. Tried a few where I am the owner... no go.

Tried                        gksu gedit <filename>
and got a new empty file.

What the ?????  Do I have to be in some kind of "ok2editLaunchers" group or something? 

This keyword thing is pretty flaky.  One suggestion was to use "Main Menu" to edit the launcher properties and put the desired keyword in Comments.  Sometimes that works.  Sometimes it doesn't.

---

### Post by akoskm on 2012-10-07
No, you don't need to be root or <anyOtherUserGroup> I can simply edit those files with nano, vi, etc.
```

cd ~/.local/share/applications
vi <application>.desktop

```
this works for me.

When you are trying to open a file which doesn't exist, the editor will give you an empty file. Do you see your .desktop files if your *~/.local/share/applications* directory?
```

cd ~/.local/share/applications
ll

```

---

### Post by mcduck on 2012-10-07
> **jbuczek said:**
> I have a week old clean install of 12.04.1.  Everything seems normal.

I want to edit some .desktop files to add keywords so dash searches turn up what I want.

I found thousands of "desktop configuration files" in /usr/share/applications and more in ~/.local/share/applications.  Mostly for stuff I'll never use.

Only a few have the ".desktop" suffix, mostly ones related to wine.  Even ones I created myself with "Main Menu" do not.

I cannot edit any of them.  If I try to open one it just starts the app.  Tried as su... no go. Tried a few where I am the owner... no go.

Tried                        gksu gedit <filename>
and got a new empty file.

What the ?????  Do I have to be in some kind of "ok2editLaunchers" group or something? 

This keyword thing is pretty flaky.  One suggestion was to use "Main Menu" to edit the launcher properties and put the desired keyword in Comments.  Sometimes that works.  Sometimes it doesn't.
"gksu gedit filename" will work just fine for .desktop files. It's just that, liek with anything else, you have to do it in the correct directory where the file is located, or provide full path to the file instead of just the filename.

And you can't just doubleclick .desktop files in a graphical filemanager as they are specifically made for file managers and menu applications etc to interpret them as application launchers instead of text files. (filemanagers that don't support the standard would work, though). So that's just the intended behaviour of these files.

---

### Post by mc4man on 2012-10-07
All .desktops files in /usr/share/applications & many in ~/.local/share/applications will be showing the 'display' name, not the actual name of the file.
(the 'display' name is whatever is on the Name= line in the .desktop

Sometimes the actual name is the  appname.desktop, sometimes the displayed name.desktop,  sometimes neither. 

A simple way to open .desktops would be to open your text editor & then just drag & drop the .desktop on to.
(normal editor for .desktops in home folder, root editor for those in /usr/share/applications, /usr/local/share/applications, ect.

Or you can set up a nautilus action(s) to get a context menu option for .desktops

---

### Post by jbuczek on 2012-10-07
I WAS in the proper folder but I didn't think to try appending the invisible .desktop.  That worked.  Drag and drop into gedit worked too, providing it was opened gksu.

Thanx

---

